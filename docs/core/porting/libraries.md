---
title: .NET Core - kitaplıkları taşıma
description: Kitaplık .NET Framework projelerinden .NET Core için bağlantı noktası hakkında bilgi edinin.
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.openlocfilehash: eb6b8506d8df218a053242cd0b8d3097fa6d9fd3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199857"
---
# <a name="porting-to-net-core---libraries"></a>.NET Core - kitaplıkları taşıma

Bu makalede, böylece platformlar arası çalışan .NET core'a taşıma kitaplık kodu açıklanmaktadır.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede, varsayılır:

- Visual Studio 2017 veya sonraki bir sürümü kullanıyor olabilirsiniz.
  - .NET core, Visual Studio'nun önceki sürümlerinde desteklenmez.
- Anlamak [taşıma işlemi önerilen](index.md).
- Herhangi bir sorun giderilmiştir [üçüncü taraf bağımlılıklarının](third-party-deps.md).

Ayrıca şu konu başlıklarının içeriğini tanıdık olmanız gerekir:

[.NET standard](~/docs/standard/net-standard.md)   
Bu konuda, tüm .NET uygulamalarında kullanılabilir olacak şekilde tasarlanmıştır .NET API'lerinin resmi belirtimi açıklanmaktadır.

[Paketler, meta paketler ve çerçeveler](~/docs/core/packages.md)   
Bu makalede, .NET Core nasıl tanımlar ve paketleri kullanır ve birden çok .NET uygulamalarında çalıştırılan kod nasıl destek paketlerinin açıklanmaktadır.

[Platformlar arası araçlarla kitaplıkları ile geliştirme](~/docs/core/tutorials/libraries.md)   
Bu konuda, platformlar arası CLI araçları ile .NET kitaplıkları yazma açıklanmaktadır.

[Eklemeler *csproj* .NET Core için biçim](~/docs/core/tools/csproj.md)   
Bu makalede proje dosyasına taşımak için bir parçası olarak eklenmiş olan değişiklikler özetlenmektedir *csproj* ve MSBuild.

