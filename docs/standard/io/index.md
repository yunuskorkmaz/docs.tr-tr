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
ms.openlocfilehash: 6bd0187f831db7fd68272e14c022efb45c8260f2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070831"
---
# <a name="file-and-stream-io"></a>Dosya ve Akış G/Ç
Dosya ve akış I/O (giriş/çıkış) bir veri aktarımının depolama ortamına mı gittiğini yoksa oradan mı geldiğini belirtir. .NET Framework'teki `System.IO` ad alanlarında, okuma ve yazma, zaman uyumlu ve zaman uyumsuz olarak veri akışları ve dosyalar üzerinde sağlayan türler bulunur. Bu ad alanları aynı zamanda dosyaları sıkıştırma ve sıkıştırmayı açma işini gerçekleştiren türleri ve borular ve seri bağlantı noktaları üzerinden iletişim sağlayan türleri içerir.  
  
 Bir dosya kalıcı depolaması olan bir sipariş edilen ve adlandırılmış bayt toplamıdır. Bu dosyalarla çalışırken dizin yolları, disk depolama ve dosya ve dizin adları ile çalışırsınız. Buna karşılık akış birkaç depolama ortamından biri olan (örneğin disk veya bellek) yedekleme deposuna yazma ve yedekleme deposundan okuma için kullanılan bir sıra bayttır. Disklerden başka sadece birkaç yedekleme deposu olduğu gibi ağ, bellek ve boru akışları gibi dosya akışlarından farklı olan birkaç tür akış vardır.  
  
## <a name="files-and-directories"></a>Dosyalar ve Dizinler  
 İçindeki türleri kullanabilirsiniz <xref:System.IO?displayProperty=nameWithType> dosyalar ve dizinler ile etkileşim kurmak için ad alanı. Örneğin, dosyalar ve dizinler için özellikleri alabilir ve ayarlayabilirsiniz. Ayrıca arama ölçütlerine dayanarak bir dizi dosya ve dizini alabilirsiniz.  

Yolu için adlandırma kuralları ve .NET Core 1.1 ve üstünde desteklenir DOS aygıtı söz dizimi ve .NET Framework 4.6.2 dahil olmak üzere ve üzeri, Windows sistemleri için bir dosya yolu express yollarını görmek [Windowssistemlerdedosyayolubiçimleri](file-path-formats.md). 
  
 Yaygın olarak kullanılan bazı dosya ve dizin sınıfları şunlardır:  
  
-   <xref:System.IO.File> -oluşturma, kopyalama, silme, taşıma ve dosya açma için statik yöntemler sağlar ve oluşturmaya yardımcı olan bir <xref:System.IO.FileStream> nesne.  
  
-   <xref:System.IO.FileInfo> -oluşturma, kopyalama, silme, taşıma ve dosya açma için örnek yöntemler sağlar ve oluşturmaya yardımcı olan bir <xref:System.IO.FileStream> nesne.  
  
-   <xref:System.IO.Directory> -oluşturma, taşıma ve dizinler ile alt dizinleri numaralandırma için statik yöntemler sağlar.  
  
-   <xref:System.IO.DirectoryInfo> -oluşturma, taşıma ve dizinler ile alt dizinleri numaralandırma için örnek yöntemleri sağlar.  
  
