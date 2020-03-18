---
title: Dosya ve Akış G/Ç - .NET
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
ms.openlocfilehash: 3c69e0fd23b1f8bc11fe908c66ba492f31a53f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706601"
---
# <a name="file-and-stream-io"></a>Dosya ve Akış G/Ç

Dosya ve akış I/O (giriş/çıkış) bir veri aktarımının depolama ortamına mı gittiğini yoksa oradan mı geldiğini belirtir. .NET Framework'de `System.IO` ad alanları, veri akışları ve dosyalar üzerinde eşzamanlı ve eşzamanlı olarak okuma ve yazmayı etkinleştiren türler içerir. Bu ad alanları aynı zamanda dosyaları sıkıştırma ve sıkıştırmayı açma işini gerçekleştiren türleri ve borular ve seri bağlantı noktaları üzerinden iletişim sağlayan türleri içerir.

Bir dosya kalıcı depolaması olan bir sipariş edilen ve adlandırılmış bayt toplamıdır. Bu dosyalarla çalışırken dizin yolları, disk depolama ve dosya ve dizin adları ile çalışırsınız. Buna karşılık akış birkaç depolama ortamından biri olan (örneğin disk veya bellek) yedekleme deposuna yazma ve yedekleme deposundan okuma için kullanılan bir sıra bayttır. Disklerden başka sadece birkaç yedekleme deposu olduğu gibi ağ, bellek ve boru akışları gibi dosya akışlarından farklı olan birkaç tür akış vardır.

## <a name="files-and-directories"></a>Dosyalar ve dizinler

Dosya ve dizinlerle <xref:System.IO?displayProperty=nameWithType> etkileşim kurmak için ad alanındaki türleri kullanabilirsiniz. Örneğin, dosyalar ve dizinler için özellikleri alabilir ve ayarlayabilirsiniz. Ayrıca arama ölçütlerine dayanarak bir dizi dosya ve dizini alabilirsiniz.

Yol adlandırma kuralları ve .NET Core 1.1 ve sonraki yıllarda desteklenen DOS aygıt sözdizimi ve daha sonra .NET Framework 4.6.2 ve sonraki leri de dahil olmak üzere Windows sistemleri için bir dosya yolunu ifade etmenin yolları için [Bkz.](file-path-formats.md)

Yaygın olarak kullanılan bazı dosya ve dizin sınıfları şunlardır:

- <xref:System.IO.File>- dosyaları oluşturmak, kopyalamak, silerken, taşımak ve açmak için <xref:System.IO.FileStream> statik yöntemler sağlar ve bir nesne oluşturmaya yardımcı olur.

- <xref:System.IO.FileInfo>- dosyaları oluşturmak, kopyalamak, silerken, taşımak ve açmak için <xref:System.IO.FileStream> örnek yöntemleri sağlar ve bir nesne oluşturmaya yardımcı olur.

- <xref:System.IO.Directory>- dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve sayısallandırma için statik yöntemler sağlar.

- <xref:System.IO.DirectoryInfo>- dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve sayısallandırma için örnek yöntemler sağlar.

- <xref:System.IO.Path>- dizin dizelerini platformlar arası bir şekilde işlemek için yöntem ve özellikler sağlar.

Dosya sistemi yöntemlerini ararken her zaman sağlam özel durum işleme sağlamalısınız. Daha fazla bilgi için Bkz. [Kullanım G/Ç hataları.](handling-io-errors.md)

Visual Basic kullanıcıları bu sınıfları kullanmanın <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> yanı sıra, sınıf tarafından sağlanan yöntemleri ve özellikleri dosya G/Ç için de kullanabilir.

[Bkz. Nasıl İş Lenir: Dizinleri Kopyalama](how-to-copy-directories.md), [Nasıl Yapıl: Dizin Girişi Oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))ve Nasıl [Sıralan: Dizin leri ve Dosyaları Nasıl Sırala.](how-to-enumerate-directories-and-files.md)

## <a name="streams"></a>Akışlar

