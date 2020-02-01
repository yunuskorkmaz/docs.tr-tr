---
title: .NET Core 'a bağlantı noktası kitaplıkları
description: .NET Framework kitaplığı projelerinin nasıl .NET Core 'a bağlantı sağladığını öğrenin.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 646587120de2e51280c2af4de36bf3a6b0f60c2d
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920615"
---
# <a name="port-net-framework-libraries-to-net-core"></a>.NET Core 'a bağlantı noktası .NET Framework kitaplıkları

.NET Framework kitaplığı kodunun, platformlar arası çalıştığı ve onu kullanan uygulamaların erişimini genişleten .NET Core 'a bağlantı noktası oluşturma hakkında bilgi edinin.

## <a name="prerequisites"></a>Prerequisites

Bu makalede şunları kabul edersiniz:

- , Visual Studio 2017 veya üstünü kullanıyor. (.NET Core, Visual Studio 'nun önceki sürümlerinde desteklenmez.)
- [Önerilen taşıma sürecini](index.md)anlayın.
- [Üçüncü taraf bağımlılıklarla](third-party-deps.md)ilgili sorunları çözmüştür.

Ayrıca, aşağıdaki makalelerin içeriğini tanımanız gerekir:

[.NET Standard](../../standard/net-standard.md)\
Bu makalede, tüm .NET uygulamalarında kullanılabilmesi amaçlanan .NET API 'lerinin biçimsel belirtimi açıklanmaktadır.

[Paketler, Metapackages ve çerçeveler](../packages.md)\
Bu makalede, .NET Core 'un paketleri nasıl tanımladığı ve kullandığı ve paketlerin birden çok .NET uygulamasında çalışan kodun nasıl desteklediği açıklanır.

[Platformlar arası araçlarla kitaplıklar geliştirme](../tutorials/libraries.md)\
Bu makalede, .NET Core CLI kullanarak kitaplıkların nasıl yazılacağı açıklanır.

[.NET Core\ *csproj* biçimine eklemeler](../tools/csproj.md)
Bu makalede, *csproj* ve MSBuild 'e taşıma kapsamında proje dosyasına eklenen değişiklikler özetlenmektedir.

[.NET Core 'A taşıma-üçüncü taraf taraflarınızın bağımlılıklarını çözümleme](third-party-deps.md)\
Bu makalede, üçüncü taraf bağımlılıkların taşınabilirliği ve bir NuGet paket bağımlılığı .NET Core üzerinde çalıştırılmazsa ne yapmalı anlatılmaktadır.

## <a name="retarget-to-net-framework-472"></a>.NET Framework 4.7.2 için yeniden hedefle

Kodunuz .NET Framework 4.7.2 hedeflenmemişse, .NET Framework 4.7.2 ' ye yeniden hedeflemeniz önerilir. Bu, .NET Standard var olan API 'Leri desteklemediği durumlarda en son API alternatiflerine yönelik kullanılabilirliği sağlar.

Bağlantı noktası atamak istediğiniz her bir proje için, Visual Studio 'da şunları yapın:

1. Projeye sağ tıklayın ve **Özellikler**' i seçin.
1. **Hedef çerçeve** açılan menüsünde **.NET Framework 4.7.2**' ı seçin.
1. Projeyi yeniden derleyin.

Projeleriniz .NET Framework 4.7.2 ' i hedeflemesini sağladığından, kodu taşıma için temel olarak bu .NET Framework sürümünü kullanın.

## <a name="determine-portability"></a>Taşınabilirliği belirleme

Sonraki adım, analiz için bir taşınabilirlik raporu oluşturmak üzere API taşınabilirlik Çözümleyicisi 'ni (ApiPort) çalıştırmak içindir.

[API taşınabilirlik Çözümleyicisi 'ni (ApiPort)](../../standard/analyzers/portability-analyzer.md) ve .NET Core hedeflemek için taşınabilirlik raporları oluşturmayı anladığınızdan emin olun. Bunun nasıl yapılacağı, gereksinimlerinize ve kişisel tastes 'ye göre farklılık gösterir. Aşağıdaki bölümlerde birkaç farklı yaklaşım ayrıntılandırır. Kodunuzun nasıl yapılandırıldığına bağlı olarak bu yaklaşımlardan oluşan adımları kendiniz bulabilirsiniz.

### <a name="deal-primarily-with-the-compiler"></a>Birincil olarak derleyiciye dağıt

Bu yaklaşım, çok sayıda .NET Framework API kullanmayan küçük projeler veya projeler için iyi bir sonuç verir. Yaklaşım basittir:

1. İsteğe bağlı olarak, projenizde ApiPort ' ı çalıştırın. ApiPort çalıştırırsanız, adresetmeniz gereken sorunlar hakkında rapordan bilgi kazanın.
1. Tüm kodunuzu yeni bir .NET Core projesine kopyalayın.
1. Taşınabilirlik raporuna (oluşturulduysa) başvururken, proje tamamen derlenene kadar derleyici hatalarını çözün.

Yapılandırılmamış olsa da, bu kod odaklı yaklaşım genellikle sorunları hızlı bir şekilde çözer. Yalnızca veri modellerini içeren bir proje, bu yaklaşım için ideal bir aday olabilir.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Taşınabilirlik sorunları çözülene kadar .NET Framework kalın

Bu yaklaşım, tüm işlem sırasında derlenen kodu bulundurmayı tercih ediyorsanız en iyi yöntem olabilir. Yaklaşım aşağıdaki gibidir:

1. Bir projede ApiPort çalıştırın.
1. Taşınabilir farklı API 'Ler kullanarak sorunları çözün.
1. Doğrudan alternatif kullanmak zorunda olmadığınız tüm alanlara göz atın.
1. Her biri yeni bir .NET Core projesine kopyalanmak üzere hazırlanana kadar, bağlantı noktası oluşturduğunuz tüm projeler için önceki adımları tekrarlayın.
1. Kodu yeni bir .NET Core projesine kopyalayın.
1. Doğrudan bir alternatif mevcut olmadığını not ettiğiniz tüm sorunları giderin.

Bu dikkatli yaklaşım, derleyici hatalarından yalnızca çalışmaya kıyasla daha fazla yapılandırılmıştır, ancak yine de kod odaklı olduğundan, her zaman derlenen koda sahip olma avantajına sahiptir. Yalnızca başka bir API kullanılarak giderilemedik bazı sorunları çözmenize yönelik Yöntem büyük ölçüde farklılık gösterir. Sonraki yaklaşımda ele alınan belirli projeler için daha kapsamlı bir plan geliştirmeniz gerektiğini fark edebilirsiniz.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Kapsamlı bir saldırı planı geliştirin

Bu yaklaşım, .NET Core 'u desteklemek için kodun yeniden yapılandırılması veya belirli kod alanlarının tamamen yeniden oluşturulması gereken daha büyük ve daha karmaşık projeler için en iyi yöntem olabilir. Yaklaşım aşağıdaki gibidir:

1. Bir projede ApiPort çalıştırın.
1. Her taşınabilir olmayan türün kullanıldığını ve bunun genel taşınabilirliği nasıl etkilediğini anlayın.
   - Bu türlerin yapısını anlayın. Bu sayı çok küçük ancak sık kullanılıyor mu? Bu sayı çok büyük ancak seyrek kullanılıyor mu? Kullanımları üzerinde mi var, ister kodunuzun genelinde yayılıyor?
   - Taşınabilir olmayan kodları daha verimli bir şekilde ilgilenebilmeniz için kolayca yalıtmak ister misiniz?
   - Kodunuzu yeniden düzenlemeniz gerekiyor mu?
   - Taşınabilir olmayan türler için aynı görevi gerçekleştiren alternatif API 'Ler var mı? Örneğin, <xref:System.Net.WebClient> sınıfını kullanıyorsanız, bunun yerine <xref:System.Net.Http.HttpClient> sınıfını kullanabilirsiniz.
   - Bir görevi gerçekleştirmek için kullanılabilecek farklı taşınabilir API 'Ler var, bu da bir iade değişikliği olmasa bile Örneğin, XML ayrıştırmak için <xref:System.Xml.Schema.XmlSchema> kullanıyorsanız ancak XML şema keşfi gerekmiyorsa, API 'ye güvenmek yerine <xref:System.Xml.Linq> API 'Leri kullanabilir ve Ayrıştırma işlemini uygulayabilirsiniz.
1. Bağlantı noktası zorlaştırılması gereken derlemeleriniz varsa .NET Framework şu an için de bu şekilde ayrılsın mı? Göz önünde bulundurmanız gereken bazı noktalar şunlardır:
   - Kitaplığınızda .NET Core ile uyumlu olmayan bazı işlevlere sahip olabilirsiniz çünkü .NET Framework veya Windows 'a özgü işlevselliği çok fazla yoğun bir şekilde kullanır. Bu işlevi şimdilik bırakın ve kaynaklar bağlantı noktası özellikleri için kullanılabilir olana kadar daha az özelliklerle kitaplığınızın geçici bir .NET Core sürümünü serbest bırakın.
   - Yeniden düzenleme yardım ister misiniz?
1. Kullanılamayan .NET Framework API 'niz için kendi uygulamanızı yazmak mantıklı mi?
   [.NET Framework başvuru kaynağından](https://github.com/Microsoft/referencesource)kodu kopyalamayı, değiştirmeyi ve kullanmayı düşünebilirsiniz. Başvuru kaynak kodu, [MIT Lisansı](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)kapsamında lisanslanır, bu nedenle kaynağı kendi kodunuz için temel olarak kullanmak için önemli bir özgürlük vardır. Yalnızca kodunuzda Microsoft 'un düzgün şekilde öznitelediğinizden emin olun.
1. Bu işlemi, farklı projeler için gerektiği şekilde tekrarlayın.
 
Analiz aşaması, kod tabanınızın boyutuna bağlı olarak biraz zaman alabilir. Bu aşamada, gereken değişikliklerin kapsamını ayrıntılı olarak anlamak ve bir plan geliştirmek için zaman harcamanız, özellikle karmaşık bir kod tabanınız varsa, genellikle uzun çalıştırmaya zaman kazandırır.

Planınız, .NET Framework 4.7.2 ' i hedeflerken, bu, önceki yaklaşımın daha yapılandırılmış bir sürümünü yaparak kod tabanınızda önemli değişiklikler yapmayı gerektirebilir. Planınızı yürütme hakkında nasıl gittiğiniz, kod tabanınıza bağımlıdır.

### <a name="mixed-approach"></a>Karışık yaklaşım

Yukarıdaki yaklaşımlardan proje başına temelinde karıştıracaksınız. Sizin ve kod tabanınız için en mantıklı şeyi yapmanız gerekir.

## <a name="port-your-tests"></a>Testlerinizin bağlantı noktası

Kodunuzu yazarken her şeyin çalıştığından emin olmanın en iyi yolu, .NET Core 'a bağlantı noktası oluştururken kodunuzun test sağlamaktır. Bunu yapmak için .NET Core için test oluşturup çalıştıran bir test çerçevesi kullanmanız gerekir. Şu anda üç seçeneğiniz vardır:

- [xUnit](https://xunit.github.io/)
  - [Başlarken](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [MSTest projesini xUnit 'e dönüştüren araç](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Başlarken](https://github.com/nunit/docs/wiki/Installation)
  - [MSTest 'ten NUnit 'e geçiş hakkında blog gönderisi](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- ['I](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Önerilen yaklaşım

Son olarak, taşıma çabası .NET Framework kodunuzun nasıl yapılandırıldığına bağlıdır. Kodunuzun bağlantı noktasının temelini oluşturan, kodunuzun temel bileşenleri olan, kitaplığınızın *temelini* oluşturmaya yönelik iyi bir yoldur. Bu, başka her şeyin doğrudan veya dolaylı olarak kullandığı veri modelleri veya diğer temel sınıflar ve yöntemler olabilir.

1. Şu anda taşıma yaptığınız kitaplığınızın katmanını sınayan test projesi bağlantı noktası.
1. Kitaplığınızın temelini yeni bir .NET Core projesine kopyalayın ve desteklemek istediğiniz .NET Standard sürümünü seçin.
1. Derlenecek kodu almak için gereken değişiklikleri yapın. Bunun büyük bölümü, *csproj* dosyanıza NuGet paketi bağımlılıkları eklenmesini gerektirebilir.
1. Testleri çalıştırın ve gerekli ayarlamaları yapın.
1. Üzerinde bağlantı noktası için sonraki kod katmanını seçin ve önceki adımları tekrarlayın.

Kitaplığınızın temelini başlatıp her bir katmanı gerektiği gibi test ederseniz, taşıma işlemi, sorunların tek seferde bir kod katmanına yalıtılabileceği sistematik bir işlemdir.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[.NET Core için projeleri düzenleme](project-structure.md)
