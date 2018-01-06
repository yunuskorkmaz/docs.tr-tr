---
title: .NET derleme Platform SDK'si (Roslyn API)
description: ".NET kodu, nokta hataları anlamak ve bu hataları düzeltmek için .NET derleyici Platform (Roslyn API'ları olarak da bilinir) SDK kullanmayı öğrenin."
keywords: "roslyn, analyzer, kod düzeltme"
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 8bebb739805f28bdc192aef7678e762d0aa51016
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2018
---
# <a name="the-net-compiler-platform-sdk"></a>.NET derleme Platform SDK'si

Derleyicileri sözdizimi ve bu kodu semantiği doğrulamak uygulama kodunun ayrıntılı bir model oluşturma. Kullanımı bu model kaynak kodunu yürütülebilir çıkışı oluşturmak için. .NET derleme Platform SDK'sı bu modeline erişim sağlar. Giderek, biz tümleşik geliştirme ortamı (IDE) özelliklerini kullanan yeniden düzenleme, IntelliSense, akıllı yeniden adlandır, "tüm başvuruları Bul" ve "Tanıma Git" gibi bizim üretkenliği artırmak için. Kod çözümleme araçları bizim kod kalitesini ve uygulama yapısında yardımcı olmak için kod oluşturucuları geliştirmek için kullanır. Bu araçları akıllı aldıkça, çok daha da fazla uygulama kodu işlemek gibi yalnızca derleyicileri oluşturduğunuz modelinin erişim. Çekirdek Görev Roslyn API'leri budur: siyah kutuları açma ve araçları ve son kullanıcıların bilgi derleyicileri bol içinde paylaşmak izin vererek kodumuza hakkında sahip.
Roslyn, aracılığıyla donuk kaynak kod içinde ve nesne kodu genişletme çevirmenler yerine derleyicileri platformları hale: araç ve uygulama kodu ilgili görevler için kullanabileceğiniz bir API.

## <a name="net-compiler-platform-sdk-concepts"></a>.NET derleme Platform SDK'sı kavramları

.NET derleme Platform SDK'sı odaklanmış kod araçları ve uygulamaları oluşturmak için girişe engel önemli ölçüde azaltır. C# ve VB diller ve C# ve VB etki alanı belirli dillerde katıştırma meta programlama kodu oluşturma ve dönüştürme, etkileşimli kullanımı gibi alanlarda yenilik için birçok fırsatlar yaratır.

.NET derleme Platform SDK'sı oluşturmanıza olanak sağlayan ***çözümleyiciler*** ve ***kod düzeltmeleri*** bulmak ve kodlama hataları düzeltin. ***Çözümleyiciler*** sözdizimi ve kod yapısını anlamak ve düzeltilmesi uygulamalar algılayabilir. ***Kod düzeltmeleri*** çözümleyicileri tarafından bulunan kodlama hataları ele almak için bir veya daha fazla önerilen düzeltmeler sağlar. Genellikle, bir Çözümleyicisi ve ilişkili kodu düzeltmeleri tek bir projede birlikte paketlenmiştir. 

Çözümleyicileri ve kod düzeltmeleri statik çözümleme kod anlamak için kullanın. Bunlar kodu çalıştırmayın ve diğer sınama fayda sağlar. Bunlar Bununla birlikte, hatalar, unmaintanable kodu veya standart kılavuz doğrulama genellikle sağlama yöntemleri çıkışı işaret edebilir.

.NET derleme Platform SDK'sı, tek bir inceleyin ve C# veya Visual Basic codebase anlamanıza olanak sağlayan API kümesi sağlar. Bu tek codebase kullanabileceğinizden çözümleyiciler yazabilir ve sözdizimsel ve anlamsal analiz API'leri .NET derleme Platform SDK tarafından sağlanan yararlanarak kodu daha kolay giderir. Derleyici tarafından yapılan anaysis çoğaltılan büyük görevden serbest, proje veya kitaplık için ortak kodlama hataları bulma ve düzeltme daha odaklı görevini üzerinde odaklanabilirsiniz.

Daha küçük bir avantajı Çözümleyicileri ve kod düzeltmeleri daha küçüktür ve kendi yazdıysanız bunlar projesinde kodu anlamak için codebase daha Visual Studio'da yüklendiğinde çok az bellek kullanır ' dir. Derleyici ve Visual Studio tarafından kullanılan aynı sınıflarını yararlanarak kendi statik çözümleme araçları oluşturabilirsiniz. Bunun anlamı ekibinizin çözümleyiciler kullanabilirsiniz ve IDE'nin performansı belirgin bir etkisi olmadan kod giderir.