Soyut taban <xref:System.IO.Stream> sınıfı bayt okuma ve yazmayı destekler. Akışları temsil eden tüm sınıflar <xref:System.IO.Stream> sınıftan devralır. Sınıf <xref:System.IO.Stream> ve türetilmiş sınıfları veri kaynakları nın ve depolarının ortak bir görünümünü sağlar ve programcıyı işletim sisteminin ve temel aygıtların belirli ayrıntılarından yalıtabilir.

Akışlar üç temel işlemi içerir:

- Okuma - bir bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma.

- Yazma - veri kaynağından bir akışa veri aktarma.

- Arama - geçerli konumu bir akış içinde sorgulama ve değiştirme.

Veri kaynağına veya havuza bağlı olarak, bir akış yalnızca bu yeteneklerin bazılarını destekleyebilir. Örneğin, <xref:System.IO.Pipes.PipeStream> sınıf arama desteklemez. Bir <xref:System.IO.Stream.CanRead%2A> <xref:System.IO.Stream.CanWrite%2A>akışın <xref:System.IO.Stream.CanSeek%2A> , ve özellikleri, akışın desteklediği işlemleri belirtir.

Bazı yaygın olarak kullanılan akış sınıfları şunlardır:

- <xref:System.IO.FileStream>– bir dosyayı okumak ve yazmak için.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>– yalıtılmış depolama alanında bir dosyaya okuma ve yazma için.

- <xref:System.IO.MemoryStream>– okuma ve arka mağaza olarak belleğe yazma için.

- <xref:System.IO.BufferedStream>– okuma ve yazma işlemlerinin performansını artırmak için.

- <xref:System.Net.Sockets.NetworkStream>– ağ yuvaları üzerinden okumak ve yazmak için.

- <xref:System.IO.Pipes.PipeStream>– Anonim ve adlandırılmış borular üzerinde okuma ve yazma için.

- <xref:System.Security.Cryptography.CryptoStream>– veri akışlarını şifreleme dönüşümlerine bağlamak için kullanılır.

