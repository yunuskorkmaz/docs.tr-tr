---
title: .NET Core - kitaplıkları taşıma
description: .NET Framework kitaplığı projelerden .NET Core için bağlantı noktası öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ca71ed4b2423846db4b2c2fc0ba87c49330b7d14
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="porting-to-net-core---libraries"></a>.NET Core - kitaplıkları taşıma

Platformlar arası çalışır .NET Core taşıma kitaplığı kodu anlatılmaktadır.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede varsayar:

- Visual Studio 2017 veya sonraki sürümünü kullanıyorsunuz.
  - .NET core Visual Studio'nun önceki sürümleri desteklenmiyor
- Anlamak [işlem taşıma önerilen](index.md).
- İle ilgili tüm sorunları çözdükten [üçüncü taraf bağımlılıkları](third-party-deps.md).

Ayrıca aşağıdaki konulara içerikle tanıdık olmanız gerekir:

[.NET standart](~/docs/standard/net-standard.md)   
Bu konuda, tüm .NET uygulamalarında kullanılabilir olacak şekilde tasarlanmıştır .NET API'lerini biçimsel belirtimini açıklanmaktadır.

[Paketler, Metapackages ve çerçeveleri](~/docs/core/packages.md)   
Bu makalede nasıl .NET Core tanımlar ve paketleri kullanır ve birden çok .NET uygulamalarında çalışan kodu nasıl destek paketlerinin açıklanır.

[Kitaplıklarla platformu araçları arası geliştirme](~/docs/core/tutorials/libraries.md)   
Bu konu için platformlar arası CLI araçlarını kullanarak .NET kitaplıkları yazma açıklanmaktadır.

[Eklemeler *csproj* .NET Core biçimi](~/docs/core/tools/csproj.md)   
Bu makalede taşımak için bir parçası olarak proje dosyasına eklenen değişiklikler özetlenmektedir *csproj* ve MSBuild.

[.NET Core taşıma -, üçüncü taraf taraf bağımlılıkları analiz etme](~/docs/core/porting/third-party-deps.md)   
Bu konuda taşınabilirlik üçüncü taraf bağımlılıkları ve .NET Core NuGet paket bağımlılığı çalıştırmaz ne yapacakları açıklanmaktadır.

## <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET framework teknolojileri .NET Core üzerinde kullanılamaz