-   <xref:System.IO.Path> -bir platformlar arası şekilde dizin dizeleri işlemek için yöntemler ve özellikler sağlar.  
  
 Her zaman, sağlam özel durum dosya sistemi yöntemleri çağrılırken işleme sağlamalıdır. Daha fazla bilgi için [g/ç işleme hataları](handling-io-errors.md).
 
 Bu sınıfları kullanmaya ek olarak, Visual Basic kullanıcıları tarafından sağlanan özellikler ve yöntemler kullanabilirsiniz <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> dosya g/ç için sınıf.  
  
 Bkz: [nasıl yapılır: dizinleri kopyalama](../../../docs/standard/io/how-to-copy-directories.md), [nasıl yapılır: Create a Directory Listing](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), ve [nasıl yapılır: dizinleri ve dosyaları numaralandırma](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Akışlar  
 Soyut temel sınıf <xref:System.IO.Stream> Bay okuma ve yazmayı destekler. Akışları temsil eden tüm sınıfların devralınacak <xref:System.IO.Stream> sınıfı. <xref:System.IO.Stream> Sınıfı türetilmiş sınıfları veri kaynakları ve genel bir görünümünü sağlar ve Programcı işletim sistemi ve temel alınan cihazların belirli ayrıntılarından ayırmak.  
  
 Akışlar üç temel işlemi içerir:  
  
-   Okuma - bir bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma.  
  
-   Yazma - veri kaynağından bir akışa veri aktarma.  
  
-   Arama - geçerli konumu bir akış içinde sorgulama ve değiştirme.  
  
 Veri kaynağına veya havuza bağlı olarak, bir akış yalnızca bu yeteneklerin bazılarını destekleyebilir. Örneğin, <xref:System.IO.Pipes.PipeStream> sınıfı aramayı desteklemez. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, Ve <xref:System.IO.Stream.CanSeek%2A> özellikleri akış desteklediği işlemleri belirtin.  
  
 Bazı yaygın olarak kullanılan akış sınıfları şunlardır:  
  
-   <xref:System.IO.FileStream> – dosyaya yazma ve okuma için.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – Yalıtılmış depolamadaki dosyaya yazma ve okuma için.  
  
-   <xref:System.IO.MemoryStream> – belleğe yedekleme deposu gibi yazma ve okuma için.  
  
-   <xref:System.IO.BufferedStream> – Okuma performansını artırmak için ve yazma işlemleri.  
  
-   <xref:System.Net.Sockets.NetworkStream> – Ağ yuvaları üzerinde yazma ve okuma için.  
  
-   <xref:System.IO.Pipes.PipeStream> – Anonim ve Adlandırılmış Kanallar üzerinden yazma ve okuma için.  
  
-   <xref:System.Security.Cryptography.CryptoStream> – veri akışlarını şifreleme dönüştürmelerine bağlama için.  
  
 Zaman uyumsuz akışlarla çalışma örneği için bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Okuyucular ve Yazıcılar  
 <xref:System.IO?displayProperty=nameWithType> Ad alanı için türler de sağlar karakterleri akışları ve onları akışlara yazmak. Genellikle, akışlar giriş ve çıkış baytı için tasarlanmıştır. Okuyucu ve yazıcı türleri kodlanmış karakterlerin baytlardan ve baytlara dönüşümünü işler ve böylece akış işlemi tamamlar. Her okuyucu ve yazıcı sınıf sınıfın alınabilmesi için bir akış ile ilişkilidir `BaseStream` özelliği.  
  
 Bazı yaygın olarak kullanılan okuyucu ve yazıcı sınıfları şunlardır:  
  
-   <xref:System.IO.BinaryReader> ve <xref:System.IO.BinaryWriter> – temel veri türlerini ikili değerler olarak yazma ve okuma için.  
  
-   <xref:System.IO.StreamReader> ve <xref:System.IO.StreamWriter> – karakterleri karakter dönüştürmek için bir kodlanmış değeri kullanarak yazma ve okuma baytlardan için.  
  
-   <xref:System.IO.StringReader> ve <xref:System.IO.StringWriter> – karakteri dizelere yazma ve okuma dizelerden için.  
  
-   <xref:System.IO.TextReader> ve <xref:System.IO.TextWriter> – diğer okuyucuların ve karakterleri ve dizeleri, ancak ikili verileri okuyup yazıcılar için soyut temel sınıf olarak hizmet eder.  
  
 Bkz [nasıl yapılır: dosyadan metin okuma](../../../docs/standard/io/how-to-read-text-from-a-file.md), [nasıl yapılır: bir dosyaya metin yazma](../../../docs/standard/io/how-to-write-text-to-a-file.md), [nasıl yapılır: dizeden karakterleri okuma](../../../docs/standard/io/how-to-read-characters-from-a-string.md), ve [nasıl yapılır:dizeyekarakteryazma](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Zaman Uyumsuz G/Ç İşlemleri  
 Büyük miktarda veriyi okumak veya yazmak kaynak yoğunluğu olabilir. Eğer uygulamanız kullanıcıya hassas kalması gerekiyorsa bu işlemleri zaman uyumsuz gerçekleştirebilirsiniz. Zaman uyumlu G/Ç işlemleri ile UI iş parçacığı kaynak yoğunluğu işlemi bitene kadar durdurulur.  Geliştirirken zaman uyumsuz g/ç işlemleri kullanın [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamanızı çalışmayı durdurdu durdurduğu etkiyi oluşturmayı engellemek için uygulamalar.  
  
 Zaman uyumsuz üyeler `Async` adlarında gibi <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, ve <xref:System.IO.Stream.WriteAsync%2A> yöntemleri. Bu yöntemlerle kullandığınız `async` ve `await` anahtar sözcükleri.  
  
 Daha fazla bilgi için [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Sıkıştırma  
 Sıkıştırma depolama için bir dosyanın boyutunu küçültme işlemini gösterir. Açma sıkıştırılmış bir dosyanın içeriğini ayıklanması işlemidir ve böylece kullanılabilir bir formata girerler. <xref:System.IO.Compression?displayProperty=nameWithType> Ad alanı, sıkıştırma ve açma dosyalar ve akışlar için türler içerir.  
  
 Aşağıdaki sınıflar, dosya ve akışları sıkıştırma ve açma işlemi olurken sıkça kullanılır.  
  
-   <xref:System.IO.Compression.ZipArchive> – oluşturma ve zip arşivindeki girdileri alınıyor.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> – sıkıştırılmış bir dosyayı temsil etmek için.  
  
-   <xref:System.IO.Compression.ZipFile> – oluşturmak, ayıklamak ve bir sıkıştırılmış paket açma.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> – oluşturmak ve sıkıştırılmış bir paketteki girişleri ayıklanıyor.  
  
-   <xref:System.IO.Compression.DeflateStream> – sıkıştırma ve Deflate algoritmasını kullanarak akışları sıkıştırma açma için.  
  
-   <xref:System.IO.Compression.GZipStream> – sıkıştırma ve açma akışları gzip veri biçiminde veri için.  
  
 Bkz: [nasıl yapılır: dosya sıkıştırma ve çıkarma](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Yalıtılmış Depolama  
 Yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Depolama kullanıcı, derleme ve etki alanı (isteğe bağlı) tarafından izole edilmiş bir sanal bir dosya sistemi sağlar. Yalıtılmış depolama özellikle uygulamanızın kullanıcı dosyalarına erişim izni yokken yararlıdır. Uygulamanız bilgisayarın güvenlik ilkesi tarafından kontrol edilir bir şekilde ayarlar veya dosyaları kaydedebilirsiniz.  
  
 Yalıtılmış depolama için uygun değildir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları; bunun yerine, uygulama verisi sınıflarını kullanın [Windows.Storage](/uwp/api/Windows.Storage) ad alanı. Daha fazla bilgi için [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) Windows geliştirme Merkezi'nde.  
  
 Aşağıdaki sınıflar yalıtılmış depolama uygularken sık kullanılır:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> – yalıtılmış depolama uygulamaları için taban sınıfı sağlar.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – Dosya ve dizinleri içeren bir yalıtılmış depolama alanı sağlar.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> -Yalıtılmış Depolama içinde bir dosyayı kullanıma sunar.  
  
 Bkz: [yalıtılmış depolama](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Windows Mağazası uygulamalarında G/Ç İşlemleri  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] ; Akışlara yazmak ve akıştan okumak için birçok tür içerir ancak bu, tüm .NET Framework g/ç türlerini içermez.  
  
 G/ç işlemlerini kullanırken dikkat edilecek bazı önemli farklar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar:  
  
-   Özellikle alakalı türler dosya işlemleri gibi <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> ve <xref:System.IO.DirectoryInfo>, dahil edilmeyen [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Bunun yerine, içindeki türleri kullanın [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) ad [!INCLUDE[wrt](../../../includes/wrt-md.md)], gibi [StorageFile](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) ve [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Yalıtılmış Depolama kullanılamaz; Bunun yerine, [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Zaman uyumsuz yöntemleri kullanın <xref:System.IO.Stream.ReadAsync%2A> ve <xref:System.IO.Stream.WriteAsync%2A>UI iş parçacığı engellenmesini önlemek için.  
  
-   Yol tabanlı sıkıştırma türleri <xref:System.IO.Compression.ZipFile> ve <xref:System.IO.Compression.ZipFileExtensions> kullanılabilir değil. Bunun yerine, içindeki türleri kullanın [Windows.Storage.Compression](https://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) ad alanı.  
  
 Gerekirse, .NET Framework akışları ve Windows çalışma zamanı akışları arasında dönüşüm yapabilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework akışları arasında dönüştürme ve Windows çalışma zamanı akışları](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) veya [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 G/ç işlemleri hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması, bakın [hızlı başlangıç: dosya okuma ve yazma](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>G/Ç ve Güvenlik  
 İçindeki sınıfları kullanırken <xref:System.IO?displayProperty=nameWithType> ad alanı, dosyalara ve dizinlere erişimi denetlemek için erişim denetim listeleri (ACL'ler) gibi işletim sistemi güvenlik gereksinimlerine uymalıdır. Bu gereksinim <xref:System.Security.Permissions.FileIOPermission> gereksinimleri. ACL'leri program aracılığıyla yönetebilirsiniz. Daha fazla bilgi için [nasıl yapılır: erişim denetimi listesi girdileri ekleyip](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Varsayılan güvenlik ilkeleri, internet veya intranet uygulamalarının kullanıcının bilgisayarındaki dosyalara erişmesini engeller. Bu nedenle, internet veya intranet üzerinden indirilecek kodu yazarken fiziksel bir dosyaya olan yolu gerektirecek g/ç sınıflarını kullanmayın. Bunun yerine, [yalıtılmış depolama](../../../docs/standard/io/isolated-storage.md) geleneksel .NET Framework uygulamaları veya kullanım için [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
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