Çözümleyicileri ve kod düzeltmeleri yazmak için üç ana senaryo vardır:

1. [*Kodlama standartları takım zorla*](#enforce-team-coding-standards)
1. [*Kitaplık paketleriyle rehberlik sağlar*](#provide-guidance-with-library-packages)
1. [*Genel kodlama rehberlik sağlar*](#provide-general-coding-guidance)

## <a name="enforce-team-coding-standards"></a>Kodlama standartları takım zorla

Birçok ekip kodlama kod incelemeleri diğer takım üyeleri ile aracılığıyla zorlanan standartları vardır. Çözümleyicileri ve kod düzeltmeleri bu işlem çok daha verimli hale getirebilir. Bir geliştirici kendi iş başkalarıyla ekipte paylaşır kod incelemeleri meydana gelir. Daha yeni bir özellik açıklamaları almadan önce tamamlamak için gereken her zaman yatırım yapmış kullanıcılar. Müşterinizle ekibin yöntemler eşleşmeyen alışkanlıklarınıza eklenir ancak hafta gidin.

Bir geliştirici kod yazar gibi çözümleyiciler çalıştırın. Hüseyin, yönergeleri hemen teşvik eden anında geri bildirim alır. Cüneyt, kendisinin prototipi oluşturulurken başlar başlamaz uyumlu kod yazmaya alışkanlıklarınıza oluşturur. Özellik insanlar gözden geçirmek için hazır olduğunda, tüm standart Kılavuzu zorlandı.

Takımlar çözümleyiciler oluşturabilirsiniz ve görünüm yöntemler kodlama takım ihlal en sık kullanılan uygulamalar için kod giderir. Bu standartları zorlamak için her geliştiricinin makinesinde yüklenebilir.

## <a name="provide-guidance-with-library-packages"></a>Kitaplık paketleriyle rehberlik sağlar

Bol miktarda kitaplıkları NuGet üzerinde .NET geliştiricileri için kullanılabilir.
Bazı Microsoft bu geliyor, bazı üçüncü taraf şirketlerden ve diğer topluluk üyeleri ve gönüllüsü. Geliştiricilerin bu kitaplıklarıyla başarılı olduğunda bu kitaplıklar daha fazla benimseme ve daha yüksek incelemeler alın.

Belge sağlamanın yanı sıra, Çözümleyicileri ve bulma ve hatalı yaygın kullanımları kitaplığınızın düzeltmek kod düzeltmeler sağlayabilir. Bu hemen düzeltmeleri daha hızlı başarılı geliştiricilere yardımcı olur. 

Çözümleyiciler paketleyebilirsiniz ve kitaplığınızı NuGet ile kod giderir. Bu senaryoda, NuGet paketini yükleyen her geliştiricinin Çözümleyicisi paketi de yüklenir. Kitaplık kullanan tüm geliştiriciler hemen Kılavuzu, ekibinden anında geri bildirim hataları ve önerilen düzeltmeler biçiminde alır.

## <a name="provide-general-guidance"></a>Genel rehberlik sağlar

.NET Geliştirici topluluğu iyi iş deneyimi desenleri ve en iyi kaçınılması desenleri buldu. Birkaç topluluk üyeleri bu önerilen desenlerinin zorunlu çözümleyiciler oluşturdunuz. Size daha fazla bilgi edinin olarak da her zaman yeni fikirleri yer yoktur.

Bu çözümleyiciler karşıya yüklenebilir [Visual Studio Market'te](https://marketplace.visualstudio.com/vs) ve Visual Studio kullanarak geliştiriciler tarafından indirilir. Yeni gelenlere dili ve platformu için kendi .NET gezisine önceki üretken ve kabul edilen yöntemler hızlıca öğrenin. Bunlar daha yaygın kullanılan hale topluluk bu yöntemler devralır.

## <a name="next-steps"></a>Sonraki adımlar

.NET derleme Platform SDK kod oluşturma, çözümleme ve yeniden düzenleme için en son dil nesne modelleri içerir. Bu bölümde, .NET derleme Platform SDK'sı kavramsal genel bakış sağlar. Daha ayrıntılı bilgi quickstarts, örnekler ve öğreticiler bölümlerde bulunabilir.

Aşağıdaki dört konulardaki .NET derleyici Platform SDK'sı kavramları hakkında daha fazla bilgi edinebilirsiniz:

 - [Derleyici API modelini anlama](compiler-api-model.md)
 - [Söz dizimi ile çalışma](work-with-syntax.md)
 - [Semantik ile çalışma](work-with-semantics.md)
 - [Bir çalışma alanı ile çalışma](work-with-workspace.md)

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
