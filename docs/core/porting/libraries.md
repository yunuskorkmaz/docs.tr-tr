---
title: .NET için bağlantı noktası kitaplıkları
description: .NET Framework kitaplığı projelerinin nasıl .NET 'e bağlantı sağladığını öğrenin.
author: cartermp
ms.date: 03/04/2021
ms.openlocfilehash: 19ee6ab15597b3c99b39b47ad55ac72a3f9d681a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873685"
---
# <a name="port-net-framework-libraries-to-net"></a>.NET için bağlantı noktası .NET Framework kitaplıkları

.NET Framework kitaplığı kodunun, platformlar arası çalıştığı ve onu kullanan uygulamaların erişimini genişleten .NET 'a bağlantı noktası oluşturma hakkında bilgi edinin.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede şunları kabul edersiniz:

- Visual Studio 2019 veya üstünü kullanıyor musunuz?
  - .NET 5, Visual Studio 2019 (v 16.9) veya üstünü gerektirir.
  - .NET Core 3,1, Visual Studio 2019 (v 16.4) veya üstünü gerektirir.
- [Önerilen taşıma sürecini](index.md)anlayın.
- [Üçüncü taraf bağımlılıklarla](third-party-deps.md)ilgili sorunları çözmüştür.

Aşağıdaki makalelerin içeriğiyle ilgili bilgi edinin:

- [.NET Standard.](../../standard/net-standard.md)\
Bu makalede, tüm .NET uygulamalarında kullanılabilmesi amaçlanan .NET API 'lerinin biçimsel belirtimi açıklanmaktadır.

- [.NET CLı ile Kitaplıklar geliştirin.](../tutorials/libraries.md)\
Bu makalede, .NET CLı kullanılarak kitaplıkların nasıl yazılacağı açıklanır.

