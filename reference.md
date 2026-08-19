# Reference
<details><summary><code>client.<a href="src/loonfs_sdk/client.py">capabilities</a>() -> CapabilityDocument</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns a summary of supported features and limits.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.capabilities()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## system
<details><summary><code>client.system.<a href="src/loonfs_sdk/system/client.py">health</a>() -> str</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns `ok` when the server is running and can accept requests.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.system.health()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.system.<a href="src/loonfs_sdk/system/client.py">get_metrics</a>() -> str</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns this process's metrics in Prometheus text exposition format 0.0.4. Unlike `/health` and `/readiness`, the route requires the deployment's bearer token.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.system.get_metrics()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.system.<a href="src/loonfs_sdk/system/client.py">readiness</a>() -> str</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns `ready` while the server admits new work. Once shutdown begins and publisher admission closes, answers 503 `shutting_down` so load balancers can drain the instance. `/health` stays the liveness probe: it only reports that the process is up.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.system.readiness()

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## admin
<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">list_checkpoints</a>(...) -> ListCheckpointsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists one page of active checkpoints in checkpoint-id order. Expired checkpoints remain visible until collection releases them. Released checkpoints are omitted. The cursor resumes a live listing and does not create a snapshot.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.list_checkpoints(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque checkpoint-list page cursor
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">create_checkpoint</a>(...) -> CreateCheckpointResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a named, user-owned checkpoint record pinning the current namespace view. Every call mints a new record under a new id; the name is a label, not a key. The record is a garbage-collection root until it is released, so routine maintenance should flush the WAL instead. This is a maintenance/admin operation, not a file mutation.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.create_checkpoint(
    namespace_id="namespace_id",
    name="name",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**name:** `str` 

Label recorded on the checkpoint record. A label, not a key: several
records may carry the same name over different bases.
    
</dd>
</dl>

<dl>
<dd>

**ttl_ms:** `typing.Optional[int]` 