[.NET Core'a taşıma -, üçüncü taraf bağımlılıklarını çözümleme](~/docs/core/porting/third-party-deps.md)   
Bu konu, taşınabilirlik ve üçüncü taraf bağımlılıklarının üzerinde .NET Core NuGet paket bağımlılık çalıştırmaz ne yapılacağını açıklar.

## <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET framework teknolojilerini .NET Core üzerinde kullanılamaz

.NET Framework kitaplıkları için çeşitli teknolojilerden, uygulama etki alanları, uzaktan iletişim, kod erişim güvenliği (CAS) ve güvenlik gibi .NET Core ile kullanmak için kullanılamaz. Kitaplıklarınızı bir veya daha fazla teknolojiler kullanıyorsa, aşağıda ana hatlarıyla belirtilen alternatif yaklaşımlar göz önünde bulundurun. Corefx'te takım API uyumluluğu hakkında daha fazla bilgi için tutan bir [davranış değişiklikleri/compat sonu ve kullanım dışı/eski API'ler listesi](https://github.com/dotnet/corefx/wiki/ApiCompat) github'da.

API veya teknoloji yalnızca şu anda uygulanmadı çünkü kasıtlı olarak desteklenmeyen var. kapsıyor değil. Sorunu bildirin [dotnet/corefx'te depo sorunları](https://github.com/dotnet/corefx/issues) github'da belirli API'ler ve teknolojileri için sorulacak. [Sorunları istekleri taşıma](https://github.com/dotnet/corefx/labels/port-to-core) ile işaretlenmiş `port-to-core` etiketi.

### <a name="appdomains"></a>Uygulama etki alanları

Uygulama etki alanları uygulamaları birbirinden yalıtın. Uygulama etki alanları, çalışma zamanı desteği gerektirir ve genellikle oldukça pahalıdır. Bunlar .NET Core uygulanmaz. Gelecekte bu özelliği eklemeyi planlıyoruz yok. Kod bir ayırma işlemi için ayrı işlemler öneririz veya alternatif olarak kapsayıcıları kullanma. Dinamik derlemeler yüklenmesi için yeni öneririz <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfı.

.NET Framework'ten kod geçiş daha kolay hale getirmek için size bazı kullanıma <xref:System.AppDomain> .NET Core API yüzeyini. Bazı API işlevleri normalde (örneğin, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), bazı üyeleri hiçbir şey yapma (örneğin, <xref:System.AppDomain.SetCachePath%2A>), ve bunlardan bazıları throw <xref:System.PlatformNotSupportedException> (örneğin, <xref:System.AppDomain.CreateDomain%2A>). Kullandığınız karşı türlerini işaretleyin [ `System.AppDomain` başvuru kaynağı](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) içinde [dotnet/corefx'te GitHub deposu](https://github.com/dotnet/corefx) uygulanan sürümünüzle eşleşen dalı seçin emin olun.

### <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan iletişim sorunlu bir mimari belirlenmiştir. Bu, artık desteklenmeyen AppDomain arası iletişim için kullanılır. Ayrıca, uzaktan iletişimi sürdürmek pahalı olan çalışma zamanı desteği gerektirir. Bu nedenlerle, .NET Core, .NET uzaktan iletişim desteklenmez ve gelecekte destek eklemeyi planlıyoruz yok.

İşlemler arasında iletişim için işlemler arası iletişim (IPC) mekanizmasını Remoting, alternatif olarak gibi göz önünde bulundurun <xref:System.IO.Pipes> veya <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıfı.

Makine arasında ağ tabanlı bir çözüm alternatif olarak kullanın. Tercihen, HTTP gibi bir düşük ek yük düz metin protokol kullanın. [Kestrel web sunucusu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), ASP.NET Core tarafından kullanılan web sunucusu, burada bir seçenektir. Ayrıca kullanmayı <xref:System.Net.Sockets> ağ tabanlı, makineler arası senaryolar için. Daha fazla seçenek için bkz: [.NET açık kaynak Geliştirici projeler: Mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Çalışma zamanı veya bir yönetilen uygulama veya kitaplık kullanır veya çalışan hangi kaynaklara sınırlamak için framework güvenmektedir, korumalı alana alma, [.NET Framework üzerinde desteklenmiyor](~/docs/framework/misc/code-access-security.md) ve .NET Core, bu nedenle de desteklenmez. Olduğunu çok fazla çalışma zamanı ve .NET Framework durumlarda ayrıcalıkların CA'lar güvenlik sınırı davranılması devam oluştuğu inanıyoruz. Ayrıca, CA uygulaması daha karmaşık hale getirir ve genellikle doğruluk performans şifrelemelerini kullanmak istemediğiniz uygulamalar için.

En az çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanmanız ayrıcalık kümesi.

### <a name="security-transparency"></a>Güvenlik saydamlık

Benzer şekilde CA'ları, güvenlik saydamlık korumalı kod güvenlik kritik kod, bildirim temelli bir şekilde ayrılması verir ancak olan [artık bir güvenlik sınırı olarak desteklenen](~/docs/framework/misc/security-transparent-code.md). Bu özellik tarafından Silverlight yoğun olarak kullanılır. 

En az çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanmanız ayrıcalık kümesi.

## <a name="converting-a-pcl-project"></a>PCL projesine dönüştürme

PCL projesine hedefleri .NET Standard için Visual Studio 2017'de kitaplık yüklenirken ve aşağıdaki adımları gerçekleştirerek dönüştürebilirsiniz:

1. Proje dosyası üzerinde sağ tıklayıp **özellikleri**.
1. Altında **Kitaplığı**seçin **hedef .NET Platform standardını**.

Paketlerinizi NuGet 3.0 destekliyorsa, proje .NET Standard için yeniden hedefler.

Paketlerinizi NuGet 3.0 desteklemiyorsa, geçerli paketlerinizi kaldırma bildiren Visual Studio'dan bir iletişim kutusu alırsınız. Bu uyarıyı alırsanız, aşağıdaki adımları gerçekleştirin:

1. Projeye sağ tıklayın, **NuGet paketlerini Yönet**.
1. Projenin paket not edin.
1. Tek tek paketleri kaldırın.
1. Kaldırma işlemini tamamlamak için Visual Studio'yu yeniden başlatmanız gerekebilir. Bu durumda, bir **yeniden** düğmesi size sunulur **NuGet Paket Yöneticisi** penceresi.
1. Projeyi yüklediğinde, .NET Standard hedefler. Kaldırmak için gerekli paketleri ekleyin.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>.NET Framework 4.6.2, .NET Framework kodunuzu yeniden hedefleme

Kodunuzu .NET Framework 4.6.2 targeting değil, .NET Framework 4.6.2 yeniden hedefle önerilir. Bu, burada bu .NET Standard mevcut API'lere desteklemiyor durumlar için en son API alternatifleri kullanılabilirliğini sağlar.

Her Visual Studio'da projeniz için istediğiniz bağlantı noktası, aşağıdakileri yapın:

1. Projeye sağ tıklayın ve Özellikler'i seçin.
1. İçinde **hedef Framework'ü** açılır menüsünde, select **.NET Framework 4.6.2**.
1. Projelerinizi derleyin.

Projelerinizi artık .NET Framework 4.6.2'yi hedefleyen olduğundan, kod taşımak için .NET Framework'ün bu sürümü, temel olarak kullanın.

## <a name="determining-the-portability-of-your-code"></a>Kodun taşınabilirliğini belirleme

Sonraki adım, API taşınabilirlik Çözümleyicisi çözümleme için taşınabilirlik rapor oluşturmak için (ApiPort) çalıştırmaktır.

Anladığınızdan emin olun [API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) ve .NET Core'u hedefleyen taşınabilirlik raporlar oluşturma. Bu büyük olasılıkla bunu nasıl kişisel beğeni ve gereksinimlerinize göre değişir. Aşağıda birkaç farklı yaklaşım ' dir. Kodunuzu nasıl yapılandırıldığını bağlı olarak bu yaklaşımların adımları karıştırma kendinizi bulabilirsiniz.

### <a name="dealing-primarily-with-the-compiler"></a>Derleyici öncelikle uğraşmanızı

Bu yaklaşım, küçük projeleri veya birçok .NET Framework API'ları kullanmayın projeler için en iyi olabilir. Bu yaklaşım, basit bir işlemdir:

1. İsteğe bağlı olarak, ApiPort projeniz üzerinde çalıştırın. ApiPort çalıştırırsanız, rapor adresine ihtiyacınız olacak konuları hakkında bilgi edinin.
1. Kodunuzun tamamını üzerinden yeni bir .NET Core projesi kopyalayın.
1. Projeyi tam olarak derler kadar taşınabilirlik rapora (oluşturduysanız) başvuru yapılırken derleyici hataları çözün.

Bu yaklaşım yapılandırılmamış olsa da, kod odaklı bir yaklaşım, genellikle sorunları hızlı bir şekilde çözmek için müşteri adayları ve daha küçük projeler veya kitaplıkları için en iyi yaklaşım olabilir. Yalnızca veri modelleri içeren bir proje, bu yaklaşım için ideal bir aday olabilir.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>.NET Framework üzerinde taşınabilirlik sorunlarını giderilmeden sağlama

İşlem süresince derleyen bir kod isterseniz bu yaklaşım, en iyi olabilir. Bu yaklaşım şu şekildedir:

1. ApiPort bir proje üzerinde çalıştırın.
1. Taşınabilir farklı API'lerini kullanarak sorunları giderin.
1. Burada doğrudan bir alternatif kullanmalarını engelledi alanları not alın.
1. Her yeni bir .NET Core projesine üzerinden kopyalanacak hazır başarılara kadar taşıma tüm projeler için önceki adımları yineleyin.
1. Yeni bir .NET Core projesine kodu kopyalayın.
1. Burada, doğrudan bir alternatif yok not ettiğiniz herhangi bir sorun çalışır.

Dikkatli bu yaklaşım yalnızca derleyici hataları çalışma daha fazla yapılandırılmış, ancak yine de oldukça kod odaklıdır ve derleme kodunu her zaman sahip avantajına sahiptir. Başka bir API aracılığıyla ele uygulanamadı belirli çözümlenebileceği şekilde önemli ölçüde farklılık gösterir. Daha kapsamlı bir geliştirme gerektiğini fark edebilirsiniz belirli sonraki yaklaşım ele alınmıştır projeleri planlayın.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Kapsamlı bir saldırı planı geliştirme

Bu yaklaşım burada kodu yeniden yapılandırma ya da tamamen kodunun belirli alanları yeniden yazma .NET Core desteği gerekli olabilir daha büyük ve daha karmaşık projeler için en iyi olabilir. Bu yaklaşım şu şekildedir:

1. ApiPort bir proje üzerinde çalıştırın.
1. Her bir taşınabilir olmayan türü kullanıldığı ve genel taşınabilirlik nasıl etkilediğini anlayın.
   - Bu tür yapısını anlayın. Bunlar sık sayıda küçük ancak kullanılan misiniz? Bunlar sık sayısı büyük ancak kullanılan misiniz? Kullanımları yoğunlaşmıştır veya, tüm kodunuzda dağıldığında?
   - Kod taşınabilir değildir ve böylece ile daha etkili bir şekilde giderebilirsiniz yalıtmak kolay mı?
   - Kodunuzu yeniden düzenleyin gerekiyor mu?
   - Taşınabilir olmayan bu türleri için aynı görevi başarmak alternatif API'leri var? Kullanıyorsanız, örneğin <xref:System.Net.WebClient> sınıfı olabilir kullanabilmek için <xref:System.Net.Http.HttpClient> bunun yerine sınıf.
   - Mongodb'nin olmasa bile bir görevi gerçekleştirmek için kullanılabilecek farklı taşınabilir API'ler var mı? Kullanıyorsanız, örneğin <xref:System.Xml.Schema.XmlSchema> için XML Ayrıştırma ancak XML gerektirmeyen şema bulma kullanabilir <xref:System.Xml.Linq> API'ler ve kendiniz bir API'sinden aksine ayrıştırma uygulayın.
1. Bağlantı noktasına zor olan derlemeler varsa, bunları .NET Framework üzerinde şimdilik bırakarak değer mi? Dikkat etmeniz gerekenler şunlardır:
   - Bazı işlevler, kitaplığınızda çok yoğun olarak .NET Framework veya özel Windows işlevini kullandığından, .NET Core ile uyumsuz olabilir. Kaynak özellikleri bağlantı noktası kullanılabilir olana kadar şimdilik bu işlevselliği geride ve bir .NET Core sürümünün kitaplığınızın geçici olarak daha az özellik ile serbest bırakma etkiliyorsa mi?
   - Bir yeniden düzenleme yardımcı olur musunuz?
1. Kendi kullanılamayan bir .NET Framework API uygulaması yazmak makul mi?
   Kopyalama, değiştirme ve koddan kullanarak düşünebilirsiniz [.NET Framework başvuru kaynağı](https://github.com/Microsoft/referencesource). Başvuru kaynak kodu altında lisanslanmıştır [MIT lisansı](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), kaynağı için kendi kodunuzu temeli olarak kullanmak için önemli özgürlüğüne sahipsiniz. Yalnızca Microsoft kodunuzda düzgün özniteliği emin olun.
1. Bu işlem, farklı projeler için gerektiği şekilde yineleyin.
 
Analiz aşaması, kod temelinizde boyutuna bağlı olarak biraz zaman alabilir. Genellikle bir plan geliştirmek için gereken değişiklikleri ve kapsamı kaydeder kapsamlı olarak anlamak için bu onay aşamasında zaman harcadığı zaman uzun vadede, özellikle karmaşık bir kod temeli varsa.

Planınızın önemli bir değişiklik yapmadan aşağıdakilerle ilgili olabilir, .NET Framework 4.6.2, bu önceki yaklaşımın daha fazla yapılandırılmış bir sürüm değişikliği yapma hedefleyen hala çalışırken kod tabanı. Nasıl, planınızın çalıştırma hakkında gidin, kod temeli üzerinde bağlıdır.

### <a name="mixing-approaches"></a>Yaklaşım karıştırma

Proje başına temelinde yukarıdaki yaklaşımları karıştırmak olasıdır. Ne de ve kod temeliniz için anlamlı yapmanız gerekir.

## <a name="porting-your-tests"></a>Testlerinizi taşıma

.NET Core için bağlantı noktası olarak kodunuzu test etmek için kodunuzu unity'nin zaman her şeyin çalıştığından emin olmak için en iyi yolu var. Bunu yapmak için derlemeler ve testler için .NET Core çalıştıran bir test çerçevesi kullanmak gerekir. Şu anda üç seçeneğiniz vardır:

- [xUnit](https://xunit.github.io/)
  * [Başlarken](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [MSTest projesi için xUnit dönüştürmek için aracı](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Başlarken](https://github.com/nunit/docs/wiki/Installation)
  * [NUnit için mstest'i geçirme hakkında Blog Gönderisi](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Taşıma için önerilen yaklaşım

Sonuç olarak, taşıma çaba yoğun olarak .NET Framework kodunuzu nasıl yapılandırıldığına bağlıdır. Kodunuzu bağlantı noktası için iyi bir başlangıç yoludur *temel* kodunuzun temel bileşenleri kitaplığınızın. Bu, veri modelleri veya bazı diğer temel sınıflar ve diğer her şey doğrudan veya dolaylı olarak kullanan yöntemleri olabilir.

1. Bağlantı noktası şu anda taşıma kitaplığınızın katman testleri test projesi.
1. Kitaplığınızı tabanı yeni bir .NET Core projesine kopyalayın ve .NET standart, desteklemek istediğiniz sürümü seçin.
1. Derleme kodu almak için gerekli değişiklikleri yapın. Bu çoğunu eklemek için NuGet Paket bağımlılıklarını gerektirebilir, *csproj* dosya.
1. Testleri çalıştırmak ve gerekli ayarlamaları yapın.
1. Sonraki katmanı kod bağlantı noktası, çekme ve önceki adımları yineleyin.

Kitaplığınızın temel ile başlayın ve temel dışa taşıma ve her katman gerektiği gibi test, bağlantı noktası oluşturma sorunları aynı anda bir kod katmanı için yalıtılmış olduğu sistematik bir işlem olur.
