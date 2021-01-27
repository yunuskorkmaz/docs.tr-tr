---
title: .NET Compiler Platform SDK anlam modeliyle çalışma
description: Bu genel bakışta, kodunuzun anlam modelini anlamak ve işlemek için kullandığınız tür hakkında bilgi sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: f0d254045a168f82888c5cc77a34f194a68aed0e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899132"
---
# <a name="work-with-semantics"></a>Semantik ile çalışma

[Sözdizimi ağaçları](work-with-syntax.md) , kaynak kodunun sözlü ve sözdizimsel yapısını temsil eder. Bu bilgilerin tek başına, kaynaktaki tüm bildirimleri ve mantığı tanımlamak için yeterli olmasına rağmen, ne başvurulduğunu belirlemek için yeterli bilgi yok. Bir ad şunları temsil edebilir:

- bir tür
- bir alan
- bir yöntem 
- Yerel bir değişken

Bunların her biri benzersiz bir şekilde farklı olsa da, hangi tanımlayıcının gerçekten başvurduğu, genellikle dil kurallarının derinlemesine bir şekilde anlaşılmasına ihtiyaç duyar.

Kaynak kodunda temsil edilen program öğeleri vardır ve programlar, derleme dosyalarında paketlenmiş daha önceden derlenen kitaplıklara de başvurabilir. Kaynak kodu olmasa da hiçbir sözdizimi düğümü veya ağacı derlemeler için kullanılabilir olmadığından, programlar bunların içindeki öğelere başvurabilirler.

Bu görevler için **anlam modeli** gerekir.

Kaynak kodun sözdizimsel modelinin yanı sıra, bir anlam modeli, dil kurallarını kapsüller, bu da, başvurulan doğru program öğesiyle tanımlayıcılarla doğru bir şekilde eşleşmenin kolay bir yolunu sunar.

## <a name="compilation"></a>Derleme

Derleme, tüm derleme başvurularını, derleyici seçeneklerini ve kaynak dosyaları içeren bir C# veya Visual Basic programı derlemek için gereken her şeyin bir gösterimidir.

Tüm bu bilgiler tek bir yerde olduğundan, kaynak kodda bulunan öğeler daha ayrıntılı olarak açıklanabilir. Derleme, belirtilen her tür, üye veya değişkeni bir sembol olarak temsil eder. Derleme, kaynak kodda belirtilen veya bir derlemeden meta veriler olarak içeri aktarılan sembolleri bulmanıza ve ilişkilendirmede yardımcı olan çeşitli yöntemler içerir.

Sözdizimi ağaçlarına benzer şekilde derlemeler sabittir. Bir derleme oluşturduktan sonra, sizin tarafınızdan veya sizinle paylaştığınız başka bir kişi tarafından değiştirilemez. Bununla birlikte, mevcut bir derlemeden yeni bir derleme oluşturabilir ve bunu yaptığınız gibi bir değişiklik belirtebilirsiniz. Örneğin, var olan bir derleme için her şekilde aynı olan bir derleme oluşturabilirsiniz, ancak ek bir kaynak dosya veya derleme başvurusu içerebilir.

## <a name="symbols"></a>Simgeleri

Bir sembol, kaynak kodu tarafından tanımlanan veya bir derlemeden meta veri olarak içeri aktarılan ayrı bir öğeyi temsil eder. Her ad alanı, tür, yöntem, özellik, alan, olay, parametre veya yerel değişken bir sembol ile temsil edilir.

Türdeki çeşitli yöntemler ve özellikler, <xref:Microsoft.CodeAnalysis.Compilation> sembolleri bulmanıza yardımcı olur. Örneğin, tanımlanmış bir tür için ortak meta veri adıyla bir simge bulabilirsiniz. Tüm sembol tablosuna, genel ad alanı tarafından kök olarak belirtilen bir sembol ağacı olarak da erişebilirsiniz.

Semboller ayrıca, derleyicinin diğer başvurulan semboller gibi kaynak veya meta verilerden belirlediği ek bilgileri de içerir. Her bir sembol türü, ' den türetilen ayrı bir arabirim tarafından temsil edilir <xref:Microsoft.CodeAnalysis.ISymbol> ve derleyicinin topladığı bilgileri ayrıntılarıyla açıklayan kendi yöntemleri ve özellikleri vardır. Bu özelliklerin birçoğu, diğer simgelere doğrudan başvurur. Örneğin, özelliği, <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> yöntemin döndürdüğü gerçek tür sembolünü söyler.

Semboller, kaynak kodu ve meta veriler arasında ad alanları, türler ve üyelerin ortak bir gösterimini sunar. Örneğin, kaynak kodda belirtilen bir yöntem ve meta verilerden içeri aktarılan bir yöntem <xref:Microsoft.CodeAnalysis.IMethodSymbol> , aynı özelliklerle bir ile temsil edilir.

Semboller, API tarafından temsil edildiği gibi CLR türü sistemine benzerdir <xref:System.Reflection> , ancak yalnızca daha fazla türden daha fazla modelleyerek daha hızlıdır. Ad alanları, yerel değişkenler ve Etiketler tüm sembollerdir. Ayrıca, semboller CLR kavramlarını değil, dil kavramlarının bir gösterimidir. Çok sayıda çakışma vardır ancak birçok anlamlı ayrımda vardır. Örneğin, C# veya Visual Basic bir yineleyici yöntemi tek bir sembolüdür. Ancak, yineleyici yöntemi CLR meta verilerine çevrildiğinde, bir tür ve birden çok yöntem olur.

## <a name="semantic-model"></a>Anlamsal model

Anlam modeli, tek bir kaynak dosya için tüm anlam bilgilerini temsil eder. Aşağıdakileri öğrenmek için kullanabilirsiniz:

- Kaynakta belirli bir konumda başvurulan semboller.
- Herhangi bir ifadenin sonuç türü.
- Hata ve uyarı olan tüm Tanılamalar.
- Değişkenlerin kaynak bölgeler içinde ve dışında nasıl akar.
- Daha belirgin soruların yanıtları.
