OSS SDK for Python 版本记录
===========================

Python SDK的版本号遵循 `Semantic Versioning <http://semver.org/>`_ 规则。

Version 2.1.1
-------------

- 修复：issue #28。
- 修复：正确的设置连接池大小。


Version 2.1.0
-------------

- 增加：可以通过 `oss2.defaults.connection_pool_size` 来设置连接池的最大连接数。
- 增加：可以通过 `oss2.resumable_upload` 函数的 `num_threads` 参数指定并发的线程数，来进行并发上传。
- 增加：提供断点下载函数 `oss2.resumable_download` 。
- 修复：保存断点信息的文件名应该由“规则化”的本地文件名生成；当断点信息文件格式不是json时，删除断点信息文件。
- 修复：修复一些文档的Bug。

Version 2.0.6
-------------

- 增加：可以通过新增的 `StsAuth` 类，进行STS临时授权
- 增加：加入Travis CI的支持
- 改变：对unit test进行了初步的梳理；

Version 2.0.5
-------------

- 改变：缺省的connect timeout由10秒改为60秒。为了兼容老的requests库（版本低于2.4.0），目前connect timeout和read timeout是同一个值，为了避免
CopyObject、UploadPartCopy因read timeout超时，故把这个超时时间设长。
- 增加：把 `security-token` 加入到子资源中，参与签名。
- 修复：用户可以通过设置oss2.defaults里的变量值，直接修改缺省参数

Version 2.0.4
-------------

- 改变：增加了unittest目录，原先的tests作为functional test；Tox默认是跑unittest
- 修复：按照依赖明确排除requests 2.9.0。因为 `Issue 2844 <https://github.com/kennethreitz/requests/issues/2844>`_ 导致不能传输UTF-8数据。
- 修复：Object名以'/'开头时，oss server应该报InvalidObjectName，而不是报SignatureDoesNotMatch。原因是URL中对'/'也要做URL编码。
- 修复：MANIFEST.in中改正README.rst等



Version 2.0.3
-------------

- 重新设计Python SDK，不再基于原有的官方0.x.x版本开发。
- 只支持Python2.6及以上版本，支持Python 3。
- 基于requests库
