---
title: Dosya ve Akış G/Ç
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
ms.openlocfilehash: 40eeeab159bdef9fc286374fde8c1c1d3a9f5c2b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105660"
---
# <a name="file-and-stream-io"></a>Dosya ve Akış G/Ç
Dosya ve akış I/O (giriş/çıkış) bir veri aktarımının depolama ortamına mı gittiğini yoksa oradan mı geldiğini belirtir. .NET Framework'teki `System.IO` ad alanları veri akışlarını ve dosyaları okuma ve yazma, zaman uyumlu ve zaman uyumsuz olarak etkinleştirin türleri içerir. Bu ad alanları aynı zamanda dosyaları sıkıştırma ve sıkıştırmayı açma işini gerçekleştiren türleri ve borular ve seri bağlantı noktaları üzerinden iletişim sağlayan türleri içerir.  
  
 Bir dosya kalıcı depolaması olan bir sipariş edilen ve adlandırılmış bayt toplamıdır. Bu dosyalarla çalışırken dizin yolları, disk depolama ve dosya ve dizin adları ile çalışırsınız. Buna karşılık akış birkaç depolama ortamından biri olan (örneğin disk veya bellek) yedekleme deposuna yazma ve yedekleme deposundan okuma için kullanılan bir sıra bayttır. Disklerden başka sadece birkaç yedekleme deposu olduğu gibi ağ, bellek ve boru akışları gibi dosya akışlarından farklı olan birkaç tür akış vardır.  
  
## <a name="files-and-directories"></a>Dosyalar ve Dizinler  
 Türler kullanabilirsiniz <xref:System.IO?displayProperty=nameWithType> dosyaları ve dizinleri ile etkileşim kurmak için ad alanı. Örneğin, dosyalar ve dizinler için özellikleri alabilir ve ayarlayabilirsiniz. Ayrıca arama ölçütlerine dayanarak bir dizi dosya ve dizini alabilirsiniz.  

Yol için bkz: adlandırma kuralları ve desteklenen .NET Core 1.1 ve daha sonra DOS aygıtı sözdizimi ve .NET Framework 4.6.2 dahil olmak üzere ve daha sonra Windows sistemleri için bir dosya yolu express yolları [dosya yolu biçimleriWindowssistemlerinde](file-path-formats.md). 
  
 Yaygın olarak kullanılan bazı dosya ve dizin sınıfları şunlardır:  
  
-   <xref:System.IO.File> -oluşturma, kopyalama, silme, taşıma ve dosyaları açma için statik yöntemler sağlar ve oluşturmaya yardımcı olan bir <xref:System.IO.FileStream> nesnesi.  
  
-   <xref:System.IO.FileInfo> -oluşturma, kopyalama, silme, taşıma ve dosyaları açma için örnek yöntemleri sağlar ve oluşturmaya yardımcı olan bir <xref:System.IO.FileStream> nesnesi.  
  
-   <xref:System.IO.Directory> -oluşturma, taşıma ve dizin ve alt dizinlere numaralandırma için statik yöntemler sağlar.  
  
-   <xref:System.IO.DirectoryInfo> -oluşturma, taşıma ve dizin ve alt dizinlere numaralandırma için örnek yöntemleri sağlar.  
  
