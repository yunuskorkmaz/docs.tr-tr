---
title: Dosya ve akış g/ç-.NET
description: .NET ' te, verilerin bir depolama ortamına ya da bir depolama ortamına aktarılması olan dosya ve akış g/ç 'nin temellerini öğrenin.
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
ms.openlocfilehash: 2f7da6bd967abce8c2fefdc54a0043b5505e22e3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558946"
---
# <a name="file-and-stream-io"></a>Dosya ve Akış G/Ç

Dosya ve akış I/O (giriş/çıkış) bir veri aktarımının depolama ortamına mı gittiğini yoksa oradan mı geldiğini belirtir. .NET Framework `System.IO` ad alanları, veri akışlarında ve dosyalarında hem zaman uyumlu hem de zaman uyumsuz olarak okuma ve yazma olanağı sağlayan türler içerir. Bu ad alanları aynı zamanda dosyaları sıkıştırma ve sıkıştırmayı açma işini gerçekleştiren türleri ve borular ve seri bağlantı noktaları üzerinden iletişim sağlayan türleri içerir.

Bir dosya kalıcı depolaması olan bir sipariş edilen ve adlandırılmış bayt toplamıdır. Bu dosyalarla çalışırken dizin yolları, disk depolama ve dosya ve dizin adları ile çalışırsınız. Buna karşılık akış birkaç depolama ortamından biri olan (örneğin disk veya bellek) yedekleme deposuna yazma ve yedekleme deposundan okuma için kullanılan bir sıra bayttır. Disklerden başka sadece birkaç yedekleme deposu olduğu gibi ağ, bellek ve boru akışları gibi dosya akışlarından farklı olan birkaç tür akış vardır.

## <a name="files-and-directories"></a>Dosyalar ve dizinler

<xref:System.IO?displayProperty=nameWithType>Dosya ve dizinler ile etkileşim kurmak için ad alanındaki türleri kullanabilirsiniz. Örneğin, dosyalar ve dizinler için özellikleri alabilir ve ayarlayabilirsiniz. Ayrıca arama ölçütlerine dayanarak bir dizi dosya ve dizini alabilirsiniz.

Yol adlandırma kuralları ve Windows sistemlerine yönelik bir dosya yolu ifade etmek için .NET Core 1,1 ve üzeri sürümlerde desteklenen DOS cihaz sözdizimi ve .NET Framework 4.6.2 ve sonraki sürümleri için, bkz. [Windows sistemlerinde dosya yolu biçimleri](file-path-formats.md).

Yaygın olarak kullanılan bazı dosya ve dizin sınıfları şunlardır:

- <xref:System.IO.File> -dosya oluşturma, kopyalama, silme, taşıma ve açma için statik yöntemler sağlar ve bir nesne oluşturulmasına yardımcı olur <xref:System.IO.FileStream> .

- <xref:System.IO.FileInfo> -dosya oluşturma, kopyalama, silme, taşıma ve açma için örnek yöntemleri sağlar ve bir nesne oluşturulmasına yardımcı olur <xref:System.IO.FileStream> .

- <xref:System.IO.Directory> -dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve sıralama için statik yöntemler sağlar.

- <xref:System.IO.DirectoryInfo> -dizinler ve alt dizinler aracılığıyla oluşturma, taşıma ve numaralandırma için örnek yöntemleri sağlar.

- <xref:System.IO.Path> -platformlar arası bir şekilde dizin dizelerini işlemek için yöntemler ve özellikler sağlar.

Dosya sistemi yöntemlerini çağırırken her zaman güçlü özel durum işleme sağlamanız gerekir. Daha fazla bilgi için bkz. [g/ç hatalarını işleme](handling-io-errors.md).

Visual Basic kullanıcılar bu sınıfları kullanmanın yanı sıra <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> dosya g/ç için sınıfı tarafından sunulan yöntemleri ve özellikleri kullanabilir.