- [.NET projesi SDK 'Ları.](../project-sdk/overview.md)\
Bu makalede SDK stili proje dosya biçimi açıklanmaktadır.

- [.NET Framework ile .NET arasında bağlantı noktası kodu için bağımlılıklarınızı çözümleyin.](third-party-deps.md)\
Bu makalede, üçüncü taraf bağımlılıkların taşınabilirliği ve bir NuGet paket bağımlılığı .NET üzerinde çalıştırılmazsa ne yapmalı anlatılmaktadır.

## <a name="retarget-to-net-framework-472"></a>.NET Framework 4.7.2 için yeniden hedefle

Kodunuz .NET Framework 4.7.2 hedeflenmemişse, .NET Framework 4.7.2 ' ye yeniden hedeflemeniz önerilir. Bu, .NET Standard var olan API 'Leri desteklemediği durumlarda en son API alternatiflerine yönelik kullanılabilirliği sağlar.

Bağlantı noktası atamak istediğiniz her bir proje için, Visual Studio 'da şunları yapın:

01. Projeye sağ tıklayın ve **Özellikler**' i seçin.
01. **Hedef çerçeve** açılan menüsünde **.NET Framework 4.7.2**' ı seçin.
01. Projeyi yeniden derleyin.

Projeleriniz .NET Framework 4.7.2 ' i hedeflemesini sağladığından, kodu taşıma için temel olarak bu .NET Framework sürümünü kullanın.

## <a name="determine-portability"></a>Taşınabilirliği belirleme

Sonraki adım, analiz için bir taşınabilirlik raporu oluşturmak üzere API taşınabilirlik Çözümleyicisi 'ni (ApiPort) çalıştırmak içindir.

[API taşınabilirlik Çözümleyicisi 'ni (ApiPort)](../../standard/analyzers/portability-analyzer.md) ve .net 'i hedeflemek için taşınabilirlik raporları oluşturmayı anladığınızdan emin olun. Bunun nasıl yapılacağı, gereksinimlerinize ve kişisel tastes 'ye göre farklılık gösterir. Aşağıdaki bölümlerde birkaç farklı yaklaşım ayrıntılandırır. Kodunuzun nasıl yapılandırıldığına bağlı olarak bu yaklaşımlardan oluşan adımları kendiniz bulabilirsiniz.

### <a name="deal-primarily-with-the-compiler"></a>Birincil olarak derleyiciye dağıt

Bu yaklaşım, çok sayıda .NET Framework API kullanmayan küçük projeler veya projeler için iyi bir sonuç verir. Yaklaşım basittir:

01. İsteğe bağlı olarak, projenizde ApiPort ' ı çalıştırın. ApiPort çalıştırırsanız, adresetmeniz gereken sorunlar hakkında rapordan bilgi kazanın.
01. Tüm kodunuzu yeni bir .NET projesine kopyalayın.
01. Taşınabilirlik raporuna (oluşturulduysa) başvururken, proje tamamen derlenene kadar derleyici hatalarını çözün.

Yapılandırılmamış olsa da, bu kod odaklı yaklaşım genellikle sorunları hızlı bir şekilde çözer. Yalnızca veri modellerini içeren bir proje, bu yaklaşım için ideal bir aday olabilir.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Taşınabilirlik sorunları çözülene kadar .NET Framework kalın

Bu yaklaşım, tüm işlem sırasında derlenen kodu bulundurmayı tercih ediyorsanız en iyi yöntem olabilir. Yaklaşım aşağıdaki gibidir:

01. Bir projede ApiPort çalıştırın.
01. Taşınabilir farklı API 'Ler kullanarak sorunları çözün.
01. Doğrudan alternatif kullanmak zorunda olmadığınız tüm alanlara göz atın.
01. Her biri yeni bir .NET projesine kopyalanmak için kullanılabilir olana kadar, bağlantı noktası oluşturduğunuz tüm projeler için önceki adımları tekrarlayın.
01. Kodu yeni bir .NET projesine kopyalayın.
01. Doğrudan bir alternatif mevcut olmadığını not ettiğiniz tüm sorunları giderin.

Bu dikkatli yaklaşım, derleyici hatalarından yalnızca çalışmaya kıyasla daha fazla yapılandırılmıştır, ancak yine de kod odaklı olduğundan, her zaman derlenen koda sahip olma avantajına sahiptir. Yalnızca başka bir API kullanılarak giderilemedik bazı sorunları çözmenize yönelik Yöntem büyük ölçüde farklılık gösterir. Sonraki yaklaşımda ele alınan belirli projeler için daha kapsamlı bir plan geliştirmeniz gerektiğini fark edebilirsiniz.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Kapsamlı bir saldırı planı geliştirin

Bu yaklaşım, .NET 'i desteklemek için kodun yeniden yapılandırılması veya belirli kod alanlarının tamamen yeniden oluşturulması gerektiği daha büyük ve daha karmaşık projeler için en iyi yöntem olabilir. Yaklaşım aşağıdaki gibidir:

01. Bir projede ApiPort çalıştırın.
01. Her taşınabilir olmayan türün kullanıldığını ve bunun genel taşınabilirliği nasıl etkilediğini anlayın.

    - Bu türlerin yapısını anlayın. Bu sayı çok küçük ancak sık kullanılıyor mu? Bu sayı çok büyük ancak seyrek kullanılıyor mu? Kullanımları üzerinde mi var, ister kodunuzun genelinde yayılıyor?
    - Taşınabilir olmayan kodları daha verimli bir şekilde ilgilenebilmeniz için kolayca yalıtmak ister misiniz?
    - Kodunuzu yeniden düzenlemeniz gerekiyor mu?
    - Taşınabilir olmayan türler için aynı görevi gerçekleştiren alternatif API 'Ler var mı? Örneğin, <xref:System.Net.WebClient> sınıfını kullanıyorsanız, <xref:System.Net.Http.HttpClient> bunun yerine sınıfını kullanın.
    - Bir görevi gerçekleştirmek için kullanılabilecek farklı taşınabilir API 'Ler var, bu da bir iade değişikliği olmasa bile Örneğin, <xref:System.Xml.Schema.XmlSchema> XML 'yi ayrıştırmak ancak XML şema keşfi gerekmiyorsa, API <xref:System.Xml.Linq> 'leri kullanabilir ve bir API 'ye güvenmek yerine kendiniz ayrıştırma uygulayabilirsiniz.

01. Bağlantı noktası zorlaştırılması gereken derlemeleriniz varsa .NET Framework şu an için de bu şekilde ayrılsın mı? Göz önünde bulundurmanız gereken bazı noktalar şunlardır:

    - Kitaplığınızda .NET ile uyumlu olmayan bazı işlevlere sahip olabilirsiniz, çünkü .NET Framework veya Windows 'a özgü işlevselliği çok fazla yoğun bir şekilde kullanır. Bu işlevi şimdilik bırakın ve kaynaklar bağlantı noktası özellikleri için kullanılabilir olana kadar daha az özellik ile kitaplığınızın geçici bir .NET sürümünü serbest bırakın.
    - Yeniden düzenleme yardım ister misiniz?

01. Kullanılamayan .NET Framework API 'niz için kendi uygulamanızı yazmak mantıklı mi?

    [.NET Framework başvuru kaynağından](https://github.com/Microsoft/referencesource)kodu kopyalamayı, değiştirmeyi ve kullanmayı düşünebilirsiniz. Başvuru kaynak kodu, [MIT Lisansı](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)kapsamında lisanslanır, bu nedenle kaynağı kendi kodunuz için temel olarak kullanmak için önemli bir özgürlük vardır. Yalnızca kodunuzda Microsoft 'un düzgün şekilde öznitelediğinizden emin olun.

01. Bu işlemi, farklı projeler için gerektiği şekilde tekrarlayın.

Analiz aşaması, kod tabanınızın boyutuna bağlı olarak biraz zaman alabilir. Bu aşamada, gereken değişikliklerin kapsamını ayrıntılı olarak anlamak ve bir plan geliştirmek için zaman harcamanız, özellikle karmaşık bir kod tabanınız varsa, genellikle son olarak size zaman kazandırır.

Planınız hala .NET Framework 4.7.2 hedeflerken kod tabanınızda önemli değişiklikler yapmayı içerebilir. Bu, önceki yaklaşımın daha yapılandırılmış bir sürümüdür. Planınızı yürütme hakkında nasıl gittiğiniz, kod tabanınıza bağımlıdır.

### <a name="mixed-approach"></a>Karışık yaklaşım

Yukarıdaki yaklaşımlardan proje başına temelinde karıştıracaksınız. Sizin ve kod tabanınız için en mantıklı şeyi yapın.

## <a name="port-your-tests"></a>Testlerinizin bağlantı noktası

Kodunuzu yazarken her şeyin çalıştığından emin olmanın en iyi yolu, .NET 'e bağlantı noktası oluştururken kodunuzu test etmek. Bunu yapmak için, .NET için testler oluşturup çalıştıran bir test çerçevesi kullanmanız gerekir. Şu anda üç seçeneğiniz vardır:

- [xUnit](https://xunit.net/)
  - [Başlarken](https://xunit.net/docs/getting-started/netcore/cmdline)
  - [MSTest projesini xUnit 'e dönüştüren araç](https://github.com/dotnet/codeformatter/tree/main/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Başlarken](https://github.com/nunit/docs/wiki/Installation)
  - [MSTest 'ten NUnit 'e geçiş hakkında blog gönderisi](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Önerilen yaklaşım

Son olarak, taşıma çabası .NET Framework kodunuzun nasıl yapılandırıldığına bağlıdır. Kodunuzun bağlantı noktasının temelini oluşturan, kodunuzun temel bileşenleri olan, kitaplığınızın *temelini* oluşturmaya yönelik iyi bir yoldur. Bu, başka her şeyin doğrudan veya dolaylı olarak kullandığı veri modelleri veya diğer temel sınıflar ve yöntemler olabilir.

01. Şu anda taşıma yaptığınız kitaplığınızın katmanını sınayan test projesi bağlantı noktası.
01. Kitaplığınızın temelini yeni bir .NET projesine kopyalayın ve desteklemek istediğiniz .NET Standard sürümünü seçin.
01. Derlenecek kodu almak için gereken değişiklikleri yapın. Bunun büyük bölümü, *csproj* dosyanıza NuGet paketi bağımlılıkları eklenmesini gerektirebilir.
01. Testleri çalıştırın ve gerekli ayarlamaları yapın.
01. Üzerinde bağlantı noktası için sonraki kod katmanını seçin ve önceki adımları tekrarlayın.

Kitaplığınızın temelini başlatıp her bir katmanı gerektiği gibi test ederseniz, taşıma işlemi, sorunların tek seferde bir kod katmanına yalıtılabileceği sistematik bir işlemdir.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[.NET için projeleri düzenleme](project-structure.md)