.NET Framework kitaplıkları için birkaç teknolojilerden appdomains oluşturuyor, Remoting, kod erişim güvenliği (CAS) ve güvenlik saydamlık gibi .NET Core ile kullanmak için kullanılamaz. Kitaplıklarınızı bir veya daha fazla bu teknolojiler kullanıyorsa, aşağıda açıklanan alternatif yaklaşımlar göz önünde bulundurun. API uyumluluğu hakkında daha fazla bilgi için CoreFX takım tutar bir [davranış değişiklikleri/compat sonları ve kullanım dışı/eski API listesi](https://github.com/dotnet/corefx/wiki/ApiCompat) github'da.

Yalnızca bir API veya teknoloji şu anda uygulanan değil çünkü bilerek desteklenmeyen sahip kapsıyor değil. Bir sorunun dosya [dotnet/corefx deposu sorunları](https://github.com/dotnet/corefx/issues) belirli API'leri ve teknolojilerin sor github'da. [Sorunları isteklerinde bağlantı noktası oluşturma](https://github.com/dotnet/corefx/labels/port-to-core) işaretlenir `port-to-core` etiketi.

### <a name="appdomains"></a>Uygulama etki alanları

Uygulama etki alanları birbirinden uygulamaları yalıtma. Uygulama etki alanları genellikle oldukça pahalıdır ve çalışma zamanı desteğini gerektirir. Bunlar .NET Core uygulanmadı. Bu yetenek gelecekte ekleme planı yoktur. Kod yalıtımı için ayrı işlemlerdeki öneririz veya alternatif olarak kapsayıcıları kullanma. Derlemeleri dinamik yükleme için yeni öneririz <xref:System.Runtime.Loader.AssemblyLoadContext> sınıfı.

.NET Framework'ten kod geçiş kolaylaştırmak için size bazı kullanıma sunulan <xref:System.AppDomain> .NET Core API yüzeyi. Normalde bazı API işlevleri (örneğin, <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), bazı üyeleri hiçbir şey yapma (örneğin, <xref:System.AppDomain.SetCachePath%2A>), ve bunların bazıları throw <xref:System.PlatformNotSupportedException> (örneğin, <xref:System.AppDomain.CreateDomain%2A>). Kullandığınız karşı türlerini denetleyin [ `System.AppDomain` başvuru kaynağı](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) içinde [dotnet/corefx GitHub deposunu](https://github.com/dotnet/corefx) uygulanan sürümünüzle eşleşen dalı seçin emin olun.

### <a name="remoting"></a>Uzaktan iletişim

.NET uzaktan iletişim sorunlu mimari belirlendi. Artık desteklenmeyen AppDomain arası iletişim için kullanılır. Ayrıca, uzaktan iletişimi korumak pahalıdır çalışma zamanı desteği gerektirir. Bu nedenlerle, .NET uzaktan iletişim .NET Core üzerinde desteklenmiyor ve biz desteği de gelecekte eklemeyi planlayın yok.

İşlemler arasında iletişim için işlemler arası iletişim (IPC) mekanizmaları Remoting, alternatif olarak gibi göz önünde bulundurun <xref:System.IO.Pipes> veya <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> sınıfı.

Makine genelinde ağ tabanlı bir çözüme alternatif olarak kullanın. Tercihen, HTTP gibi bir düşük yükünü düz metin protokolünü kullanır. [Kestrel web sunucusu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), ASP.NET Core tarafından kullanılan web sunucusu burada bir seçenek olabilir. Ayrıca, kullanmayı <xref:System.Net.Sockets> ağ tabanlı, makineler arası senaryolar için. Daha fazla seçenek için bkz: [.NET açık kaynak Geliştirici projeler: Mesajlaşma](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Çalışma zamanı veya bir yönetilen uygulamayı veya kitaplık kullanır veya çalıştıran hangi kaynaklara sınırlamak için framework bağlı, korumalı alan [.NET Framework üzerinde desteklenmiyor](~/docs/framework/misc/code-access-security.md) ve bu nedenle .NET Core üzerinde de desteklenmez. Olduğunu .NET Framework ve çalışma zamanı çok fazla durumlarda ayrıcalıkların CA'lar güvenlik sınırı davranma devam oluştuğu inanıyoruz. Buna ek olarak, CAS uygulama daha karmaşık hale getirir ve genellikle doğruluk performans etkileri kullanmak istemediğiniz uygulamalar için sahiptir.

En az çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanın ayrıcalık kümesi.

### <a name="security-transparency"></a>Güvenlik saydamlık

Benzer CA'lar için güvenlik saydamlık korumalı kod güvenlik kritik kodundan bildirim temelli bir şekilde ayrılmasını sağlar ancak olan [artık bir güvenlik sınırı desteklenen](~/docs/framework/misc/security-transparent-code.md). Bu özellik, Silverlight tarafından yoğun olarak kullanılır. 

En az çalışan işlemleri için sanallaştırma, kapsayıcıları veya kullanıcı hesapları gibi işletim sistemi tarafından sağlanan güvenlik sınırları kullanın ayrıcalık kümesi.

### <a name="globaljson"></a>Global.JSON

*Global.json* bir projenin .NET Core araçları sürümünü ayarlamanıza olanak tanır isteğe bağlı bir dosya bir dosyadır. .NET Core gecelik derlemelerini kullanıyorsanız ve SDK'ın belirli bir sürüm belirtmek istiyorsanız, sürümüyle belirtin bir *global.json* dosya. Genellikle geçerli çalışma dizini veya üst dizinleri birinde yer alıyor. 

```json
{
  "sdk": {
    "version": "2.1.0-preview1-006491"
  }
}
```

## <a name="converting-a-pcl-project"></a>PCL proje dönüştürme

PCL Proje hedefleri .NET standart için Visual Studio 2017 kitaplıkta yükleniyor ve aşağıdaki adımları gerçekleştirerek dönüştürebilirsiniz:

1. Proje dosyasını sağ tıklatın ve seçin **özellikleri**.
1. Altında **Kitaplığı**seçin **hedef .NET Platform standardını**.

Paketlerinizi NuGet 3.0 destekliyorsa, proje .NET standart retargets.

Paketlerinizi NuGet 3.0 desteklemiyorsa, geçerli paketleri kaldırmak için bildiren Visual Studio'dan bir iletişim kutusu alırsınız. Bu uyarıyı almaya devam ederseniz, aşağıdaki adımları gerçekleştirin:

1. Projeye sağ tıklayın, **NuGet paketlerini Yönet**.
1. Projenin paketleri not edin.
1. Tek tek paketleri kaldırın.
1. Kaldırma işlemini tamamlamak için Visual Studio'yu yeniden başlatmanız gerekebilir. Bu durumda, bir **yeniden** düğmesi size sunulur **NuGet Paket Yöneticisi** penceresi.
1. Projeyi yeniden yüklediğinde, .NET standart hedefler. Kaldırmak için gerekli paketleri ekleyin.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>.NET Framework 4.6.2, .NET Framework kodunuzu yeniden hedefleme

.NET Framework 4.6.2, kodunuzu hedefleme değil, .NET Framework 4.6.2 yeniden hedefleyin önerilir. Bu, burada bu .NET standart mevcut API'lerini desteklemiyor durumları için en son API alternatifleri kullanılabilirliğini sağlar.

Her projelerinizi Visual Studio'da istediğiniz bağlantı noktası, aşağıdakileri yapın:

1. Projeye sağ tıklayın ve Özellikler'i seçin.
1. İçinde **hedef Framework** açılan listesinde, select **.NET Framework 4.6.2**.
1. Projelerinizi yeniden derleyin.

Projelerinizi artık hedef .NET Framework 4.6.2 nedeni, .NET Framework sürümünü kodu taşıma için temel olarak kullanın.

## <a name="determining-the-portability-of-your-code"></a>Kodunuzu taşınabilirlik belirleme

Sonraki adım, API taşınabilirlik Çözümleyicisi çözümleme için taşınabilirlik rapor oluşturmak için (ApiPort) çalıştırmaktır.

Anladığınızdan emin olun [API taşınabilirlik Çözümleyicisi (ApiPort)](../../standard/analyzers/portability-analyzer.md) ve .NET Core hedefleme için taşınabilirlik raporlar üretmek nasıl. Bu büyük olasılıkla nasıl yapacağınız gereksinimlerinize ve kişisel zevki göre değişir. Hangi aşağıdaki birkaç farklı yaklaşımlara ' dir. Kendinizi kodunuzu nasıl yapılandırıldığını bağlı olarak Bu yaklaşımlardan adımları karıştırma bulabilirsiniz.

### <a name="dealing-primarily-with-the-compiler"></a>Derleyici öncelikle postalarla

Bu yaklaşım, küçük projeleri veya pek çok .NET Framework API'ları kullanmayın projeleri için en iyi olabilir. Yaklaşım basittir:

1. İsteğe bağlı olarak, ApiPort projeniz üzerinde çalıştırın. ApiPort çalıştırırsanız, bilgi adresine gerekir konularda raporundan kazanır.
1. Tüm kodunuz üzerinde yeni bir .NET Core projeye kopyalayın.
1. Projeyi tam olarak derler kadar taşınabilirlik rapora (oluşturursa) başvuran sırasında derleyici hataları çözün.

Bu yaklaşım yapılandırılmamış olsa da, kod odaklı yaklaşım genellikle hızla sorunlarını çözmek için müşteri adayları ve daha küçük projeleri veya kitaplıkları için en iyi yaklaşımı olabilir. Yalnızca veri modelleri içeren bir projesi bu yaklaşım için ideal bir aday olabilir.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Taşınabilirlik sorunlarını çözümlenene kadar .NET Framework üzerine sağlama

Tüm işlem sırasında derler koda sahip tercih ederseniz, bu yaklaşım en iyi olabilir. Yaklaşım aşağıdaki gibidir:

1. ApiPort bir proje üzerinde çalıştırın.
1. Taşınabilir farklı API'lerini kullanarak sorunları giderin.
1. Burada, doğrudan bir alternatif kullanamıyor alanları not edin.
1. Her yeni bir .NET Core projeye üzerinden kopyalanacak hazır emin kadar taşıma tüm projeleri için önceki adımları yineleyin.
1. Kod yeni bir .NET Core projeye kopyalayın.
1. Burada, doğrudan bir alternatif yok not ettiğiniz herhangi bir sorunla çalışır.

Dikkatli bu yaklaşım derleyici hataları yalnızca çalışma daha fazla yapılandırılmış, ancak hala görece kod odaklı ve her zaman derler koduna sahip avantajına sahiptir. Yalnızca başka bir API kullanarak ele uygulanamadı belirli sorunları gidermek şekilde önemli ölçüde farklılık gösterir. Daha fazla kapsamlı bir geliştirmek gerektiğini fark edebilirsiniz belirli projeler, sonraki yaklaşımı ele alınmıştır planlayın.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Saldırı kapsamlı bir planı geliştirme

Bu yaklaşım burada kod yeniden yapılandırma ya da tamamen kodunun belirli alanları yeniden yazma işlemi .NET Core desteklemek gerekli olabilir daha büyük ve daha karmaşık projeler için en iyi olabilir. Yaklaşım aşağıdaki gibidir:

1. ApiPort bir proje üzerinde çalıştırın.
1. Her taşınabilir olmayan türü kullanıldığı ve, genel taşınabilirlik nasıl etkilediğini anlayın.
   - Bu türlerde yapısını anlayın. Bunlar sıklıkla numarasında küçük ancak kullanılan misiniz? Bunlar seyrek numarasında büyük ancak kullanılan misiniz? Kullanımlarını yoğunlaşmıştır ya da, tüm kodunuzda yayılır?
   - Taşınabilir değil ve böylece ile daha etkili bir şekilde gerçekleştirememektedir kod ayırmak kolay mi?
   - Kodunuzu yeniden düzenlemeniz gerekiyor mu?
   - Taşınabilir olmayan bu türlerde aynı görevi alternatif API'leri var mı? Kullanıyorsanız, örneğin <xref:System.Net.WebClient> sınıfı, olabilir kullanabilmek için <xref:System.Net.Http.HttpClient> yerine sınıfı.
   - İçeri Kayma değiştirme olmasa bile bir görevi gerçekleştirmek kullanılabilen farklı taşınabilir API'leri vardır? Kullanıyorsanız, örneğin <xref:System.Xml.Schema.XmlSchema> için XML Ayrıştırma ancak XML gerektirmeyen şema bulma kullanabilir <xref:System.Xml.Linq> API'ları ve kendiniz bir API üzerine bağlı olan aksine ayrıştırma uygulayın.
1. Bağlantı noktasına zordur derlemeleri varsa, bunları .NET Framework üzerinde şu an için bırakırlar değerinde mi? Dikkate alınması gereken bazı noktalar şunlardır:
   - Kitaplığınızdaki çok yoğun olarak .NET Framework veya Windows'a özgü işlevini kullandığından, .NET Core ile uyumlu olmayan bazı işlevler olabilir. Kaynak bağlantı noktası özellikleri kullanılabilir olana kadar şimdilik bu işlevselliği kalmasını ve .NET Core sürüm kitaplığınızın geçici olarak atanabildiği daha az özellik ile serbest bırakma değer nedir?
   - Bir düzenleme yardımcı?
1. Kullanılamayan bir .NET Framework API'yi kendi uygulama yazmak makul mi?
   Kopyalama, değiştirme ve koddan kullanarak düşünebilirsiniz [.NET Framework başvuru kaynağı](https://github.com/Microsoft/referencesource). Başvuru kaynak kodu altında lisanslanmıştır [MIT lisansı](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), bu nedenle kaynağı kendi kodunuzu için temel olarak kullanmak için önemli serbestçe. Yalnızca Microsoft kodunuzda düzgün özniteliği emin olun.
1. Bu işlem, farklı projeler için gerektiği kadar yineleyin.
 
Analiz aşaması temelinizde boyutuna bağlı olarak biraz zaman alabilir. Gereken değişiklikleri ve genellikle bir plan geliştirmek için kapsam kaydeder kapsamlı olarak anlamak için bu aşamada zaman harcama saat uzun vadede, özellikle karmaşık codebase varsa.

Planınız önemli bir değişiklik yapmadan ilgili olabilir, .NET Framework 4.6.2, bu önceki yaklaşımın daha fazla yapılandırılmış bir sürüm değişikliği yapma hala hedefleme sırasında codebase. Nasıl planınız çalıştırma hakkında gidin, kod temeli üzerinde bağlıdır.

### <a name="mixing-approaches"></a>Yaklaşımlar karıştırma

Proje başına temelinde yukarıdaki yaklaşımlar karışık olasıdır. Ne en size ve temelinizde için anlamlı yapmanız gerekir.

## <a name="porting-your-tests"></a>Testlerinizi bağlantı noktası oluşturma

Kodunuzu bağlantı noktalı zaman her şeyi çalıştığından emin olmak için en iyi yolu, .NET Core için bağlantı noktası olarak kodunuzu test etmektir. Bunu yapmak için bir sınama Framework'e oluşturur ve .NET Core için testleri çalıştırır kullanmak gerekir. Şu anda, üç seçeneğiniz vardır:

- [xUnit](https://xunit.github.io/)
  * [Başlarken](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Mstest'i projesinde xUnit için dönüştürme aracı](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [Başlarken](https://github.com/nunit/docs/wiki/Installation)
  * [Blog yayını için NUnit mstest'i geçirme hakkında](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [Mstest'i](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Taşıma için önerilen yaklaşım

Sonuç olarak, taşıma çaba yoğun olarak .NET Framework kodunuzu nasıl yapılandırıldığına bağlıdır. Kodunuzu bağlantı noktası için en iyi yolu başından itibaren olan *temel* kodunuzu temel bileşenleridir kitaplığınızın. Bu, veri modelleri veya bazı diğer temel sınıfları ve şey doğrudan veya dolaylı olarak kullanan yöntemleri olabilir.

1. Bağlantı noktası şu anda taşıma kitaplığınızın katman testleri test projesi.
1. Yeni bir .NET Core projeye kitaplığınızın temel kopyalayın ve .NET standart, desteklemek istediğiniz sürümü seçin.
1. Kodu derlemek için erişmek için gerekli tüm değişiklikleri yapın. Bu çoğunu NuGet Paket bağımlılıklarını eklemeyi gerektirebilir, *csproj* dosya.
1. Testleri çalıştırın ve gerekli ayarlamaları yapın.
1. Sonraki katmanı kod bağlantı noktası, çekme ve önceki adımları yineleyin.

Kitaplığınızı tabanıyla başlatmak ve dışa taban taşıyın ve gerektiği gibi her katman test, bağlantı noktası oluşturma sorunları aynı anda kod bir katmana yalıtılmış nerede sistematik, bir işlemdir.
