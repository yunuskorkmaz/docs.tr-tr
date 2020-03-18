---
title: .NET Core bağlantı noktası kitaplıkları
description: Kitaplık projelerini .NET Framework'den .NET Core'a nasıl ileteceklerini öğrenin.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 68fe36e543d949dc76bdb0c19ef3482936ad9e79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398911"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port .NET Framework kütüphaneleri .NET Core

.NET Framework kitaplık kodunu ,NET Core'a nasıl ulaştıracağınızı ve platform lar arası çalıştığı ve onu kullanan uygulamaların erişimini nasıl genişlettiği öğrenin.

## <a name="prerequisites"></a>Önkoşullar

Bu makalede, şunları varsayar:

- Visual Studio 2017 veya sonraki lerini kullanıyoruz. (.NET Core Visual Studio önceki sürümlerinde desteklenmez.)
- Önerilen [taşıma işlemini](index.md)anlayın.
- Üçüncü taraf bağımlılıklarıyla ilgili sorunları [çözdük.](third-party-deps.md)

Ayrıca aşağıdaki makalelerin içeriği aşina olmalıdır:

[.NET Standardı](../../standard/net-standard.md)\
Bu makalede, tüm .NET uygulamalarında bulunması amaçlanan .NET API'lerinin resmi belirtimi açıklanmaktadır.

[Paketler, Metapaketler ve Çerçeveler](../packages.md)\
Bu makalede.NET Core'un paketleri nasıl tanımladığı ve kullandığı ve paketlerin birden çok .NET uygulamasında çalışan destek kodunu niçin kullandığı açıklanır.

[Çapraz Platform Araçları ile Kütüphaneler Geliştirme](../tutorials/libraries.md)\
Bu makalede, .NET Core CLI kullanarak kitaplıkların nasıl yazılalıyorum.

[.NET Core için *csproj* formatına eklemeler](../tools/csproj.md)\
Bu makalede, *csproj* ve MSBuild'e taşınmanın bir parçası olarak proje dosyasına eklenen değişiklikler özetlenmiştir.

