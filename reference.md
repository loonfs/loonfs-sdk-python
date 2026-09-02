# Reference
## Capabilities
<details><summary><code>client.capabilities.<a href="src/loonfs/capabilities/client.py">retrieve</a>() -> CapabilityDocument</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.capabilities.retrieve()

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

## namespaces
<details><summary><code>client.namespaces.<a href="src/loonfs/namespaces/client.py">create</a>(...) -> Namespace</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.create(
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

<details><summary><code>client.namespaces.<a href="src/loonfs/namespaces/client.py">retrieve</a>(...) -> Namespace</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.retrieve(
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

<details><summary><code>client.namespaces.<a href="src/loonfs/namespaces/client.py">delete</a>(...) -> DeleteNamespaceResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.delete(
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

<details><summary><code>client.namespaces.<a href="src/loonfs/namespaces/client.py">fork</a>(...) -> Namespace</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.namespaces.fork(
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

## Changes
<details><summary><code>client.changes.<a href="src/loonfs/changes/client.py">list</a>(...) -> ListChangesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns committed changes after a sequence. A snapshot limits the feed to its captured sequence.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.changes.list(
    namespace_id="namespace_id",
    after_seq=1000000,
    snapshot_id="chk_00000000000000000000000000000002",
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

**snapshot_id:** `typing.Optional[CheckpointId]` — End the feed at this snapshot's captured sequence
    
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

## Commits
<details><summary><code>client.commits.<a href="src/loonfs/commits/client.py">create</a>(...) -> CommitResponse</code></summary>
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
from loonfs.server import LoonFS, ActorRef, FilesystemOperation_CreateDirectory

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.commits.create(
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

## Files
<details><summary><code>client.files.<a href="src/loonfs/files/client.py">content</a>(...) -> typing.Iterator[bytes]</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns the current file bytes, a retained revision, or the revision captured by a live snapshot.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.content(
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

**revision_no:** `typing.Optional[RevisionNo]` — Optional prior revision number; cannot be combined with snapshot_id
    
</dd>
</dl>

<dl>
<dd>

**snapshot_id:** `typing.Optional[CheckpointId]` — Use the file revision captured by this snapshot
    
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

<details><summary><code>client.files.<a href="src/loonfs/files/client.py">create_download</a>(...) -> BeginDownloadResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.create_download(
    namespace_id="namespace_id",
    snapshot_id="chk_00000000000000000000000000000002",
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

**snapshot_id:** `typing.Optional[CheckpointId]` — Use the file revision captured by this snapshot
    
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

<details><summary><code>client.files.<a href="src/loonfs/files/client.py">list</a>(...) -> ListPathEntriesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists a directory from the current state or a live snapshot.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.list(
    namespace_id="namespace_id",
    path="path",
    snapshot_id="chk_00000000000000000000000000000002",
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

**snapshot_id:** `typing.Optional[CheckpointId]` — Use the directory state captured by this snapshot
    
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

<details><summary><code>client.files.<a href="src/loonfs/files/client.py">retrieve</a>(...) -> PathEntry</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Returns path metadata from the current state or a live snapshot.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.retrieve(
    namespace_id="namespace_id",
    path="path",
    snapshot_id="chk_00000000000000000000000000000002",
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

**snapshot_id:** `typing.Optional[CheckpointId]` — Use the path state captured by this snapshot
    
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

<details><summary><code>client.files.<a href="src/loonfs/files/client.py">list_revisions</a>(...) -> ListFileRevisionsResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.list_revisions(
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

<details><summary><code>client.files.<a href="src/loonfs/files/client.py">grep</a>(...) -> GrepResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.files.grep(
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

## Trash
<details><summary><code>client.trash.<a href="src/loonfs/trash/client.py">list</a>(...) -> ListTrashResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.trash.list(
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
<details><summary><code>client.inodes.<a href="src/loonfs/inodes/client.py">retrieve</a>(...) -> PathEntry</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.retrieve(
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

<details><summary><code>client.inodes.<a href="src/loonfs/inodes/client.py">list_children</a>(...) -> ListInodeChildrenResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists one page of a directory's children addressed by parent inode ID, in canonical name-key order. Inode addressing keeps a listing and its resumption on the same directory across concurrent renames or moves of the parent.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.list_children(
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

**inode_id:** `str` — Directory inode ID
    
</dd>
</dl>

<dl>
<dd>

**limit:** `typing.Optional[int]` — Maximum page size
    
</dd>
</dl>

<dl>
<dd>

**cursor:** `typing.Optional[str]` — Opaque directory page cursor
    
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

<details><summary><code>client.inodes.<a href="src/loonfs/inodes/client.py">list_revisions</a>(...) -> ListFileRevisionsResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.list_revisions(
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

<details><summary><code>client.inodes.<a href="src/loonfs/inodes/client.py">content</a>(...) -> typing.Iterator[bytes]</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.content(
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

<details><summary><code>client.inodes.<a href="src/loonfs/inodes/client.py">create_download</a>(...) -> BeginDownloadByInodeResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.inodes.create_download(
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

## Snapshots
<details><summary><code>client.snapshots.<a href="src/loonfs/snapshots/client.py">list</a>(...) -> ListSnapshotsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Lists live snapshots in snapshot-id order. Released and expired snapshots are omitted.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.snapshots.list(
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

**cursor:** `typing.Optional[str]` — Opaque snapshot-list page cursor
    
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

<details><summary><code>client.snapshots.<a href="src/loonfs/snapshots/client.py">create</a>(...) -> Snapshot</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Creates a snapshot of the current namespace state. Every call creates a new snapshot.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.snapshots.create(
    namespace_id="namespace_id",
    name="name",
    ttl_ms=1000000,
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

**name:** `str` — A label that does not need to be unique.
    
</dd>
</dl>

<dl>
<dd>

**ttl_ms:** `int` — Snapshot lifetime from the current server time, in milliseconds.
    
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

<details><summary><code>client.snapshots.<a href="src/loonfs/snapshots/client.py">extend</a>(...) -> Snapshot</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Extends a live snapshot without passing its lifetime limit. Repeating the request has the same result.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.snapshots.extend(
    namespace_id="namespace_id",
    snapshot_id="snapshot_id",
    ttl_ms=1000000,
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

**snapshot_id:** `str` — Snapshot id
    
</dd>
</dl>

<dl>
<dd>

**ttl_ms:** `int` — Requested lifetime from the server's current time, in milliseconds.
    
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

<details><summary><code>client.snapshots.<a href="src/loonfs/snapshots/client.py">release</a>(...) -> ReleaseSnapshotResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Releases a snapshot by id. Repeated releases succeed.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.snapshots.release(
    namespace_id="namespace_id",
    snapshot_id="snapshot_id",
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

**snapshot_id:** `str` — Snapshot id
    
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
<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">create</a>(...) -> BeginUploadResponse</code></summary>
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
from loonfs.server import LoonFS, BeginUploadRequest_ServiceProxied

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.create(
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

<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">retrieve</a>(...) -> UploadSession</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.retrieve(
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

<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">abort</a>(...) -> UploadSession</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.abort(
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

<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">complete</a>(...) -> UploadSession</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Completes an upload. The request mode must match the mode used to start the session. Direct uploads include a content claim; multipart also includes completed parts.
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
from loonfs.server import LoonFS, UploadCompletion_ServiceProxied

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.complete(
    namespace_id="namespace_id",
    upload_id="upload_id",
    request=UploadCompletion_ServiceProxied(),
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

**request:** `UploadCompletion` 
    
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

<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">put_content</a>(...) -> UploadContentResponse</code></summary>
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
client.uploads.put_content(...)
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

<details><summary><code>client.uploads.<a href="src/loonfs/uploads/client.py">sign_parts</a>(...) -> SignUploadPartsResponse</code></summary>
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
from loonfs.server import LoonFS, UploadPartChecksumClaim, Checksum

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.uploads.sign_parts(
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

Parts to authorize and the checksum for each part. Requesting a part
again replaces the previous upload for that part number.
    
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

## Admin Checkpoints
<details><summary><code>client.admin.checkpoints.<a href="src/loonfs/admin/checkpoints/client.py">list</a>(...) -> ListCheckpointsResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.checkpoints.list(
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

<details><summary><code>client.admin.checkpoints.<a href="src/loonfs/admin/checkpoints/client.py">create</a>(...) -> Checkpoint</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.checkpoints.create(
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

<details><summary><code>client.admin.checkpoints.<a href="src/loonfs/admin/checkpoints/client.py">release</a>(...) -> ReleaseCheckpointResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.checkpoints.release(
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

## Admin Diagnostics
<details><summary><code>client.admin.diagnostics.<a href="src/loonfs/admin/diagnostics/client.py">retrieve</a>(...) -> NamespaceDiagnostics</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.diagnostics.retrieve(
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

## Admin GrepIndex
<details><summary><code>client.admin.grep_index.<a href="src/loonfs/admin/grep_index/client.py">retrieve</a>(...) -> GrepIndex</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.grep_index.retrieve(
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

<details><summary><code>client.admin.grep_index.<a href="src/loonfs/admin/grep_index/client.py">disable</a>(...) -> GrepIndex</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.grep_index.disable(
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

<details><summary><code>client.admin.grep_index.<a href="src/loonfs/admin/grep_index/client.py">enable</a>(...) -> GrepIndex</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.grep_index.enable(
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

<details><summary><code>client.admin.grep_index.<a href="src/loonfs/admin/grep_index/client.py">gc</a>(...) -> GrepGcResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.grep_index.gc(
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

## Admin Maintenance
<details><summary><code>client.admin.maintenance.<a href="src/loonfs/admin/maintenance/client.py">run</a>(...) -> MaintenanceStepResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Runs one bounded maintenance step. Include `metadata_maintenance`, `retention`, or `gc` to select actions. Each selector is an options object, and an empty object uses server defaults. Actions run in that order, and only selected actions appear in the response. At least one action is required. A deleted namespace accepts only `gc`. GC processes up to 1024 candidates by default and returns a cursor when more work remains. A lost root update race is reported as an outcome.
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.maintenance.run(
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

**gc:** `typing.Optional[GcRequest]` 

Run one bounded mark-and-sweep garbage-collection pass. Omit this
field to skip garbage collection.
    
</dd>
</dl>

<dl>
<dd>

**metadata_maintenance:** `typing.Optional[MetadataMaintenanceRequest]` 

Flush the visible WAL tail into metadata segments, then run one bounded
reorganization step.
    
</dd>
</dl>

<dl>
<dd>

**retention:** `typing.Optional[AdvanceRetentionRequest]` 

Advance the retention floor to the flushed manifest head. Include this
field to select the action.
    
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

## Admin Store
<details><summary><code>client.admin.store.<a href="src/loonfs/admin/store/client.py">probe</a>(...) -> StoreProbeResponse</code></summary>
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
from loonfs.server import LoonFS

client = LoonFS(
    token="<token>",
    base_url="https://yourhost.com/path/to/api",
)

client.admin.store.probe(
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

