---
title: .NET Compiler Platform SDK’sı (Roslyn API’leri)
description: .NET kodunu anlamak, hataları belirlemek ve bu hataları onarmak için .NET Compiler Platform SDK 'sını (Roslyn API 'Leri olarak da bilinir) kullanmayı öğrenin.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: 872bfd388f6974a6d99f769c43e5d341454518cc
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226679"
---
# <a name="the-net-compiler-platform-sdk"></a>.NET Compiler Platform SDK 'Sı

Derleyiciler, bu kodun söz dizimini ve semantiğini doğrulayan, uygulama kodunun ayrıntılı bir modelini oluşturur. Bu model, kaynak koddan yürütülebilir çıktıyı oluşturmak için kullanılır. .NET Compiler Platform SDK bu modele erişim sağlar. Giderek, üretkenliğinizi artırmak için IntelliSense, yeniden düzenleme, akıllı yeniden adlandırma, "tüm başvuruları bul" ve "tanıma git" gibi tümleşik geliştirme ortamı (IDE) özelliklerine güveniyoruz. Kod kaliteimizi ve uygulama oluşturmaya yardımcı olmak için kod oluşturucularımızı geliştirmek üzere kod analizi araçlarına güveniyoruz. Bu araçların daha akıllı bir şekilde yararlandıkları için, uygulama kodunu işlemek üzere yalnızca derleyicilerin oluşturdukları modele daha fazla ve daha fazlasına erişmesi gerekir. Roslyn API 'Lerinin temel görevi budur: donuk kutuları açma ve araçların ve son kullanıcıların, en fazla bilgi derleyicileri, kodumuza sahip olduğu konusunda paylaşmasına izin verme.
Roslyn aracılığıyla, opak kaynak kodu ve nesne kodu genişletme çeviricileri olması yerine, derleyiciler şu şekilde olur: Araçlar ve uygulamalarınızda kod ile ilgili görevler için kullanabileceğiniz API 'Ler.

## <a name="net-compiler-platform-sdk-concepts"></a>.NET Compiler Platform SDK kavramları

.NET Compiler Platform SDK, kod odaklı araçları ve uygulamaları oluşturmak için engel önemli ölçüde düşürür. Meta programlama, kod oluşturma ve dönüştürme, C# ve Visual Basic dillerinin etkileşimli kullanımı ve etki alanına özgü dillerde C# ve Visual Basic ekleme gibi alanlarda yenilik için birçok fırsat oluşturur.

.NET Compiler Platform SDK, kodlama hatalarını bulup düzelten ***çözümleyiciler*** ve ***kod düzeltmeleri*** oluşturmanıza olanak sağlar. ***Çözümleyiciler*** , kodun sözdizimini ve yapısını anlayıp düzeltilmesi gereken uygulamaları algılar. ***Kod düzeltmeleri*** , çözümleyiciler tarafından bulunan kodlama hatalarının adreslenmesi için bir veya daha fazla önerilen düzeltme sağlar. Genellikle, bir çözümleyici ve ilişkili kod düzeltmeleri tek bir projede birlikte paketlenir.

Çözümleyiciler ve kod düzeltmeleri kodu anlamak için statik analizler kullanır. Kodu çalıştırmaz veya diğer test avantajları sağlamaz. Ancak, genellikle hatalara, sürdürülebilir koda veya Standart Kılavuz ihlaline yol açabilecek uygulamalar ortaya çıkar.

.NET Compiler Platform SDK, bir C# veya Visual Basic kod temeli incelemenizi ve anlamanıza olanak tanıyan tek bir API kümesi sağlar. Bu tek kod temelini kullanabilmeniz için, .NET Compiler Platform SDK 'Sı tarafından sunulan sözdizimsel ve anlam Analizi API 'Lerinden yararlanarak çözümleyiciler ve kod düzeltmeleri daha kolay bir şekilde yazabilirsiniz. Derleyicinin yaptığı çözümlemenin çoğaltılmasının büyük bir görevinden serbest bırakılmış olduğunda, projeniz veya kitaplığınız için ortak kodlama hatalarını bulma ve düzeltme hakkında daha odaklanmış bir göreve odaklanabilirsiniz.

Daha küçük bir avantaj, çözümleyicilerin ve kod düzeltmalarınızın daha küçük olması ve Visual Studio 'da yüklendiğinde bir projedeki kodu anlamak için kendi kod tabanınızı yazdığınızda çok daha az bellek kullanmasıdır. Derleyici ve Visual Studio tarafından kullanılan sınıflardan yararlanarak kendi statik analiz araçlarınızı oluşturabilirsiniz. Bu, takımınızın, IDE performansını fark etmeden bir etkisi olmadan çözümleyiciler ve kod düzeltmeleri kullanabileceği anlamına gelir.

Çözümleyiciler ve kod düzeltmeleri yazmak için üç ana senaryo vardır:

