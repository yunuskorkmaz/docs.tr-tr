---
title: .NET Core için bağlantı kitaplıkları
description: Kitaplık .NET Framework projelerinden .NET Core için bağlantı noktası hakkında bilgi edinin.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 8709c4942bcd1b0fc7f0e75ee41e5c9a01df83ee
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745566"
---
# <a name="port-net-framework-libraries-to-net-core"></a>.NET Framework kitaplıkları .NET Core için bağlantı noktası

Platformlar arası çalıştırmak ve daha geniş kitlelere ulaşın, onu kullanan uygulamaları için .NET Core, .NET Framework kitaplığı kod bağlantı noktası hakkında bilgi edinin.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede, varsayılır:

- Visual Studio 2017 veya sonraki bir sürümü kullanıyor olabilirsiniz.
  - .NET core, Visual Studio'nun önceki sürümlerinde desteklenmez.
- Anlamak [taşıma işlemi önerilen](index.md).
- Herhangi bir sorun giderilmiştir [üçüncü taraf bağımlılıklarının](third-party-deps.md).

Ayrıca şu konu başlıklarının içeriğini tanıdık olmanız gerekir:

[.NET standard](../../standard/net-standard.md)\
Bu konuda, tüm .NET uygulamalarında kullanılabilir olacak şekilde tasarlanmıştır .NET API'lerinin resmi belirtimi açıklanmaktadır.

[Paketler, meta paketler ve çerçeveler](~/docs/core/packages.md)   
Bu makalede, .NET Core nasıl tanımlar ve paketleri kullanır ve birden çok .NET uygulamalarında çalıştırılan kod nasıl destek paketlerinin açıklanmaktadır.

[Platformlar arası araçlarla kitaplıkları ile geliştirme](~/docs/core/tutorials/libraries.md)   
Bu konuda, platformlar arası CLI araçları ile .NET kitaplıkları yazma açıklanmaktadır.

[Eklemeler *csproj* .NET Core için biçim](~/docs/core/tools/csproj.md)   
Bu makalede proje dosyasına taşımak için bir parçası olarak eklenmiş olan değişiklikler özetlenmektedir *csproj* ve MSBuild.

[.NET Core'a taşıma -, üçüncü taraf bağımlılıklarını çözümleme](~/docs/core/porting/third-party-deps.md)   
Bu konu, taşınabilirlik ve üçüncü taraf bağımlılıklarının üzerinde .NET Core NuGet paket bağımlılık çalıştırmaz ne yapılacağını açıklar.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>.NET Framework kodunuzu .NET Framework 4.7.2 yeniden hedefleme

Kodunuzu .NET Framework'ün 4.7.2 hedefleyen değil, .NET Framework 4.7.2 yeniden hedefle önerilir. Bu, burada bu .NET Standard mevcut API'lere desteklemiyor durumlar için en son API alternatifleri kullanılabilirliğini sağlar.

Her Visual Studio'da projeniz için istediğiniz bağlantı noktası, aşağıdakileri yapın:

1. Sağ tıklatın ve proje **özellikleri**.
1. İçinde **hedef Framework'ü** açılır menüsünde, select **.NET Framework 4.7.2**.
1. Projelerinizi derleyin.

Projelerinizi artık .NET Framework'ü 4.7.2 hedefleyen olduğundan, kod taşımak için .NET Framework'ün bu sürümü, temel olarak kullanın.

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

Planınızın önemli bir değişiklik yapmadan aşağıdakilerle ilgili olabilir, .NET Framework 4.7.2, bu önceki yaklaşımın daha fazla yapılandırılmış bir sürüm değişikliği yapma hedefleyen hala çalışırken kod tabanı. Nasıl, planınızın çalıştırma hakkında gidin, kod temeli üzerinde bağlıdır.

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

>[!div class="step-by-step"]
>[Next](project-structure.md)