Akışları eş zamanlı olarak çalışma örneği için, [Bkz. Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Okuyucular ve yazarlar

Ad <xref:System.IO?displayProperty=nameWithType> alanı ayrıca, kodlanmış karakterleri akışlardan okuma ve akışlara yazmak için de çeşitli türler sağlar. Genellikle, akışlar giriş ve çıkış baytı için tasarlanmıştır. Okuyucu ve yazıcı türleri kodlanmış karakterlerin baytlardan ve baytlara dönüşümünü işler ve böylece akış işlemi tamamlar. Her okuyucu ve yazar sınıfı, sınıfın `BaseStream` özelliği üzerinden alınabilen bir akışla ilişkilidir.

Bazı yaygın olarak kullanılan okuyucu ve yazıcı sınıfları şunlardır:

- <xref:System.IO.BinaryReader>ve <xref:System.IO.BinaryWriter> – ilkel veri türlerini ikili değerler olarak okumak ve yazmak için.

- <xref:System.IO.StreamReader>ve <xref:System.IO.StreamWriter> – karakterleri baytlara dönüştürmek için kodlama değeri kullanarak karakterleri okumak ve yazmak için.

- <xref:System.IO.StringReader>ve <xref:System.IO.StringWriter> – karakterleri okumak ve dizelerden yazmak için.

- <xref:System.IO.TextReader>ve <xref:System.IO.TextWriter> – karakterleri ve dizeleri okuyup yazan, ancak ikili veri yazan diğer okuyucu ve yazarlar için soyut temel sınıflar olarak hizmet vermektedir.

[Bkz. Nasıl Yazılır: Dosyadan Metin Okuma](how-to-read-text-from-a-file.md), [Nasıl Yazılır: Dosyaya Metin Yazma](how-to-write-text-to-a-file.md), Nasıl [Yazılır: String'ten Karakterleri Okuma](how-to-read-characters-from-a-string.md)ve Nasıl [Yazılır: Karakterleri Dize'ye Yazma](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Asynchronous G/Ç işlemleri

Büyük miktarda veriyi okumak veya yazmak kaynak yoğunluğu olabilir. Eğer uygulamanız kullanıcıya hassas kalması gerekiyorsa bu işlemleri zaman uyumsuz gerçekleştirebilirsiniz. Zaman uyumlu G/Ç işlemleri ile UI iş parçacığı kaynak yoğunluğu işlemi bitene kadar durdurulur.  Uygulamanızın çalışmayı durdurduğu izlenimini oluşturmayı önlemek için Windows 8.x Store uygulamalarını geliştirirken eşzamanlı G/Ç işlemleri kullanın.

Eşzamanlı üyeler adlarında `Async` <xref:System.IO.Stream.CopyToAsync%2A>, , <xref:System.IO.Stream.FlushAsync%2A> <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> yöntemler gibi içerirler. Bu yöntemleri `async` `await` anahtar kelimelerle birlikte kullanırsınız.

Daha fazla bilgi için Bkz. [Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="compression"></a>Sıkıştırma

Sıkıştırma depolama için bir dosyanın boyutunu küçültme işlemini gösterir. Açma sıkıştırılmış bir dosyanın içeriğini ayıklanması işlemidir ve böylece kullanılabilir bir formata girerler. Ad <xref:System.IO.Compression?displayProperty=nameWithType> alanı, dosyaları ve akışları sıkıştırma ve sıkıştırma için türleri içerir.

Aşağıdaki sınıflar, dosya ve akışları sıkıştırma ve açma işlemi olurken sıkça kullanılır.

- <xref:System.IO.Compression.ZipArchive>– zip arşivindeki girişleri oluşturmak ve almak için.

- <xref:System.IO.Compression.ZipArchiveEntry>– sıkıştırılmış bir dosyayı temsil etmek için.

- <xref:System.IO.Compression.ZipFile>– sıkıştırılmış bir paket oluşturmak, çıkarmak ve açmak için.

- <xref:System.IO.Compression.ZipFileExtensions>– sıkıştırılmış bir pakette giriş oluşturmak ve ayıklamak için.

- <xref:System.IO.Compression.DeflateStream>– Deflate algoritmasını kullanarak akışları sıkıştırmak ve dekomprese etmek için.

- <xref:System.IO.Compression.GZipStream>– gzip veri formatında akışları sıkıştırmak ve dekomprese etmek için.

[Bkz. Nasıl: Dosyaları Sıkıştır Ve Ayıkla.](how-to-compress-and-extract-files.md)

## <a name="isolated-storage"></a>Yalıtılmış depolama

Yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Depolama kullanıcı, derleme ve etki alanı (isteğe bağlı) tarafından izole edilmiş bir sanal bir dosya sistemi sağlar. Yalıtılmış depolama özellikle uygulamanızın kullanıcı dosyalarına erişim izni yokken yararlıdır. Uygulamanız bilgisayarın güvenlik ilkesi tarafından kontrol edilir bir şekilde ayarlar veya dosyaları kaydedebilirsiniz.

Windows 8.x Store uygulamaları için yalıtılmış depolama alanı kullanılamaz; bunun yerine, <xref:Windows.Storage?displayProperty=nameWithType> ad alanında uygulama veri sınıflarını kullanın. Daha fazla bilgi için [Uygulama verilerine](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29)bakın.

Aşağıdaki sınıflar yalıtılmış depolama uygularken sık kullanılır:

- <xref:System.IO.IsolatedStorage.IsolatedStorage>– yalıtılmış depolama uygulamaları için taban sınıf sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>– dosya ve dizinler içeren yalıtılmış bir depolama alanı sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>- yalıtılmış depolama içinde bir dosya ortaya çıkarır.

Bkz. [Yalıtılmış Depolama](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Windows Mağazası uygulamalarında G/Ç işlemleri

Windows 8.x Store uygulamaları için .NET, akışlardan okuma ve yazma türlerinin çoğunu içerir; ancak, bu küme tüm .NET Framework G/Ç türlerini içermez.

Windows 8.x Store uygulamalarında G/Ç işlemlerini kullanırken dikkat edilmesi gereken bazı önemli farklar:

- Özellikle <xref:System.IO.File>, , <xref:System.IO.FileInfo> <xref:System.IO.Directory> ve <xref:System.IO.DirectoryInfo>, gibi dosya işlemleriyle ilgili türler Windows 8.x Store uygulamaları için .NET'e dahil edilmez. Bunun yerine, Windows <xref:Windows.Storage?displayProperty=nameWithType> Runtime'ın ad alanında ki <xref:Windows.Storage.StorageFile> <xref:Windows.Storage.StorageFolder>türleri kullanın, örneğin.

- Yalıtılmış depolama kullanılamıyor; bunun yerine, [uygulama verilerini](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))kullanın.

- Kullanıcı Bira iş parçacığının <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A>engellenmesini önlemek için eşzamanlı yöntemler kullanın.

- Yol tabanlı sıkıştırma <xref:System.IO.Compression.ZipFile> türleri <xref:System.IO.Compression.ZipFileExtensions> ve kullanılamıyor. Bunun yerine, <xref:Windows.Storage.Compression?displayProperty=nameWithType> ad alanındaki türleri kullanın.

Gerekirse, .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüşüm yapabilirsiniz. Daha fazla bilgi için [bkz: .NET Framework Streams ve Windows Runtime Akışları arasında dönüştürme](how-to-convert-between-dotnet-streams-and-winrt-streams.md) veya <xref:System.IO.WindowsRuntimeStreamExtensions>.

Bir Windows 8.x Store uygulamasındaki G/Ç işlemleri hakkında daha fazla bilgi için [Quickstart: Okuma ve yazma dosyaları](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))na bakın.

## <a name="io-and-security"></a>G/Ç ve güvenlik

<xref:System.IO?displayProperty=nameWithType> Ad alanında sınıfları kullandığınızda, dosyalara ve dizinlere erişimi denetlemek için erişim denetim listeleri (ALA'lar) gibi işletim sistemi güvenlik gereksinimlerini izlemeniz gerekir. Bu gereksinim, tüm <xref:System.Security.Permissions.FileIOPermission> gereksinimlere ek olarak yapılır. ACL'leri program aracılığıyla yönetebilirsiniz. Daha fazla bilgi için [bkz: Erişim Denetim Listesi Girişleri Ekle veya Kaldır.](how-to-add-or-remove-access-control-list-entries.md)

Varsayılan güvenlik ilkeleri, internet veya intranet uygulamalarının kullanıcının bilgisayarındaki dosyalara erişmesini engeller. Bu nedenle, internet veya intranet üzerinden indirilecek kodu yazarken fiziksel bir dosyaya olan yolu gerektirecek g/ç sınıflarını kullanmayın. Bunun yerine, geleneksel .NET Framework uygulamaları için [yalıtılmış depolamayı](isolated-storage.md) kullanın veya Windows 8.x Store uygulamaları için [uygulama verilerini](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) kullanın.

Güvenlik denetimi yalnızca akış oluşturulduğunda gerçekleştirilir. Bu nedenle, bir akış açmayın ve sonra onu en az güvenilen koda veya uygulama alanına geçirin.

## <a name="related-topics"></a>İlgili konular

- [Yaygın G/Ç Görevleri](common-i-o-tasks.md)\
Dosyalar, dizinler, akışları ve ilgili içerik ile her görevin örneği ile ilişkili g/ç görevlerinin bir listesini sağlar.

- [Asynchronous Dosya I/O](asynchronous-file-i-o.md)\
Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.

- [Yalıtılmış Depolama](isolated-storage.md)\
Kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasını tanımlar.

- [Boru](pipe-operations.md)\
.NET Framework içindeki anonim ve adlandırılmış yöneltme işlemlerini açıklar.

- [Bellek Eşlenen Dosyalar](memory-mapped-files.md)\
Sanal bellek içindeki disk üzerinde bulunan dosyaların içeriğini içeren bellek eşlemeli dosyaları açıklar. Büyük dosyaları düzenlemek ve işlemler arası iletişim için olan paylaşılan belleği oluşturmak için bellek eşlemeli dosyaları kullanabilirsiniz.
