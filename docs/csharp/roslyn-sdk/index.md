---
title: .NET Compiler Platform SDK’sı (Roslyn API’leri)
description: .NET kodunu anlamak, hataları tespit etmek ve bu hataları düzeltmek için .NET Derleyici Platformu SDK'yı (Roslyn API'leri olarak da adlandırılır) kullanmayı öğrenin.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: a1ceb1d11cf846e67be2c6558978e01133e591da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76742744"
---
# <a name="the-net-compiler-platform-sdk"></a>.NET Derleyici Platformu SDK

Derleyiciler, bu kodun sözdizimini ve semantiğini doğrularken uygulama kodunun ayrıntılı bir modelini oluştururlar. Bu modeli, kaynak kodundan çalıştırılabilir çıktıoluşturmak için kullanırlar. .NET Derleyici Platformu SDK bu modele erişim sağlar. Üretkenliğimizi artırmak için IntelliSense, refactoring, akıllı yeniden adlandırma, "Tüm referansları bul" ve "Tanıma git" gibi entegre geliştirme ortamı (IDE) özelliklerine giderek daha fazla güveniyoruz. Kod kalitemizi geliştirmek için kod analiz araçlarına ve uygulama yapımına yardımcı olacak kod jeneratörlerine güveniyoruz. Bu araçlar daha akıllı hale gelince, yalnızca derleyicilerin uygulama kodunu işlerken oluşturdukları modelin daha fazlasına erişmeye ihtiyaç duyarlar. Bu Roslyn API'lerinin temel misyonudur: kara kutuları açmak ve araçların ve son kullanıcıların kodumuz hakkında sahip olduğu bilgi derleyicilerinin zenginliğini paylaşmalarına izin vermek.
Roslyn aracılığıyla opak kaynak kodlu ve nesne kodlu çevirmenler olmak yerine, derleyiciler platform haline gelir: Araçlarınızda ve uygulamalarınızda kodla ilgili görevler için kullanabileceğiniz API'ler.

## <a name="net-compiler-platform-sdk-concepts"></a>.NET Derleyici Platformu SDK kavramları

.NET Derleyici Platformu SDK, kod odaklı araçlar ve uygulamalar oluşturmak için giriş engelini önemli ölçüde düşürür. Meta programlama, kod oluşturma ve dönüştürme, C# ve Visual Basic dillerinin etkileşimli kullanımı ve etki alanına özgü dillerde C# ve Visual Basic'in katıştırma gibi alanlarda inovasyon için birçok fırsat yaratır.

.NET Derleyici Platformu SDK, kodlama hatalarını bulan ve düzelten ***analizörler*** ve ***kod düzeltmeleri*** oluşturmanıza olanak tanır. ***Çözümleyiciler*** kodun sözdizimini ve yapısını anlar ve düzeltilmesi gereken uygulamaları algılar. ***Kod düzeltmeleri,*** çözümleyiciler tarafından bulunan kodlama hatalarını gidermek için önerilen bir veya daha fazla düzeltme sağlar. Genellikle, bir çözümleyici ve ilişkili kod düzeltmeleri tek bir projede birlikte paketlenir.

Çözümleyiciler ve kod düzeltmeleri kodu anlamak için statik çözümleme kullanır. Kodu çalıştırmaz veya başka sınama avantajları sağlamaz. Ancak, genellikle hatalara, sürdürülemez koda veya standart kılavuz ihlaline yol açan uygulamalara işaret edebilirler.

.NET Derleyici Platformu SDK, c# veya Visual Basic kod tabanını incelemenizi ve anlamanızı sağlayan tek bir API kümesi sağlar. Bu tek kod tabanını kullanabileceğiniz için,.NET Derleyici Platformu SDK tarafından sağlanan sözdizimi ve anlamsal analiz API'lerinden yararlanarak çözümleyicileri ve kod düzeltmelerini daha kolay yazabilirsiniz. Derleyici tarafından yapılan çözümlemesi çoğaltma büyük görevden kurtulmuş, bulma ve proje veya kitaplık için ortak kodlama hataları düzeltme daha odaklı görev konsantre olabilirsiniz.

Daha küçük bir yararı, çözümleyicilerinizin ve kod düzeltmelerinizin daha küçük olması ve Visual Studio'ya yüklendiğinde, projedeki kodu anlamak için kendi kod tabanınızı yazmanızdan çok daha az bellek kullanmasıdır. Derleyici ve Visual Studio tarafından kullanılan aynı sınıfları kullanarak, kendi statik analiz araçları oluşturabilirsiniz. Bu, ekibinizin IDE'nin performansı üzerinde gözle görülür bir etki yaratmadan çözümleyicileri ve kod düzeltmelerini kullanabileceği anlamına gelir.