[.NET Core'a Taşıma - Üçüncü Taraf Bağımlılıklarınızı Analiz Etme](third-party-deps.md)\
Bu makalede, üçüncü taraf bağımlılıklarının taşınabilirliği ve Bir NuGet paket bağımlılığı .NET Core'da çalışmadığında ne yapmanız gerektiğini açıklar.

## <a name="retarget-to-net-framework-472"></a>.NET Framework 4.7.2'ye yeniden hedefleme

Kodunuz .NET Framework 4.7.2'yi hedeflemiyorsa, .NET Framework 4.7.2'yi yeniden hedeflemenizi tavsiye ettik. Bu, .NET Standardının varolan API'leri desteklemediği durumlar için en son API alternatiflerinin kullanılabilirliğini sağlar.

Bağlantı noktası olmak istediğiniz projelerin her biri için Visual Studio'da aşağıdakileri yapın:

1. Projeye sağ tıklayın ve **Özellikler'i**seçin.
1. Hedef **Çerçeve** açılır düşüşünde **.NET Framework 4.7.2'yi**seçin.
1. Projeyi yeniden derle.

Projeleriniz artık .NET Framework 4.7.2'yi hedeflediğiiçin, kod taşıma için temel olarak .NET Framework'ün bu sürümünü kullanın.

## <a name="determine-portability"></a>Taşınabilirliği belirleme

Bir sonraki adım, analiz için taşınabilirlik raporu oluşturmak için API Taşınabilirlik Çözümleyicisini (ApiPort) çalıştırmaktır.

[API Taşınabilirlik Çözümleyicisi'ni (ApiPort)](../../standard/analyzers/portability-analyzer.md) ve .NET Core'u hedeflemek için taşınabilirlik raporlarının nasıl oluşturacağınızı anladığınızdan emin olun. Bunu nasıl yapacağınız büyük olasılıkla ihtiyaçlarınıza ve kişisel zevklerinize göre değişir. Aşağıdaki bölümlerde birkaç farklı yaklaşım ayrıntılı. Kodunuzu nasıl yapılandırıldığına bağlı olarak kendinizi bu yaklaşımların adımlarını karıştırArak bulabilirsiniz.

### <a name="deal-primarily-with-the-compiler"></a>Öncelikle derleyici ile anlaşma

Bu yaklaşım, çok fazla .NET Framework API kullanmayan küçük projeler veya projeler için iyi çalışır. Yaklaşım basittir:

1. İsteğe bağlı olarak, projenizde ApiPort çalıştırın. ApiPort'u çalıştırın, ele almanız gereken konular hakkında rapordan bilgi edinin.
1. Tüm kodunuzu yeni bir .NET Core projesinde kopyalayın.
1. Taşınabilirlik raporuna atıfta bulunurken (oluşturulursa), derleyici hatalarını proje tam olarak derleyene kadar çözün.

Yapılandırılan olmamasına rağmen, bu kod odaklı yaklaşım genellikle sorunları hızlı bir şekilde çözer. Yalnızca veri modelleri içeren bir proje bu yaklaşım için ideal bir aday olabilir.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Taşınabilirlik sorunları çözülene kadar .NET Framework'de kalın

Tüm işlem boyunca derlenen bir kod olmasını tercih ederseniz, bu yaklaşım en iyisi olabilir. Yaklaşım aşağıdaki gibidir:

1. ApiPort'u bir projede çalıştırın.
1. Taşınabilir farklı API'ler kullanarak sorunları giderin.
1. Doğrudan bir alternatif kullanmanın engellendiği alanlara dikkat edin.
1. Her birinin yeni bir .NET Core projesine kopyalanmaya hazır olduğundan emin olana kadar taşıma yaptığınız tüm projeler için önceki adımları yineleyin.
1. Kodu yeni bir .NET Core projesine kopyalayın.
1. Doğrudan bir alternatifin var olmadığını belirttiğiniz sorunları çözün.

Bu dikkatli yaklaşım sadece derleyici hataları çalışma daha yapılandırılmış, ama yine de nispeten kod odaklı ve her zaman derleyen kod sahip yararı vardır. Başka bir API kullanarak ele alınamayan bazı sorunları çözme şekliniz büyük ölçüde değişir. Bir sonraki yaklaşımda ele alınan belirli projeler için daha kapsamlı bir plan geliştirmeniz gerektiğini görebilirsiniz.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Kapsamlı bir saldırı planı geliştirin

Bu yaklaşım, kodu yeniden yapılandırmanın veya belirli kod alanlarının yeniden yazılmasının .NET Core'u desteklemek için gerekli olabileceği daha büyük ve daha karmaşık projeler için en iyi yaklaşım olabilir. Yaklaşım aşağıdaki gibidir:

1. ApiPort'u bir projede çalıştırın.
1. Taşınabilir olmayan her türün nerede kullanıldığını ve bunun genel taşınabilirliği nasıl etkilediğini anlayın.
   - Bu tür lerin doğasını anlayın. Sayıca az dır ama sık kullanılırlar mı? Sayıca fazla dır ama seyrek olarak kullanılırlar mı? Kullanımları yoğunmu, yoksa kodunuza mı yayılır?
   - Taşınabilir olmayan kodu daha etkili bir şekilde başa çıkabilmeniz için yalıtmak kolay mı?
   - Kodunuzu yeniden düzenlemeniz gerekiyor mu?
   - Taşınabilir olmayan bu türler için, aynı görevi yerine getiren alternatif API'ler var mı? Örneğin, <xref:System.Net.WebClient> sınıfı kullanıyorsanız, <xref:System.Net.Http.HttpClient> bunun yerine sınıfı kullanabilirsiniz.
   - Bir bırakma yerine olmasa bile, bir görevi gerçekleştirmek için farklı taşınabilir API'ler var mı? Örneğin, XML'i <xref:System.Xml.Schema.XmlSchema> ayrıştırmak için kullanıyorsanız ancak XML şema keşfi ni <xref:System.Xml.Linq> gerektirmiyorsa, API'lere güvenerek yerine API'leri kullanabilir ve ayrıştırmayı uygulayabilirsiniz.
1. Bağlantı noktası zor olan derlemeler varsa, şimdilik .NET Framework'de bırakmaya değer mi? Göz önünde bulundurulması gereken bazı şeyler şunlardır:
   - Kitaplığınızda .NET Core ile uyumsuz bazı işlevler olabilir, çünkü bu işlevler .NET Framework veya Windows'a özgü işlevsellik lere çok fazla dayanır. Bu işlevselliği şimdilik geride bırakıp, özellikleri taşıma noktasına gelenkaynaklar kullanılabilir olana kadar kitaplığınızın geçici bir .NET Core sürümünü daha az özelliklere sahip olarak yayınlamaya değer mi?
   - Bir refactor yardımcı olur mu?
1. Kullanılamayan bir .NET Framework API'yi kendi uygulamanızı yazmak mantıklı mıdır?
   [.NET Framework başvuru kaynağından](https://github.com/Microsoft/referencesource)kodu kopyalamayı, değiştirmeyi ve kullanmayı düşünebilirsiniz. Referans kaynak kodu [MIT Lisansı](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)altında lisanslanmıştır, bu nedenle kaynağı kendi kodunuz için temel olarak kullanma özgürlüğünüz vardır. Microsoft'u kodunuza doğru şekilde atfettiğimizden emin olun.
1. Bu işlemi farklı projeler için gerektiği gibi yineleyin.

Çözümleme aşaması, kod tabanınızın boyutuna bağlı olarak biraz zaman alabilir. Gereken değişikliklerin kapsamını iyice anlamak ve bir plan geliştirmek için bu aşamada zaman harcamak, özellikle karmaşık bir kod tabanınız varsa, genellikle uzun vadede size zaman kazandırır.

Planınız,.NET Framework 4.7.2'yi hedefleyerek kod tabanınızda önemli değişiklikler yapmayı kapsayabilir ve bu da önceki yaklaşımın daha yapılandırılmış bir sürümünü yapabilir. Planınızı nasıl uygulayabileceğiniz kod tabanınıza bağlıdır.

### <a name="mixed-approach"></a>Karışık yaklaşım

Yukarıdaki yaklaşımları proje başına karıştıracağınız olasıdır. Size ve kod tabanınız için en mantıklı olanı yapmalısınız.

## <a name="port-your-tests"></a>Testlerinizi silikle

Kodunuzu taşımayaptığınızda her şeyin çalıştığından emin olmak için en iyi yol, kodunuzu .NET Core'a taşımayaparken sınamaktır. Bunu yapmak için .NET Core için testler oluşturan ve çalıştıran bir sınama çerçevesi kullanmanız gerekir. Şu anda üç seçeneğiniz vardır:

- [xBirim](https://xunit.github.io/)
  - [Başlarken](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [MSTest projesini xUnit'e dönüştürme aracı](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Başlarken](https://github.com/nunit/docs/wiki/Installation)
  - [MSTest'ten NUnit'e geçiş hakkında blog yazısı](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Önerilen yaklaşım

Sonuç olarak, taşıma çabası büyük ölçüde .NET Framework kodunuzu nasıl yapılandırıldığına bağlıdır. Kodunuzu taşımanın iyi bir yolu, kodunuzu temel bileşenleri olan kitaplığınızın *tabanıyla* başlamaktır. Bu, veri modelleri veya diğer bazı temel sınıfları ve her şeyin doğrudan veya dolaylı olarak kullandığı yöntemler olabilir.

1. Şu anda taşımakta olduğunuz kitaplığınızın katmanını sınayan test projesini siler.
1. Kitaplığınızın tabanından yeni bir .NET Core projesine kopyalayın ve desteklemek istediğiniz .NET Standardı'nın sürümünü seçin.
1. Kodu derlemek için gereken değişiklikleri yapın. Bunların çoğu *csproj* dosyanıza NuGet paket bağımlılıkları eklemeyi gerektirebilir.
1. Testleri çalıştırın ve gerekli ayarlamaları yapın.
1. Bağlantı noktası için bir sonraki kod katmanını seçin ve önceki adımları yineleyin.

Kitaplığınızın tabanıyla başlayıp tabandan dışa doğru hareket ederseniz ve her katmanı gerektiği gibi sınarsanız, taşıma, sorunların aynı anda bir kod katmanına yalıtıldığı sistematik bir işlemdir.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[.NET Core için projeleri düzenleme](project-structure.md)