-   <xref:System.IO.Path> -Dizin dizeleri bir platformlar arası şekilde işlemek için yöntemleri ve özellikleri sağlar.  
  
 Bu sınıfların kullanarak ek olarak, Visual Basic kullanıcılar tarafından sağlanan özellikleri ve yöntemleri kullanabilir <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> dosya g/ç için sınıf.  
  
 Bkz: [nasıl yapılır: dizinleri kopyalama](../../../docs/standard/io/how-to-copy-directories.md), [nasıl yapılır: bir dizin listesi oluşturma](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), ve [nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Akışlar  
 Özet temel sınıf <xref:System.IO.Stream> bayt okuma ve yazma destekler. Akışlar temsil eden tüm sınıflar devralınmalıdır <xref:System.IO.Stream> sınıfı. <xref:System.IO.Stream> Sınıfı ve türetilmiş sınıflarının veri kaynakları ve depoları ortak bir görünümünü sağlar ve işletim sistemi ve arka plandaki cihazların belirli ayrıntıları Programcı yalıtır.  
  
 Akışlar üç temel işlemi içerir:  
  
-   Okuma - bir bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma.  
  
-   Yazma - veri kaynağından bir akışa veri aktarma.  
  
-   Arama - geçerli konumu bir akış içinde sorgulama ve değiştirme.  
  
 Veri kaynağına veya havuza bağlı olarak, bir akış yalnızca bu yeteneklerin bazılarını destekleyebilir. Örneğin, <xref:System.IO.Pipes.PipeStream> sınıfı aramayı desteklemiyor. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, Ve <xref:System.IO.Stream.CanSeek%2A> bir akış özelliklerini akış destekleyen işlemleri belirtin.  
  
 Bazı yaygın olarak kullanılan akış sınıfları şunlardır:  
  
-   <xref:System.IO.FileStream> – Okuma ve bir dosyaya yazmak için.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – Okuma ve yalıtılmış depolama dosyasında yazma.  
  
-   <xref:System.IO.MemoryStream> – Okuma ve bellek yedekleme deposu olarak yazma.  
  
-   <xref:System.IO.BufferedStream> – okuma performansı artırmak için ve yazma işlemleri.  
  
-   <xref:System.Net.Sockets.NetworkStream> – Okuma ve yazma ağ yuva için.  
  
-   <xref:System.IO.Pipes.PipeStream> – Okuma ve yazma adsız ve Adlandırılmış Kanallar üzerinden için.  
  
-   <xref:System.Security.Cryptography.CryptoStream> – veri akışları için şifreleme dönüştürmeleri bağlama.  
  
 Akışlarla zaman uyumsuz olarak çalışan bir örnek için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Okuyucular ve Yazıcılar  
 <xref:System.IO?displayProperty=nameWithType> Ad alanı da sağlayan türleri kodlanmış okuma karakterlerinden akışlar ve akışlara yazma. Genellikle, akışlar giriş ve çıkış baytı için tasarlanmıştır. Okuyucu ve yazıcı türleri kodlanmış karakterlerin baytlardan ve baytlara dönüşümünü işler ve böylece akış işlemi tamamlar. Her okuyucu ve yazıcı sınıfı sınıfının alınan bir akışa ilişkilendirildiği `BaseStream` özelliği.  
  
 Bazı yaygın olarak kullanılan okuyucu ve yazıcı sınıfları şunlardır:  
  
-   <xref:System.IO.BinaryReader> ve <xref:System.IO.BinaryWriter> – okuma ve yazma temel veri türleri olarak ikili değerler için.  
  
-   <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> – okuma ve karakterleri dönüştürmek için bir kodlama değerini kullanarak karakterleri yazma bayt sayısı.  
  
-   <xref:System.IO.StringReader> ve <xref:System.IO.StringWriter> – okuma ve yazma için ve karakter dizelerden için.  
  
-   <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> – soyut taban sınıfları diğer okuyucuların ve okuma ve yazma karakterler ve dizeleri ancak ikili olmayan veriler yazarları için hizmet.  
  
 Bkz: [nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md), [nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md), [nasıl yapılır: bir dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md), ve [nasıl yapılır:dizeyekarakteryazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Zaman Uyumsuz G/Ç İşlemleri  
 Büyük miktarda veriyi okumak veya yazmak kaynak yoğunluğu olabilir. Eğer uygulamanız kullanıcıya hassas kalması gerekiyorsa bu işlemleri zaman uyumsuz gerçekleştirebilirsiniz. Zaman uyumlu G/Ç işlemleri ile UI iş parçacığı kaynak yoğunluğu işlemi bitene kadar durdurulur.  Zaman uyumsuz g/ç işlemlerini geliştirirken kullanmak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamanızı çalışmayı durdurdu izlenim oluşturma önlemek için uygulamalar.  
  
 Zaman uyumsuz üyeleri içeren `Async` adlarında, gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> yöntemleri. Bu yöntemlerle kullandığınız `async` ve `await` anahtar sözcükler.  
  
 Daha fazla bilgi için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Sıkıştırma  
 Sıkıştırma depolama için bir dosyanın boyutunu küçültme işlemini gösterir. Açma sıkıştırılmış bir dosyanın içeriğini ayıklanması işlemidir ve böylece kullanılabilir bir formata girerler. <xref:System.IO.Compression?displayProperty=nameWithType> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için türleri içerir.  
  
 Aşağıdaki sınıflar, dosya ve akışları sıkıştırma ve açma işlemi olurken sıkça kullanılır.  
  
-   <xref:System.IO.Compression.ZipArchive> – oluşturma ve zip arşivini girişleri alınıyor.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> – sıkıştırılmış bir dosyayı temsil etmek için.  
  
-   <xref:System.IO.Compression.ZipFile> – oluşturma, ayıklanması ve bir sıkıştırılmış paket açma.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> – oluşturma ve bir sıkıştırılmış paket girişlerinde ayıklanıyor.  
  
-   <xref:System.IO.Compression.DeflateStream> – sıkıştırma ve Deflate algoritmasını kullanarak akışları boyutunda.  
  
-   <xref:System.IO.Compression.GZipStream> – sıkıştırma ve gzip veri biçimi akış boyutunda.  
  
 Bkz: [nasıl yapılır: dosya sıkıştırma ve çıkarma](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Yalıtılmış Depolama  
 Yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Depolama kullanıcı, derleme ve etki alanı (isteğe bağlı) tarafından izole edilmiş bir sanal bir dosya sistemi sağlar. Yalıtılmış depolama özellikle uygulamanızın kullanıcı dosyalarına erişim izni yokken yararlıdır. Uygulamanız bilgisayarın güvenlik ilkesi tarafından kontrol edilir bir şekilde ayarlar veya dosyaları kaydedebilirsiniz.  
  
 Yalıtılmış depolama için kullanılabilir olmadığından [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları; bunun yerine, uygulama veri sınıflarında kullanın [Windows.Storage](/uwp/api/Windows.Storage) ad alanı. Daha fazla bilgi için bkz: [uygulama verilerini](/previous-versions/windows/apps/hh464917(v=win.10)) Windows geliştirme Merkezi'ndeki.  
  
 Aşağıdaki sınıflar yalıtılmış depolama uygularken sık kullanılır:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> – yalıtılmış depolama uygulamaları için temel sınıf sağlar.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – dosyaları ve dizinleri içeren bir yalıtılmış depolama alanı sağlar.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> -Yalıtılmış Depolama dosyasında kullanıma sunar.  
  
 Bkz: [yalıtılmış depolama](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Windows Mağazası uygulamalarında G/Ç İşlemleri  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Türlerinin çoğunu okuma ve yazma akışlara; içerir ancak, bu kümesi tüm .NET Framework g/ç türleri içermiyor.  
  
 G/ç işlemlerinde kullanırken dikkat edilecek bazı önemli farklar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar:  
  
-   Türleri özellikle ilgili dosya işlemleri için gibi <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> ve <xref:System.IO.DirectoryInfo>, dahil edilmez [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Bunun yerine, türler kullanın [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) ad alanı [!INCLUDE[wrt](../../../includes/wrt-md.md)], gibi [StorageFile](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) ve [StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Yalıtılmış Depolama kullanılabilir değil; Bunun yerine, kullanın [uygulama verileri](/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Zaman uyumsuz yöntemleri gibi kullandığınız <xref:System.IO.Stream.ReadAsync%2A> ve <xref:System.IO.Stream.WriteAsync%2A>, kullanıcı Arabirimi iş parçacığı engellenmesini önlemek için.  
  
-   Yol tabanlı sıkıştırma türleri <xref:System.IO.Compression.ZipFile> ve <xref:System.IO.Compression.ZipFileExtensions> kullanılabilir değil. Bunun yerine, türler kullanın [Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) ad alanı.  
  
 Gerekirse, .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüşüm yapabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework akışları arasında dönüştürme ve Windows çalışma zamanı akışları](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) veya [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 G/ç işlemleri hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bkz: [hızlı başlangıç: Okuma ve dosyalara yazma](/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>G/Ç ve Güvenlik  
 Sınıflarda kullandığınızda <xref:System.IO?displayProperty=nameWithType> ad alanı, dosyalar ve dizinler erişimi denetlemek için erişim denetim listelerini (ACL'ler) gibi işletim sistemi güvenlik gereksinimleri izlemelidir. Bu gereksinim yanı sıra olan <xref:System.Security.Permissions.FileIOPermission> gereksinimleri. ACL'leri program aracılığıyla yönetebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: erişim denetimi listesi girdileri ekleyip](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Varsayılan güvenlik ilkeleri, internet veya intranet uygulamalarının kullanıcının bilgisayarındaki dosyalara erişmesini engeller. Bu nedenle, internet veya intranet üzerinden indirilecek kodu yazarken fiziksel bir dosyaya olan yolu gerektirecek g/ç sınıflarını kullanmayın. Bunun yerine, kullanın [yalıtılmış depolama](../../../docs/standard/io/isolated-storage.md) geleneksel .NET Framework uygulamaları veya kullanım için [uygulama verileri](/previous-versions/windows/apps/hh464917(v=win.10)) için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 Güvenlik denetimi yalnızca akış oluşturulduğunda gerçekleştirilir. Bu nedenle, bir akış açmayın ve sonra onu en az güvenilen koda veya uygulama alanına geçirin.  
  
## <a name="related-topics"></a>İlgili Konular  
  
-   [Ortak G/Ç Görevleri](../../../docs/standard/io/common-i-o-tasks.md)  
  
 Dosyalar, dizinler, akışları ve ilgili içerik ile her görevin örneği ile ilişkili g/ç görevlerinin bir listesini sağlar.  
  
-   [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.  
  
-   [Yalıtılmış Depolama](../../../docs/standard/io/isolated-storage.md)  
  
 Kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasını tanımlar.  
  
-   [Kanallar](../../../docs/standard/io/pipe-operations.md)  
  
 .NET Framework içindeki anonim ve adlandırılmış yöneltme işlemlerini açıklar.  
  
-   [Bellek Eşlemeli Dosyalar](../../../docs/standard/io/memory-mapped-files.md)  
  
 Sanal bellek içindeki disk üzerinde bulunan dosyaların içeriğini içeren bellek eşlemeli dosyaları açıklar. Büyük dosyaları düzenlemek ve işlemler arası iletişim için olan paylaşılan belleği oluşturmak için bellek eşlemeli dosyaları kullanabilirsiniz.