Optional lifetime; the server computes the record's expiry from its
own clock. Absent means the pin holds until explicitly released.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">release_checkpoint</a>(...) -> ReleaseCheckpointResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Releases a user-owned checkpoint pin by id. Idempotent: releasing an already-released or reaped record succeeds. The record is reaped by a later garbage-collection pass; its pinned data becomes collectable only on the pass after that.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.release_checkpoint(
    namespace_id="namespace_id",
    checkpoint_id="checkpoint_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**checkpoint_id:** `str` — Checkpoint id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">get_namespace_diagnostics</a>(...) -> NamespaceDiagnostics</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns namespace state together with the current manifest and visible WAL tail.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.get_namespace_diagnostics(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">get_grep_index_status</a>(...) -> GrepIndexStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns whether the namespace's grep index is `disabled`, `backfilling`, or `active`, including build progress when available. A namespace that has never enabled the index is `disabled`. This operation requires a deployment that maintains grep indexes and does not change the index.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.get_grep_index_status(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">disable_grep_index</a>(...) -> GrepIndexStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Disables the namespace's grep root and clears its segment references with one durable compare-and-swap; index maintenance stops on its own once a step reads the disabled root. Explicit grep garbage collection later reclaims the segments. Idempotent. Requires this deployment to maintain the grep index.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.disable_grep_index(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">enable_grep_index</a>(...) -> GrepIndexStatusResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Enables the namespace's grep root and asks this deployment's maintenance runner for the backfill's first step. The response reports the lifecycle and bookkeeping read after the transition: a fresh enable is `backfilling` with the sequence its checkpoint captured, while an already-enabled namespace answers with its current status. Idempotent. Requires this deployment to maintain the grep index.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.enable_grep_index(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">gc_grep_index</a>(...) -> GrepGcResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Runs one explicit garbage-collection pass over only this namespace's grep-owned extension keyspace. A tombstoned or absent namespace has aged extension state reaped; no grep garbage collection runs implicitly. `max_objects` bounds the reads the pass spends and returns a `next_cursor` when keys remain; resuming re-reads liveness and the grep root, so a cursor only skips enumeration. Requires this deployment to maintain the grep index.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.gc_grep_index(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` 

Opaque resume token returned as `next_cursor` by an earlier pass
against the same namespace.
    
</dd>
</dl>

<dl>
<dd>

**max_objects:** `typing.Optional[int]` 

Reads this pass may spend before returning with a `next_cursor`.
Omit to take the same per-pass default the runtime's own collection
takes.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">maintenance_step</a>(...) -> MaintenanceStepResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Runs one bounded maintenance step. The body selects the actions by naming them: `metadata` folds the WAL tail once it reaches the threshold and merges one bounded reorganization unit, `advance_retention: true` advances the retention floor, and `gc` runs one bounded garbage-collection pass. Selected actions run in that order, each reports separately, and an absent report means the body did not select that action. A body that selects nothing is rejected. Nothing surrenders replay history or sweeps objects unless the body asked for it. A deleted namespace accepts a step that selects `gc` alone, which is how its reclaimable state is collected; any other selection is refused. Step-driven GC defaults to 1024 candidates and returns its cursor for a later step rather than looping internally. Losing the root race is an outcome, not an error.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.maintenance_step(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**advance_retention:** `typing.Optional[bool]` 

Advance the retention floor to the flushed manifest head. Nothing
surrenders replay history unless this is true.
    
</dd>
</dl>

<dl>
<dd>

**gc:** `typing.Optional[GcRequest]` 

Run one bounded mark-and-sweep garbage-collection pass. Nothing
sweeps unless this is present.
    
</dd>
</dl>

<dl>
<dd>

**metadata:** `typing.Optional[MetadataMaintenanceRequest]` 

Flush the visible WAL tail into metadata tables, then run one bounded
reorganization step.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.admin.<a href="src/loonfs_sdk/admin/client.py">probe_store</a>(...) -> StoreProbeResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Proves the configured object store honours the create-if-absent, compare-and-swap, visibility, listing, and ranged-read semantics LoonFS depends on, and reports what it found check by check. Nothing runs this implicitly: a probe writes and deletes objects, all of them under a scratch prefix that is not a durable object family, and its last check deletes them and proves the prefix empty. A store that fails a check answers 200 with that check reported `failed` — the probe ran, and the answer is that the store is wrong. Optional capabilities a store declares it lacks answer `unsupported`, which is an answer rather than a fault. This route does not decide whether the deployment may serve presigned direct uploads: that trust comes from the endpoint allowlist, because a probe exercises the server's own request path and never a presigned capability handed to a client.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.probe_store(
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `StoreProbeRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## namespaces
<details><summary><code>client.namespaces.<a href="src/loonfs_sdk/namespaces/client.py">create_namespace</a>(...) -> Namespace</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new empty namespace.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.create_namespace(
    namespace_id="demo",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `NamespaceId` — Durable namespace id to create.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.namespaces.<a href="src/loonfs_sdk/namespaces/client.py">get_namespace</a>(...) -> Namespace</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the current head and retention state for a namespace.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.get_namespace(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.namespaces.<a href="src/loonfs_sdk/namespaces/client.py">delete_namespace</a>(...) -> DeleteNamespaceResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Marks a namespace as deleted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.delete_namespace(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**expected_head_seq:** `typing.Optional[ChangeSeq]` — Delete only if the namespace head is still at this sequence
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.namespaces.<a href="src/loonfs_sdk/namespaces/client.py">fork_namespace</a>(...) -> Namespace</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a new namespace as a fork from the source namespace's current durable view.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.fork_namespace(
    namespace_id="namespace_id",
    new_namespace_id="demo",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Source namespace id
    
</dd>
</dl>

<dl>
<dd>

**new_namespace_id:** `NamespaceId` — Durable namespace id for the fork target.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## filesystem
<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">list_changes</a>(...) -> ChangesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns committed changes from the write-ahead log. Callers can use this feed to keep another projection synchronized with WAL history.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.list_changes(
    namespace_id="namespace_id",
    after_seq=1000000,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**after_seq:** `ChangeSeq` — Return committed changes after this sequence
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">apply_commit</a>(...) -> CommitResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Applies one commit: an ordered, non-empty list of path operations that commit together as one logical commit, under one commit id that makes retries idempotent. A single-operation call is the one-element case. The first operation that fails aborts the whole request, and a request carrying more than one operation names that operation's position in `details.operation_index`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS, ActorRef, FilesystemOperation_CreateDirectory

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.apply_commit(
    namespace_id="namespace_id",
    actor=ActorRef(
        id="usr_8f3c",
        kind="user",
    ),
    commit_id="c_f3a9c2d4b6e8417a90c5d2f8e1b7a6c0",
    operations=[
        FilesystemOperation_CreateDirectory(
            path="/docs/report.txt",
        )
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**actor:** `ActorRef` — Actor responsible for the commit, as supplied by the application.
    
</dd>
</dl>

<dl>
<dd>

**commit_id:** `CommitId` — Caller-supplied idempotency key for the whole request.
    
</dd>
</dl>

<dl>
<dd>

**operations:** `typing.List[FilesystemOperation]` 

Ordered operations to apply. Must be non-empty; they commit all
together or not at all.
    
</dd>
</dl>

<dl>
<dd>

**content_tokens:** `typing.Optional[typing.List[ContentToken]]` 

Proofs for any new external content refs introduced by this request.
One proof covers every operation that names its content ref.
    
</dd>
</dl>

<dl>
<dd>

**message:** `typing.Optional[str]` 

Caller annotation recorded on the commit and reported by the change
feed. Part of the commit's identity: reusing `commit_id` with a
different message is a `commit_id_reuse_conflict`, exactly as it is
for an explicit commit.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">get_file_bytes</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns file bytes for the current revision at a path, or for a specific retained revision when `revision_no` is provided.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.get_file_bytes(
    namespace_id="namespace_id",
    path="path",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**path:** `str` — Absolute file path
    
</dd>
</dl>

<dl>
<dd>

**revision_no:** `typing.Optional[RevisionNo]` — Optional prior revision number
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">begin_download</a>(...) -> BeginDownloadResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Authorizes one direct read of a file's content object and returns a short-lived presigned GET capability, the resolved revision, and the content reference the client checks the arriving bytes against. `Range` is outside the signature, so one grant serves ranged, resumed, and parallel reads. Deployments that cannot presign answer 501 `not_supported`; the proxied `GET /filesystem/content` route stays available and is capped by `download.max_content_bytes`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.begin_download(
    namespace_id="namespace_id",
    path="/docs/report.txt",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**path:** `AbsolutePath` — Absolute path of the file to read.
    
</dd>
</dl>

<dl>
<dd>

**revision_no:** `typing.Optional[RevisionNo]` — Revision to read, or `None` for the path's current revision.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">list_path_entries</a>(...) -> ListPathEntriesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists a directory at the current namespace head.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.list_path_entries(
    namespace_id="namespace_id",
    path="path",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**path:** `str` — Absolute filesystem path
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque directory-list page cursor
    
</dd>
</dl>

<dl>
<dd>

**include_attributes:** `typing.Optional[bool]` — Project each entry's attribute map and revision (`true` or `false`). Defaults to `false`: a page holds many entries and each map may be 64 KiB, so a listing does not carry them unless asked.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">list_file_revisions</a>(...) -> ListFileRevisionsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Resolves the current path to a file inode and returns revisions for that file. If the file could be renamed, use the inode revision API for stable identity.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.list_file_revisions(
    namespace_id="namespace_id",
    path="path",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**path:** `str` — Absolute file path
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque file-revisions page cursor
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">stat_path</a>(...) -> AuthoritativePathEntry</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the current metadata for a path, including inode identity, kind, display name, file content metadata, and the inode's attributes.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.stat_path(
    namespace_id="namespace_id",
    path="path",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**path:** `str` — Absolute filesystem path
    
</dd>
</dl>

<dl>
<dd>

**include_attributes:** `typing.Optional[bool]` — Project the inode's attribute map and revision (`true` or `false`). Defaults to `true`: a stat answers for one path and a map is capped at 64 KiB.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.filesystem.<a href="src/loonfs_sdk/filesystem/client.py">list_trash</a>(...) -> ListTrashResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the namespace's recoverable deletions, oldest deletion first. Entries never age out at the retention floor; each carries the inode id and deletion sequence undelete needs, plus the deleted name when the delete recorded one.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.filesystem.list_trash(
    namespace_id="namespace_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque trash page cursor
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## inodes
<details><summary><code>client.inodes.<a href="src/loonfs_sdk/inodes/client.py">stat_inode</a>(...) -> AuthoritativePathEntry</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the current path entry for a visible inode. Unknown or hidden inodes answer `inode_not_found`.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.stat_inode(
    namespace_id="namespace_id",
    inode_id="ino_123",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**inode_id:** `str` — Inode ID
    
</dd>
</dl>

<dl>
<dd>

**include_attributes:** `typing.Optional[bool]` — Project the inode's attribute map and revision (`true` or `false`). Defaults to `true`: a stat answers for one path and a map is capped at 64 KiB.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inodes.<a href="src/loonfs_sdk/inodes/client.py">list_file_revisions_by_inode</a>(...) -> ListFileRevisionsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns retained revisions for a file inode without requiring a current path.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.list_file_revisions_by_inode(
    namespace_id="namespace_id",
    inode_id="ino_123",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**inode_id:** `str` — File inode ID
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque file-revisions page cursor
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inodes.<a href="src/loonfs_sdk/inodes/client.py">get_file_revision_bytes_by_inode</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Reads and verifies one retained file revision by inode ID and revision number.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.get_file_revision_bytes_by_inode(
    namespace_id="namespace_id",
    inode_id="inode_id",
    revision_no=1000000,
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**inode_id:** `str` — File inode ID
    
</dd>
</dl>

<dl>
<dd>

**revision_no:** `RevisionNo` — Revision number
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.inodes.<a href="src/loonfs_sdk/inodes/client.py">begin_download_by_inode</a>(...) -> BeginDownloadByInodeResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Authorizes a direct read of one retained inode revision. The request body is `{}` and the response does not include a path.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.begin_download_by_inode(
    namespace_id="namespace_id",
    inode_id="ino_123",
    revision_no=1000000,
    request={
        "key": "value"
    },
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**inode_id:** `str` — File inode ID
    
</dd>
</dl>

<dl>
<dd>

**revision_no:** `RevisionNo` — Revision number
    
</dd>
</dl>

<dl>
<dd>

**request:** `BeginDownloadByInodeRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## query
<details><summary><code>client.query.<a href="src/loonfs_sdk/query/client.py">grep</a>(...) -> GrepResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Searches file content with a regular expression, accelerated by the namespace's grep index. Matches are verified against the real pattern and returned in ascending `(inode_id, byte_offset)` order; revisions committed after the index watermark are scanned exhaustively unless `allow_stale` skips them. Requires this deployment to serve grep and the namespace to carry a materialized active grep root.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.query.grep(
    namespace_id="namespace_id",
    pattern="pattern",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**pattern:** `str` — Pattern in the Rust `regex` crate's dialect. Its UTF-8 encoding must be at most 1024 bytes.
    
</dd>
</dl>

<dl>
<dd>

**case_insensitive:** `typing.Optional[bool]` — Match case-insensitively (`true` or `false`). Defaults to `false`.
    
</dd>
</dl>

<dl>
<dd>

**path_prefix:** `typing.Optional[str]` — Complete absolute path used to restrict matches.
    
</dd>
</dl>

<dl>
<dd>

**allow_scan:** `typing.Optional[bool]` — Permit a capped exhaustive scan when the pattern has no required grams (`true` or `false`). Defaults to `false`.
    
</dd>
</dl>

<dl>
<dd>

**allow_stale:** `typing.Optional[bool]` — Return indexed-only results when the unindexed tail exceeds the scan budget (`true` or `false`). Defaults to `false`.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum matches per page
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque grep page cursor
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## uploads
<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">begin_upload</a>(...) -> BeginUploadResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Starts an upload session for content that may later be attached to a file. Service-proxied uploads send bytes through the server; direct-put uploads return object-store presigned credentials.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS, BeginUploadRequest_ServiceProxied

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.begin_upload(
    namespace_id="namespace_id",
    request=BeginUploadRequest_ServiceProxied(),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**request:** `BeginUploadRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">get_upload_status</a>(...) -> UploadSessionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns an upload session. A completed session includes a new content token so the client can retry the commit without uploading the content again.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.get_upload_status(
    namespace_id="namespace_id",
    upload_id="upload_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**upload_id:** `str` — Upload session id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">abort_upload</a>(...) -> UploadSessionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Ends an upload session without selecting content and deletes the object it was writing. Repeating it succeeds; a session that already completed cannot be aborted.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.abort_upload(
    namespace_id="namespace_id",
    upload_id="upload_id",
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**upload_id:** `str` — Upload session id
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">complete_upload</a>(...) -> UploadSessionResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Completes an upload. The request mode must match the mode used to start the session. Direct-multipart requests also include the content claim and completed parts.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS, CompleteUploadRequest_ServiceProxied

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.complete_upload(
    namespace_id="namespace_id",
    upload_id="upload_id",
    request=CompleteUploadRequest_ServiceProxied(),
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**upload_id:** `str` — Upload session id
    
</dd>
</dl>

<dl>
<dd>

**request:** `CompleteUploadRequest` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">upload_content</a>(...) -> UploadContentResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Uploads bytes into a service-proxied upload session and returns the content reference for the stored object.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
client.uploads.upload_content(...)
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**upload_id:** `str` — Upload session id
    
</dd>
</dl>

<dl>
<dd>

**request:** `typing.Union[bytes, typing.Iterator[bytes], typing.AsyncIterator[bytes]]` 
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.uploads.<a href="src/loonfs_sdk/uploads/client.py">sign_upload_parts</a>(...) -> SignUploadPartsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns one short-lived, checksum-bound upload capability per requested part of an open direct_multipart session. Asking again for a part is how a client retries it.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```python
from loonfs_sdk import LoonFS, UploadPartChecksumClaim, Checksum

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.sign_upload_parts(
    namespace_id="namespace_id",
    upload_id="upload_id",
    parts=[
        UploadPartChecksumClaim(
            checksum=Checksum(
                algorithm="sha256",
                value="value",
            ),
            part_number=1,
        )
    ],
)

```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**namespace_id:** `str` — Namespace id
    
</dd>
</dl>

<dl>
<dd>

**upload_id:** `str` — Upload session id
    
</dd>
</dl>

<dl>
<dd>

**parts:** `typing.List[UploadPartChecksumClaim]` 

Parts to authorize, each with the checksum the provider will enforce
on it. Asking again for a part already uploaded is how a client
retries one: a repeated part is last-write-wins at the provider.
    
</dd>
</dl>

<dl>
<dd>

**request_options:** `typing.Optional[RequestOptions]` — Request-specific configuration.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

