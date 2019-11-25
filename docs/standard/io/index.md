---
title: File and Stream I/O - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 889271ca41fb84b44757adfffc61ffbfbc0a03a8
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204794"
---
# <a name="file-and-stream-io"></a>Dosya ve Akış G/Ç

Dosya ve akış I/O (giriş/çıkış) bir veri aktarımının depolama ortamına mı gittiğini yoksa oradan mı geldiğini belirtir. In the .NET Framework, the `System.IO` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files. Bu ad alanları aynı zamanda dosyaları sıkıştırma ve sıkıştırmayı açma işini gerçekleştiren türleri ve borular ve seri bağlantı noktaları üzerinden iletişim sağlayan türleri içerir.

Bir dosya kalıcı depolaması olan bir sipariş edilen ve adlandırılmış bayt toplamıdır. Bu dosyalarla çalışırken dizin yolları, disk depolama ve dosya ve dizin adları ile çalışırsınız. Buna karşılık akış birkaç depolama ortamından biri olan (örneğin disk veya bellek) yedekleme deposuna yazma ve yedekleme deposundan okuma için kullanılan bir sıra bayttır. Disklerden başka sadece birkaç yedekleme deposu olduğu gibi ağ, bellek ve boru akışları gibi dosya akışlarından farklı olan birkaç tür akış vardır.

## <a name="files-and-directories"></a>Files and directories

You can use the types in the <xref:System.IO?displayProperty=nameWithType> namespace to interact with files and directories. Örneğin, dosyalar ve dizinler için özellikleri alabilir ve ayarlayabilirsiniz. Ayrıca arama ölçütlerine dayanarak bir dizi dosya ve dizini alabilirsiniz.

For path naming conventions and the ways to express a file path for Windows systems, including with the DOS device syntax supported in .NET Core 1.1 and later and the .NET Framework 4.6.2 and later, see [File path formats on Windows systems](file-path-formats.md).

Yaygın olarak kullanılan bazı dosya ve dizin sınıfları şunlardır:

- <xref:System.IO.File> - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.

- <xref:System.IO.FileInfo> - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.

- <xref:System.IO.Directory> - provides static methods for creating, moving, and enumerating through directories and subdirectories.

- <xref:System.IO.DirectoryInfo> - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

- <xref:System.IO.Path> - provides methods and properties for processing directory strings in a cross-platform manner.

You should always provide robust exception handling when calling filesystem methods. For more information, see [Handling I/O errors](handling-io-errors.md).

In addition to using these classes, Visual Basic users can use the methods and properties provided by the <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> class for file I/O.

