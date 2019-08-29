---
title: .NET Compiler Platform SDK anlam modeliyle çalışma
description: Bu genel bakışta, kodunuzun anlam modelini anlamak ve işlemek için kullandığınız tür hakkında bilgi sağlanır.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: c594447bb553f488d60fe83900e2f141608b570f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105662"
---
# <a name="work-with-semantics"></a>Semantik ile çalışma

[Sözdizimi ağaçları](work-with-syntax.md) , kaynak kodunun sözlü ve sözdizimsel yapısını temsil eder. Bu bilgilerin tek başına, kaynaktaki tüm bildirimleri ve mantığı tanımlamak için yeterli olmasına rağmen, ne başvurulduğunu belirlemek için yeterli bilgi yok. Bir ad şunları temsil edebilir:

- bir tür
- bir alan
- bir yöntemi
- Yerel bir değişken

Bunların her biri benzersiz bir şekilde farklı olsa da, hangi tanımlayıcının gerçekten başvurduğu, genellikle dil kurallarının derinlemesine bir şekilde anlaşılmasına ihtiyaç duyar. 

Kaynak kodunda temsil edilen program öğeleri vardır ve programlar, derleme dosyalarında paketlenmiş daha önceden derlenen kitaplıklara de başvurabilir. Kaynak kodu olmasa da hiçbir sözdizimi düğümü veya ağacı derlemeler için kullanılabilir olmadığından, programlar bunların içindeki öğelere başvurabilirler.

Bu görevler için **anlam modeli**gerekir.

Kaynak kodun sözdizimsel modelinin yanı sıra, bir anlam modeli, dil kurallarını kapsüller, bu da, başvurulan doğru program öğesiyle tanımlayıcılarla doğru bir şekilde eşleşmenin kolay bir yolunu sunar.

## <a name="compilation"></a>Derleme

Derleme, tüm derleme başvurularını, derleyici seçeneklerini ve kaynak dosyaları C# içeren bir veya Visual Basic programı derlemek için gereken her şeyin bir gösterimidir. 

Tüm bu bilgiler tek bir yerde olduğundan, kaynak kodda bulunan öğeler daha ayrıntılı olarak açıklanabilir. Derleme, belirtilen her tür, üye veya değişkeni bir sembol olarak temsil eder. Derleme, kaynak kodda belirtilen veya bir derlemeden meta veriler olarak içeri aktarılan sembolleri bulmanıza ve ilişkilendirmede yardımcı olan çeşitli yöntemler içerir.

Sözdizimi ağaçlarına benzer şekilde derlemeler sabittir. Bir derleme oluşturduktan sonra, sizin tarafınızdan veya sizinle paylaştığınız başka bir kişi tarafından değiştirilemez. Bununla birlikte, mevcut bir derlemeden yeni bir derleme oluşturabilir ve bunu yaptığınız gibi bir değişiklik belirtebilirsiniz. Örneğin, var olan bir derleme için her şekilde aynı olan bir derleme oluşturabilirsiniz, ancak ek bir kaynak dosya veya derleme başvurusu içerebilir.

## <a name="symbols"></a>Simgeleri

Bir sembol, kaynak kodu tarafından tanımlanan veya bir derlemeden meta veri olarak içeri aktarılan ayrı bir öğeyi temsil eder. Her ad alanı, tür, yöntem, özellik, alan, olay, parametre veya yerel değişken bir sembol ile temsil edilir. 

<xref:Microsoft.CodeAnalysis.Compilation> Türdeki çeşitli yöntemler ve özellikler, sembolleri bulmanıza yardımcı olur. Örneğin, tanımlanmış bir tür için ortak meta veri adıyla bir simge bulabilirsiniz. Tüm sembol tablosuna, genel ad alanı tarafından kök olarak belirtilen bir sembol ağacı olarak da erişebilirsiniz.

Semboller ayrıca, derleyicinin diğer başvurulan semboller gibi kaynak veya meta verilerden belirlediği ek bilgileri de içerir. Her bir sembol türü, ' den <xref:Microsoft.CodeAnalysis.ISymbol>türetilen ayrı bir arabirim tarafından temsil edilir ve derleyicinin topladığı bilgileri ayrıntılarıyla açıklayan kendi yöntemleri ve özellikleri vardır. Bu özelliklerin birçoğu, diğer simgelere doğrudan başvurur. Örneğin, <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> özelliği, yöntem bildiriminin başvurduğu gerçek tür sembolünü söyler.

Semboller, kaynak kodu ve meta veriler arasında ad alanları, türler ve üyelerin ortak bir gösterimini sunar. Örneğin, kaynak kodda belirtilen bir yöntem ve meta verilerden içeri aktarılan bir yöntem, aynı özelliklerle bir <xref:Microsoft.CodeAnalysis.IMethodSymbol> ile temsil edilir.

Semboller, <xref:System.Reflection> API tarafından temsil edildiği gibi CLR türü sistemine benzerdir, ancak yalnızca daha fazla türden daha fazla modelleyerek daha hızlıdır. Ad alanları, yerel değişkenler ve Etiketler tüm sembollerdir. Ayrıca, semboller CLR kavramlarını değil, dil kavramlarının bir gösterimidir. Çok sayıda çakışma vardır ancak birçok anlamlı ayrımda vardır. Örneğin, C# veya Visual Basic bir yineleyici yöntemi tek bir sembolüdür. Ancak, yineleyici yöntemi CLR meta verilerine çevrildiğinde, bir tür ve birden çok yöntem olur.

## <a name="semantic-model"></a>Anlam modeli

Anlam modeli, tek bir kaynak dosya için tüm anlam bilgilerini temsil eder. Aşağıdakileri öğrenmek için kullanabilirsiniz: 

- Kaynakta belirli bir konumda başvurulan semboller.
- Herhangi bir ifadenin sonuç türü.
- Hata ve uyarı olan tüm Tanılamalar.
- Değişkenlerin kaynak bölgeler içinde ve dışında nasıl akar.
- Daha belirgin soruların yanıtları.