Bkz. [nasıl yapılır: dizinleri kopyalama](how-to-copy-directories.md), [nasıl yapılır: Dizin listesi oluşturma](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))ve [nasıl yapılır: dizinleri ve dosyaları listeleme](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Akışlar

Soyut temel sınıf, <xref:System.IO.Stream> baytları okumayı ve yazmayı destekler. Akışları temsil eden tüm sınıflar <xref:System.IO.Stream> sınıfından devralınır. <xref:System.IO.Stream>Sınıfı ve türetilmiş sınıfları, veri kaynakları ve depoların ortak bir görünümünü sağlar ve programcı 'yı işletim sisteminin ve temel cihazların belirli ayrıntılarından yalıtır.

Akışlar üç temel işlemi içerir:

- Okuma - bir bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma.

- Yazma - veri kaynağından bir akışa veri aktarma.

- Arama - geçerli konumu bir akış içinde sorgulama ve değiştirme.

Veri kaynağına veya havuza bağlı olarak, bir akış yalnızca bu yeteneklerin bazılarını destekleyebilir. Örneğin, <xref:System.IO.Pipes.PipeStream> sınıfı aramayı desteklemez. <xref:System.IO.Stream.CanRead%2A>Akışın, <xref:System.IO.Stream.CanWrite%2A> ve <xref:System.IO.Stream.CanSeek%2A> özellikleri akışın desteklediği işlemleri belirtir.

Bazı yaygın olarak kullanılan akış sınıfları şunlardır:

- <xref:System.IO.FileStream> – bir dosyaya okuma ve yazma için.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – yalıtılmış depolamada bir dosyaya okuma ve yazma için.

- <xref:System.IO.MemoryStream> – yedekleme deposu olarak belleğe okuma ve yazma için.

- <xref:System.IO.BufferedStream> – okuma ve yazma işlemlerinin performansını iyileştirmek için.

- <xref:System.Net.Sockets.NetworkStream> – Ağ yuvaları üzerinde okuma ve yazma için.

- <xref:System.IO.Pipes.PipeStream> – anonim ve adlandırılmış kanallar üzerinde okuma ve yazma için.

- <xref:System.Security.Cryptography.CryptoStream> – veri akışlarını şifreleme dönüşümlerine bağlamak için.

Akışlarla zaman uyumsuz olarak çalışma örneği için bkz. [zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Okuyucular ve yazarlar

<xref:System.IO?displayProperty=nameWithType>Ad alanı Ayrıca akışlardan kodlanmış karakterleri okumak ve akışlara yazmak için türler sağlar. Genellikle, akışlar giriş ve çıkış baytı için tasarlanmıştır. Okuyucu ve yazıcı türleri kodlanmış karakterlerin baytlardan ve baytlara dönüşümünü işler ve böylece akış işlemi tamamlar. Her okuyucu ve yazıcı sınıfı, sınıfın özelliği aracılığıyla alınabilecek bir akış ile ilişkilendirilir `BaseStream` .

Bazı yaygın olarak kullanılan okuyucu ve yazıcı sınıfları şunlardır:

- <xref:System.IO.BinaryReader> ve <xref:System.IO.BinaryWriter> – basit veri türlerini ikili değerler olarak okumak ve yazmak için.

- <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> karakterleri bir kodlama değeri kullanarak okumak ve yazmak için karakterleri bayta ve bayttan dönüştürür.

- <xref:System.IO.StringReader> ve, <xref:System.IO.StringWriter> dizeden ve dizeden karakter okumak ve yazmak için.

- <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> – diğer okuyucular ve yazarların karakter ve dizeleri okuyup yazacağı ancak ikili verileri içermeyen diğer okuyucular ve yazarlar için soyut temel sınıflar olarak görev yapar.

Bkz. [nasıl yapılır: dosyadan metin okuma](how-to-read-text-from-a-file.md), [nasıl yapılır: bir dosyaya metin yazma](how-to-write-text-to-a-file.md), [nasıl yapılır: bir dizeden karakter okuma](how-to-read-characters-from-a-string.md)ve [nasıl yapılır: bir dizeye karakter yazma](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Zaman uyumsuz g/ç işlemleri

Büyük miktarda veriyi okumak veya yazmak kaynak yoğunluğu olabilir. Eğer uygulamanız kullanıcıya hassas kalması gerekiyorsa bu işlemleri zaman uyumsuz gerçekleştirebilirsiniz. Zaman uyumlu G/Ç işlemleri ile UI iş parçacığı kaynak yoğunluğu işlemi bitene kadar durdurulur.  Uygulamanızın çalışmayı durdurduğu izlenimi oluşturmayı engellemek için Windows 8. x Mağazası uygulamaları geliştirirken zaman uyumsuz g/ç işlemlerini kullanın.

Zaman uyumsuz Üyeler,,, `Async` <xref:System.IO.Stream.CopyToAsync%2A> <xref:System.IO.Stream.FlushAsync%2A>  <xref:System.IO.Stream.ReadAsync%2A> ve yöntemleri gibi adlarında bulunur <xref:System.IO.Stream.WriteAsync%2A> . Bu yöntemleri `async` ve anahtar kelimeleri ile birlikte kullanırsınız `await` .

Daha fazla bilgi için bkz. [zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md).

## <a name="compression"></a>Sıkıştırma

Sıkıştırma depolama için bir dosyanın boyutunu küçültme işlemini gösterir. Açma sıkıştırılmış bir dosyanın içeriğini ayıklanması işlemidir ve böylece kullanılabilir bir formata girerler. <xref:System.IO.Compression?displayProperty=nameWithType>Ad alanı, dosyaları ve akışları sıkıştırmak ve sıkıştırmayı yapmak için türler içerir.

Aşağıdaki sınıflar, dosya ve akışları sıkıştırma ve açma işlemi olurken sıkça kullanılır.

- <xref:System.IO.Compression.ZipArchive> – ZIP arşivindeki girişleri oluşturmak ve almak için.

- <xref:System.IO.Compression.ZipArchiveEntry> – sıkıştırılmış bir dosyayı temsil etmek için.

- <xref:System.IO.Compression.ZipFile> – sıkıştırılmış bir paket oluşturmak, ayıklamak ve açmak için.

- <xref:System.IO.Compression.ZipFileExtensions> – sıkıştırılmış bir pakette giriş oluşturmak ve ayıklamak için.

- <xref:System.IO.Compression.DeflateStream> – Söndür algoritmasını kullanarak akışları sıkıştırmak ve sıkıştırmayı açma.

- <xref:System.IO.Compression.GZipStream> – bir gzip veri biçimindeki akışları sıkıştırmak ve sıkıştırmayı açma için.

Bkz. [nasıl yapılır: dosyaları sıkıştırma ve ayıklama](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Yalıtılmış depolama

Yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Depolama kullanıcı, derleme ve etki alanı (isteğe bağlı) tarafından izole edilmiş bir sanal bir dosya sistemi sağlar. Yalıtılmış depolama özellikle uygulamanızın kullanıcı dosyalarına erişim izni yokken yararlıdır. Uygulamanız bilgisayarın güvenlik ilkesi tarafından kontrol edilir bir şekilde ayarlar veya dosyaları kaydedebilirsiniz.

Yalıtılmış depolama, Windows 8. x Mağazası uygulamaları için kullanılamaz; Bunun yerine, ad alanındaki uygulama veri sınıflarını kullanın <xref:Windows.Storage?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [uygulama verileri](/previous-versions/windows/apps/hh464917(v=win.10)).

Aşağıdaki sınıflar yalıtılmış depolama uygularken sık kullanılır:

- <xref:System.IO.IsolatedStorage.IsolatedStorage> – yalıtılmış depolama uygulamaları için temel sınıf sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – dosyaları ve dizinleri içeren bir yalıtılmış depolama alanı sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> -yalıtılmış depolama içinde bir dosya gösterir.

Bkz. [yalıtılmış depolama](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Windows Mağazası uygulamalarında g/ç işlemleri

Windows 8. x Mağazası uygulamaları için .NET, akışları okuma ve akışlara yazma için birçok tür içerir; Ancak, bu küme tüm .NET Framework g/ç türlerini içermez.

Windows 8. x Mağaza uygulamalarında g/ç işlemlerini kullanırken dikkat edilmesi için bazı önemli farklılıklar:

- ,, Ve gibi dosya işlemleriyle özellikle ilgili türler <xref:System.IO.File> , <xref:System.IO.FileInfo> <xref:System.IO.Directory> <xref:System.IO.DirectoryInfo> Windows 8. x Mağazası uygulamaları için .net 'e dahil değildir. Bunun yerine, <xref:Windows.Storage?displayProperty=nameWithType> ve gibi Windows çalışma zamanı ad alanındaki türleri kullanın <xref:Windows.Storage.StorageFile> <xref:Windows.Storage.StorageFolder> .

- Yalıtılmış depolama kullanılamıyor; Bunun yerine, [uygulama verilerini](/previous-versions/windows/apps/hh464917(v=win.10))kullanın.

- <xref:System.IO.Stream.ReadAsync%2A> <xref:System.IO.Stream.WriteAsync%2A> UI iş parçacığını engellemeyi engellemek için ve gibi zaman uyumsuz yöntemleri kullanın.

- Yol tabanlı sıkıştırma türleri <xref:System.IO.Compression.ZipFile> ve <xref:System.IO.Compression.ZipFileExtensions> kullanılamıyor. Bunun yerine, ad alanındaki türleri kullanın <xref:Windows.Storage.Compression?displayProperty=nameWithType> .

Gerekirse, .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüşüm yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework akışlar ve Windows çalışma zamanı akışları arasında dönüştürme](how-to-convert-between-dotnet-streams-and-winrt-streams.md) <xref:System.IO.WindowsRuntimeStreamExtensions> .

Bir Windows 8. x Mağazası uygulamasındaki g/ç işlemleri hakkında daha fazla bilgi için bkz. [hızlı başlangıç: dosya okuma ve yazma](/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>G/ç ve güvenlik

<xref:System.IO?displayProperty=nameWithType>Ad alanındaki sınıfları kullandığınızda, dosyalara ve dizinlere erişimi denetlemek için erişim denetim listeleri (ACL 'ler) gibi işletim sistemi güvenlik gereksinimlerini izlemeniz gerekir. Bu gereksinim, tüm gereksinimlere ek olarak yapılır <xref:System.Security.Permissions.FileIOPermission> . ACL'leri program aracılığıyla yönetebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Access Control liste girişi ekleme veya kaldırma](how-to-add-or-remove-access-control-list-entries.md).

Varsayılan güvenlik ilkeleri, internet veya intranet uygulamalarının kullanıcının bilgisayarındaki dosyalara erişmesini engeller. Bu nedenle, internet veya intranet üzerinden indirilecek kodu yazarken fiziksel bir dosyaya olan yolu gerektirecek g/ç sınıflarını kullanmayın. Bunun yerine, geleneksel .NET Framework uygulamalar için [yalıtılmış depolama](isolated-storage.md) kullanın veya Windows 8. x Mağazası uygulamaları için [uygulama verilerini](/previous-versions/windows/apps/hh464917(v=win.10)) kullanın.

Güvenlik denetimi yalnızca akış oluşturulduğunda gerçekleştirilir. Bu nedenle, bir akış açmayın ve sonra onu en az güvenilen koda veya uygulama alanına geçirin.

## <a name="related-topics"></a>İlgili konular

- [Ortak g/ç görevleri](common-i-o-tasks.md)\
Dosyalar, dizinler, akışları ve ilgili içerik ile her görevin örneği ile ilişkili g/ç görevlerinin bir listesini sağlar.

- [Zaman uyumsuz dosya g/ç](asynchronous-file-i-o.md)\
Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.

- [Yalıtılmış depolama](isolated-storage.md)\
Kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasını tanımlar.

- [Kanallara](pipe-operations.md)\
.NET Framework içindeki anonim ve adlandırılmış yöneltme işlemlerini açıklar.

- [Bellekle eşlenen dosyalar](memory-mapped-files.md)\
Sanal bellek içindeki disk üzerinde bulunan dosyaların içeriğini içeren bellek eşlemeli dosyaları açıklar. Büyük dosyaları düzenlemek ve işlemler arası iletişim için olan paylaşılan belleği oluşturmak için bellek eşlemeli dosyaları kullanabilirsiniz.