Çözümleyiciler ve kod düzeltmeleri yazmak için üç ana senaryo vardır:

1. [*Ekip kodlama standartlarını uygulayın*](#enforce-team-coding-standards)
1. [*Kütüphane paketleriyle rehberlik sağlayın*](#provide-guidance-with-library-packages)
1. [*Genel rehberlik sağlayın*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Ekip kodlama standartlarını uygulayın

Birçok takımın, diğer ekip üyeleriyle kod incelemeleri yoluyla uygulanan kodlama standartları vardır. Çözümleyiciler ve kod düzeltmeleri bu işlemi çok daha verimli hale getirebilir. Kod incelemeleri, bir geliştirici çalışmalarını ekipteki diğer kişilerle paylaştığında gerçekleşir. Geliştirici herhangi bir yorum almadan önce yeni bir özellik tamamlamak için gerekli her zaman yatırım olacaktır. Geliştirici, takımın antrenmanlarına uymayan alışkanlıkları pekiştirirken haftalar cayabilir.

Çözümleyiciler bir geliştirici olarak çalıştırın kod yazar. Geliştirici, kılavuzu hemen takip eden anında geri bildirim alır. Geliştirici, prototip oluşturmaya başlar başlamaz uyumlu kod yazma alışkanlıkları oluşturur. Özellik insanların incelemesi için hazır olduğunda, tüm standart kılavuz lar uygulanır.

Takımlar, takım kodlama uygulamalarını ihlal eden en yaygın uygulamaları arayan çözümleyiciler ve kod düzeltmeleri oluşturabilir. Bunlar, standartları uygulamak için her geliştiricinin makinesine yüklenebilir.

## <a name="provide-guidance-with-library-packages"></a>Kütüphane paketleriyle rehberlik sağlayın

NuGet'de .NET geliştiricileri için çok sayıda kütüphane bulunmaktadır.
Bunların bazıları Microsoft'tan, bazıları üçüncü taraf şirketlerden ve diğerleri topluluk üyelerinden ve gönüllülerden gelir. Bu kitaplıklar, geliştiriciler bu kitaplıklarla başarılı olduğunda daha fazla benimseme ve daha yüksek incelemeler alır.

Belge sağlamanın yanı sıra, kitaplığınızın yaygın yanlış kullanımlarını bulan ve düzelten çözümleyiciler ve kod düzeltmeleri sağlayabilirsiniz. Bu acil düzeltmeler geliştiricilerin daha hızlı başarılı yardımcı olacaktır.

NuGet'deki kitaplığınız ile analizörleri ve kod düzeltmelerini paketleyebilirsiniz. Bu senaryoda, NuGet paketinizi yükleyen her geliştirici çözümleyici paketini de yükler. Kitaplığınızı kullanan tüm geliştiriciler, hatalar ve önerilen düzeltmeler hakkında anında geri bildirim formunda ekibinizden hemen rehberlik alır.

## <a name="provide-general-guidance"></a>Genel rehberlik sağlayın

.NET geliştirici topluluğu, iyi çalışan deneyim kalıpları ve en iyi kaçınılan desenler aracılığıyla keşfedmiştir. Bazı topluluk üyeleri, bu önerilen desenleri uygulayan çözümleyiciler oluşturmuştur. Biz daha fazla bilgi olarak, her zaman yeni fikirler için yer vardır.

Bu analizörler Visual Studio [Marketplace'e](https://marketplace.visualstudio.com/vs) yüklenebilir ve Visual Studio kullanan geliştiriciler tarafından indirilebilir. Dile ve platforma yeni başlayanlar kabul edilen uygulamaları hızlı bir şekilde öğrenir ve .NET yolculuklarında daha erken üretken olurlar. Bunlar daha yaygın olarak kullanılmaya açıldıkça, toplum bu uygulamaları benimser.

## <a name="next-steps"></a>Sonraki adımlar

.NET Derleyici Platformu SDK, kod oluşturma, analiz ve yeniden düzenleme için en son dil nesnesi modellerini içerir. Bu bölümde .NET Derleyici Platformu SDK'ya kavramsal bir genel bakış sağlanmaktadır. Daha fazla bilgi quickstarts, örnekler ve öğreticiler bölümlerinde bulunabilir.

.NET Derleyici Platformu SDK'daki kavramlar hakkında daha fazla bilgi için bu beş konudan bilgi alabilirsiniz:

- [Söz dizimi görselleştiricisi ile kod bulma](syntax-visualizer.md)
- [Derleyici API modelini anlama](compiler-api-model.md)
- [Söz dizimi ile çalışma](work-with-syntax.md)
- [Semantik ile çalışma](work-with-semantics.md)
- [Bir çalışma alanı ile çalışma](work-with-workspace.md)

Başlamak için **.NET Derleyici Platformu SDK'yı**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