See [How to: Copy Directories](how-to-copy-directories.md), [How to: Create a Directory Listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100)), and [How to: Enumerate Directories and Files](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Akışlar

The abstract base class <xref:System.IO.Stream> supports reading and writing bytes. All classes that represent streams inherit from the <xref:System.IO.Stream> class. The <xref:System.IO.Stream> class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.

Akışlar üç temel işlemi içerir:

- Okuma - bir bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma.

- Yazma - veri kaynağından bir akışa veri aktarma.

- Arama - geçerli konumu bir akış içinde sorgulama ve değiştirme.

Veri kaynağına veya havuza bağlı olarak, bir akış yalnızca bu yeteneklerin bazılarını destekleyebilir. For example, the <xref:System.IO.Pipes.PipeStream> class does not support seeking. The <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, and <xref:System.IO.Stream.CanSeek%2A> properties of a stream specify the operations that the stream supports.

Bazı yaygın olarak kullanılan akış sınıfları şunlardır:

- <xref:System.IO.FileStream> – for reading and writing to a file.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – for reading and writing to a file in isolated storage.

- <xref:System.IO.MemoryStream> – for reading and writing to memory as the backing store.

- <xref:System.IO.BufferedStream> – for improving performance of read and write operations.

- <xref:System.Net.Sockets.NetworkStream> – for reading and writing over network sockets.

- <xref:System.IO.Pipes.PipeStream> – for reading and writing over anonymous and named pipes.

- <xref:System.Security.Cryptography.CryptoStream> – for linking data streams to cryptographic transformations.

For an example of working with streams asynchronously, see [Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Readers and writers

The <xref:System.IO?displayProperty=nameWithType> namespace also provides types for reading encoded characters from streams and writing them to streams. Genellikle, akışlar giriş ve çıkış baytı için tasarlanmıştır. Okuyucu ve yazıcı türleri kodlanmış karakterlerin baytlardan ve baytlara dönüşümünü işler ve böylece akış işlemi tamamlar. Each reader and writer class is associated with a stream, which can be retrieved through the class's `BaseStream` property.

Bazı yaygın olarak kullanılan okuyucu ve yazıcı sınıfları şunlardır:

- <xref:System.IO.BinaryReader> and <xref:System.IO.BinaryWriter> – for reading and writing primitive data types as binary values.

- <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> – for reading and writing characters by using an encoding value to convert the characters to and from bytes.

- <xref:System.IO.StringReader> and <xref:System.IO.StringWriter> – for reading and writing characters to and from strings.

- <xref:System.IO.TextReader> and <xref:System.IO.TextWriter> – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

See [How to: Read Text from a File](how-to-read-text-from-a-file.md), [How to: Write Text to a File](how-to-write-text-to-a-file.md), [How to: Read Characters from a String](how-to-read-characters-from-a-string.md), and [How to: Write Characters to a String](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Asynchronous I/O operations

Büyük miktarda veriyi okumak veya yazmak kaynak yoğunluğu olabilir. Eğer uygulamanız kullanıcıya hassas kalması gerekiyorsa bu işlemleri zaman uyumsuz gerçekleştirebilirsiniz. Zaman uyumlu G/Ç işlemleri ile UI iş parçacığı kaynak yoğunluğu işlemi bitene kadar durdurulur.  Use asynchronous I/O operations when developing Windows 8.x Store apps to prevent creating the impression that your app has stopped working.

The asynchronous members contain `Async` in their names, such as the <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>,  <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> methods. You use these methods with the `async` and `await` keywords.

For more information, see [Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="compression"></a>Sıkıştırma

Sıkıştırma depolama için bir dosyanın boyutunu küçültme işlemini gösterir. Açma sıkıştırılmış bir dosyanın içeriğini ayıklanması işlemidir ve böylece kullanılabilir bir formata girerler. The <xref:System.IO.Compression?displayProperty=nameWithType> namespace contains types for compressing and decompressing files and streams.

Aşağıdaki sınıflar, dosya ve akışları sıkıştırma ve açma işlemi olurken sıkça kullanılır.

- <xref:System.IO.Compression.ZipArchive> – for creating and retrieving entries in the zip archive.

- <xref:System.IO.Compression.ZipArchiveEntry> – for representing a compressed file.

- <xref:System.IO.Compression.ZipFile> – for creating,  extracting, and opening a compressed package.

- <xref:System.IO.Compression.ZipFileExtensions> – for creating and extracting entries in a compressed package.

- <xref:System.IO.Compression.DeflateStream> – for compressing and decompressing streams using the Deflate algorithm.

- <xref:System.IO.Compression.GZipStream> – for compressing and decompressing streams in gzip data format.

See [How to: Compress and Extract Files](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Isolated storage

Yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Depolama kullanıcı, derleme ve etki alanı (isteğe bağlı) tarafından izole edilmiş bir sanal bir dosya sistemi sağlar. Yalıtılmış depolama özellikle uygulamanızın kullanıcı dosyalarına erişim izni yokken yararlıdır. Uygulamanız bilgisayarın güvenlik ilkesi tarafından kontrol edilir bir şekilde ayarlar veya dosyaları kaydedebilirsiniz.

Isolated storage is not available for Windows 8.x Store apps; instead, use application data classes in the <xref:Windows.Storage?displayProperty=nameWithType> namespace. For more information, see [Application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Aşağıdaki sınıflar yalıtılmış depolama uygularken sık kullanılır:

- <xref:System.IO.IsolatedStorage.IsolatedStorage> – provides the base class for isolated storage implementations.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – provides an isolated storage area that contains files and directories.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - exposes a file within isolated storage.

See [Isolated Storage](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>I/O operations in Windows Store apps

The [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] contains many of the types for reading from and writing to streams; however, this set does not include all the .NET Framework I/O types.

Some important differences to note when using I/O operations in Windows 8.x Store apps:

- Types specifically related to file operations, such as <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> and <xref:System.IO.DirectoryInfo>, are not included in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Instead, use the types in the <xref:Windows.Storage?displayProperty=nameWithType> namespace of the Windows Runtime, such as <xref:Windows.Storage.StorageFile> and <xref:Windows.Storage.StorageFolder>.

- Isolated storage is not available; instead, use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Use asynchronous methods, such as <xref:System.IO.Stream.ReadAsync%2A> and <xref:System.IO.Stream.WriteAsync%2A>, to prevent blocking the UI thread.

- The path-based compression types <xref:System.IO.Compression.ZipFile> and <xref:System.IO.Compression.ZipFileExtensions> are not available. Instead, use the types in the <xref:Windows.Storage.Compression?displayProperty=nameWithType> namespace.

Gerekirse, .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüşüm yapabilirsiniz. For more information, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md) or <xref:System.IO.WindowsRuntimeStreamExtensions>.

For more information about I/O operations in a Windows 8.x Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>I/O and security

When you use the classes in the <xref:System.IO?displayProperty=nameWithType> namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories. This requirement is in addition to any <xref:System.Security.Permissions.FileIOPermission> requirements. ACL'leri program aracılığıyla yönetebilirsiniz. For more information, see [How to: Add or Remove Access Control List Entries](how-to-add-or-remove-access-control-list-entries.md).

Varsayılan güvenlik ilkeleri, internet veya intranet uygulamalarının kullanıcının bilgisayarındaki dosyalara erişmesini engeller. Bu nedenle, internet veya intranet üzerinden indirilecek kodu yazarken fiziksel bir dosyaya olan yolu gerektirecek g/ç sınıflarını kullanmayın. Instead, use [isolated storage](isolated-storage.md) for traditional .NET Framework applications, or use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) for Windows 8.x Store apps.

Güvenlik denetimi yalnızca akış oluşturulduğunda gerçekleştirilir. Bu nedenle, bir akış açmayın ve sonra onu en az güvenilen koda veya uygulama alanına geçirin.

## <a name="related-topics"></a>İlgili konular

- [Common I/O Tasks](common-i-o-tasks.md)\
Dosyalar, dizinler, akışları ve ilgili içerik ile her görevin örneği ile ilişkili g/ç görevlerinin bir listesini sağlar.

- [Asynchronous File I/O](asynchronous-file-i-o.md)\
Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.

- [Isolated Storage](isolated-storage.md)\
Kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasını tanımlar.

- [Pipes](pipe-operations.md)\
.NET Framework içindeki anonim ve adlandırılmış yöneltme işlemlerini açıklar.

- [Memory-Mapped Files](memory-mapped-files.md)\
Sanal bellek içindeki disk üzerinde bulunan dosyaların içeriğini içeren bellek eşlemeli dosyaları açıklar. Büyük dosyaları düzenlemek ve işlemler arası iletişim için olan paylaşılan belleği oluşturmak için bellek eşlemeli dosyaları kullanabilirsiniz.
