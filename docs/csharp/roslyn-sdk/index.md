---
title: .NET derleyici Platformu SDK'sı (Roslyn API'leri)
description: .NET derleyici Platformu (Roslyn API'leri olarak da bilinir) SDK .NET kod, hataların, anlamak ve bu hataları düzeltmek için kullanmayı öğrenin.
ms.date: 10/10/2017
ms.custom: mvc
ms.openlocfilehash: be65d8ecafc13fc699efb10dc396b0631ba70810
ms.sourcegitcommit: 81bd16c7435a8c9183d2a7e878a2a5eff7d04584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2019
ms.locfileid: "54249144"
---
# <a name="the-net-compiler-platform-sdk"></a>.NET derleyici Platformu SDK'sı

Söz dizimi ve kodun semantik doğrulama gibi derleyicileri uygulama kodu daha ayrıntılı bir modelini oluşturun. Bunlar yürütülebilir çıkışı kaynak kodu oluşturmak için bu modeli kullanır. .NET derleyici Platformu SDK'sı, bu model erişim sağlar. Gittikçe, biz tümleşik geliştirme ortamı (IDE) özelliklerini kullanan yeniden düzenleme, IntelliSense, akıllı yeniden adlandırma, "tüm başvuruları Bul" ve "Tanıma Git" gibi bizim üretkenliği artırmak için. Biz, bizim kod kalitesini ve uygulama oluşturma, yardımcı olmak için kod oluşturucuları geliştirmek için kod çözümleme araçları dayanır. Bu araçlar daha akıllıca kararlar alın gibi daha fazla ve daha fazla uygulama kodu işlemek gibi yalnızca derleyiciler oluşturduğunuz modelin erişim. Roslyn API'leri çekirdek görev budur: siyah kutularını açan açarak ve araçları ve zengin bilgi derleyiciler içinde paylaşmak için son kullanıcılara izin vererek kodumuz hakkında sahip.
Roslyn, aracılığıyla donuk kaynak kod içinde ve nesne kodu çıkış çevirmenler olan yerine derleyiciler platformları olur: Kodla ilgili görevler araç ve uygulamalar için kullanabileceğiniz API'ler.

## <a name="net-compiler-platform-sdk-concepts"></a>.NET derleyici Platformu SDK'sı kavramları

.NET derleyici Platformu SDK'sı kod odaklı araç ve uygulamalar oluşturmak için giriş engel önemli ölçüde azaltır. C# ve VB dil ve C# ve VB etki alanına özgü diller katıştırma meta programlama kod oluşturma ve dönüştürme, etkileşimli kullanmak gibi alanlarda yenilik için birçok fırsat oluşturur.

.NET derleyici Platformu SDK'sı oluşturmanıza olanak sağlayan ***Çözümleyicileri*** ve ***kod düzeltme*** bulun ve kodlama hatalarını düzeltin. ***Çözümleyiciler*** kod yapısını ve söz dizimini anlamak ve düzeltilmesi gereken yöntemler algılayın. ***Kod düzeltme*** çözümleyiciler tarafından bulunan kodlama hatalarını ele almak için bir veya daha fazla önerilen düzeltmeleri sağlayabilir. Genellikle, bir çözümleyici ve ilişkili kod düzeltmeleri tek bir projede birlikte paketlenmiştir. 

Çözümleyicileri ve kod düzeltmeleri kod anlamak için statik çözümleme kullanın. Bunlar kodu çalıştırmayın ve diğer test yararlar sağlar. Bunların ancak hatalar, kodlardan veya standart kılavuz doğrulama genellikle neden uygulamaları işaret olabilir.

.NET derleyici Platformu SDK'sı tek bir inceleyin ve bir C# veya Visual Basic kod temeli anlamanıza olanak sağlayan API kümesi sağlar. Bu tek bir kod temeli kullanabileceğinizden, çözümleyiciler yazabilirsiniz ve sözdizimsel ve semantik analizi .NET derleyici Platformu SDK tarafından sağlanan API'leri yararlanarak daha kolay kodu düzeltir. Derleyici tarafından yapılan çözümleme çoğaltmak büyük görevden serbest, proje veya kitaplığı için yaygın kodlama hataları bulma ve düzeltme daha odaklı görevini üzerinde odaklanabilirsiniz.

Daha küçük bir avantajı, Çözümleyicileri ve kod düzeltmeleri daha küçük ve çok daha az bellek kendi yazdıysanız bunlar kod projesinde anlamak için codebase daha Visual Studio'ya yüklendiğinde kullanmak içindir. Derleyici ve Visual Studio tarafından kullanılan sınıfların yararlanarak kendi statik analiz araçları oluşturabilirsiniz. Bu, takımınızın Çözümleyicileri kullanabilirsiniz ve IDE'nin performansı belirgin bir etkisi olmadan kod düzeltmeleri anlamına gelir.

Çözümleyicileri ve kod düzeltmeleri yazmak için üç ana senaryo vardır:

1. [*Takım kod standartlarımız, koda zorla*](#enforce-team-coding-standards)
1. [*Kitaplık paketleriyle rehberlik*](#provide-guidance-with-library-packages)
1. [*Genel rehberlik*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>Takım kod standartlarımız, koda zorla

Birçok ekip, kodlama diğer takım üyeleri kod incelemeleriyle aracılığıyla zorlanır standartları vardır. Çözümleyicileri ve kod düzeltmeleri bu işlem çok daha verimli olmasını sağlayabilir. Bir geliştirici çalışmalarını başkalarıyla ekipte paylaştığında, kod incelemeleri gerçekleşir. Geliştirici açıklamaları almadan önce yeni bir özelliği tamamlamak için gereken her zaman yatırım yapmış. Takımın yöntemler eşleşmeyen alışkanlıkları Geliştirici güçlendirir sırada hafta Git.

Bir geliştirici kodu yazdığı gibi çözümleyiciler çalıştırın. Geliştirici yönergeleri hemen teşvik eder anında geri bildirim alır. Geliştirici, prototip oluşturma başlar başlamaz uyumlu kod yazma alışkanlıkların. Özellik gözden geçirmek, insanlar için hazır olduğunda, tüm standart Kılavuzu zorlandı.

Takımlar Çözümleyicileri oluşturabilirsiniz ve kod düzeltmeleri, takım kodlama uygulamaları ihlal en yaygın yöntemleri arayın. Bu standartları zorlamak için her geliştiricinin makineye yüklenebilir.

## <a name="provide-guidance-with-library-packages"></a>Kitaplık paketleriyle rehberlik

NuGet üzerinde .NET geliştiricileri için kullanılabilen zengin kitaplıkları vardır.
Bazı Microsoft bu geliyor, bazı üçüncü taraf şirketlerden ve diğer topluluk üyelerinin ve destekledikleri. Geliştiriciler bu kitaplıkları ile başarılı olduğunda bu kitaplıklar, daha fazla benimsenmesi ve daha yüksek incelemeleri alın.

Belgeleri sağlamanın yanı sıra Çözümleyicileri ve yaygın bir yanlış kullanımları kitaplığınızın bulun ve kod düzeltmeleri sağlayabilir. Bu anlık düzeltmeler, geliştiricilerin daha hızlı bir şekilde başarılı yardımcı olur. 

Çözümleyiciler paketleyebilir ve kitaplığınızı NuGet ile kodu düzeltir. Bu senaryoda, NuGet paketinizi yükleyen her geliştiricinin Çözümleyicisi paketi de yüklenir. Kitaplığınızı kullanan tüm geliştiriciler hemen Kılavuzu takımınızdan biçiminde hataları ve önerilen düzeltmeler hakkında anında geri bildirim alırsınız.

## <a name="provide-general-guidance"></a>Genel rehberlik

.NET Geliştirici topluluğu iyi çalışma deneyimi desenleri ve en iyi önlenmesini desenleri algıladı. Çeşitli topluluk üyeleri bu önerilen desenlerinin zorunlu Çözümleyicileri oluşturdunuz. Size daha fazla bilgi edinin olarak da her zaman yeni fikirler yer yoktur.

Bu çözümleyici yüklenebilir [Visual Studio Market](https://marketplace.visualstudio.com/vs) ve Visual Studio kullanan geliştiriciler tarafından indirilir. Yeni dil ve platform gelenlere kabul edilen uygulamaları hızlı bir şekilde öğrenin ve daha önce .NET YOLCULUĞUNA üretken olun. Bunlar daha yaygın kullanılan haline topluluk bu yöntemler devralır.

## <a name="next-steps"></a>Sonraki adımlar

.NET derleyici Platformu SDK'sı, kod oluşturma, analiz ve yeniden düzenleme için en son dil nesne modellerini içerir. Bu bölüm .NET derleyici Platformu SDK'sı kavramsal bir genel bakış sağlar. Hızlı başlangıçlar, örnekler ve öğreticiler bölümlerde daha ayrıntılı bilgi bulunabilir.

Bu beş konulardaki .NET derleyici Platformu SDK'sı kavramları hakkında daha fazla bilgi edinebilirsiniz:

 - [Söz dizimi görselleştiricisi ile kod bulma](syntax-visualizer.md)
 - [Derleyici API modelini anlama](compiler-api-model.md)
 - [Söz dizimi ile çalışma](work-with-syntax.md)
 - [Semantik ile çalışma](work-with-semantics.md)
 - [Bir çalışma alanı ile çalışma](work-with-workspace.md)
 
Başlamak için yüklemeniz gerekecektir **.NET derleyici Platformu SDK'sı**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