1. [*Takım kodlama standartlarını zorla*](#enforce-team-coding-standards)
1. [*Kitaplık paketleriyle rehberlik sağlama*](#provide-guidance-with-library-packages)
1. [*Genel rehberlik sağlama*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Takım kodlama standartlarını zorla

Birçok ekibin, diğer ekip üyeleriyle kod İncelemeleri aracılığıyla zorlanan kodlama standartları vardır. Çözümleyiciler ve kod düzeltmeleri, bu işlemi çok daha verimli hale getirir. Bir geliştirici ekipte diğerleriyle birlikte çalışmalarını paylaşıyorsa, kod İncelemeleri meydana gelir. Geliştirici, herhangi bir yorum almadan önce yeni bir özelliği tamamlamaya yönelik tüm zamanı yatıracaktır. Geliştiriciler, takımın uygulamalarıyla eşleşmeyen alışkanlıkları zorlarken bu işlem tarafından değişebilir.

Çözümleyiciler geliştirici kodu yazanlar olarak çalışır. Geliştirici, Kılavuzu hemen takip eden anında geri bildirim alır. Geliştirici, prototip yazmaya başladığı anda uyumlu kod yazmak için alışkanlıkları oluşturur. Özellik insanlar tarafından incelenmek üzere hazırlandığında, tüm standart rehberlik zorlanır.

Takımlar, takım kodlama uygulamalarını ihlal eden en yaygın uygulamaları bulmak için çözümleyiciler ve kod düzeltmeleri oluşturabilir. Bu, standartları zorlamak için her geliştiricinin makinesine yüklenebilir.

## <a name="provide-guidance-with-library-packages"></a>Kitaplık paketleriyle rehberlik sağlama

NuGet üzerinde .NET geliştiricileri için kullanılabilen çok sayıda kitaplık vardır.
Bunlardan bazıları, üçüncü taraf şirketlerden bazıları ve Topluluk üyelerinden ve gönüllü teers 'tan bazıları tarafından Microsoft 'tan geliyor. Bu kitaplıklar, geliştiricilerin bu kitaplıklarla başarılı olabilmesi için daha fazla benimseme ve daha fazla inceleme alır.

Belge sağlamaya ek olarak, kitaplığınızın ortak yanlış kullanımlarını bulup düzelten çözümleyiciler ve kod düzeltmeleri sağlayabilirsiniz. Bu anında düzeltmeler, geliştiricilerin daha hızlı başarılı olmasını sağlayacaktır.

NuGet 'de çözümleyicilerin ve kod düzeltmelerinin kitaplığınızı paketleyebilir. Bu senaryoda, NuGet paketinizi yükleyen her geliştirici Çözümleyicisi paketini de yükler. Kitaplığınızı kullanan tüm geliştiriciler, hatalar ve önerilen düzeltmeler hakkında anında geri bildirim biçiminde takımınızdan hemen kılavuzluk eder.

## <a name="provide-general-guidance"></a>Genel rehberlik sağlama

.NET geliştirici topluluğu, en iyi şekilde çalışan deneyim desenleri ve en iyi kaçınılmış desenler aracılığıyla keşfedilmiştir. Birçok topluluk üyesi, bu önerilen desenleri zorlayan çözümleyiciler oluşturmuş. Daha fazla bilgi edindiğimiz gibi, yeni fikirler için her zaman yer vardır.

Bu çözümleyiciler [Visual Studio Market](https://marketplace.visualstudio.com/vs) yüklenebilir ve Visual Studio kullanılarak geliştiriciler tarafından indirilebilir. Yeni dile ve platforma yönelik olarak kabul edilen uygulamalar, .NET yolculuğunda daha önce kabul edilebilir ve daha önce üretken hale gelir. Bunlar daha yaygın olarak kullanıldığından, topluluk bu uygulamaları benimsemiştir.

## <a name="next-steps"></a>Sonraki adımlar

.NET Compiler Platform SDK, kod oluşturma, çözümleme ve yeniden düzenleme için en son dil nesne modellerini içerir. Bu bölüm .NET Compiler Platform SDK 'ya kavramsal bir genel bakış sağlar. Hızlı başlangıçlar, örnekler ve öğreticiler bölümlerinde daha fazla ayrıntı bulabilirsiniz.

Bu beş konuda .NET Compiler Platform SDK 'daki kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [Söz dizimi görselleştiricisi ile kod bulma](syntax-visualizer.md)
- [Derleyici API modelini anlama](compiler-api-model.md)
- [Söz dizimi ile çalışma](work-with-syntax.md)
- [Semantik ile çalışma](work-with-semantics.md)
- [Bir çalışma alanı ile çalışma](work-with-workspace.md)

Başlamak için **.net Compiler Platform SDK 'sını**yüklemeniz gerekir:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
