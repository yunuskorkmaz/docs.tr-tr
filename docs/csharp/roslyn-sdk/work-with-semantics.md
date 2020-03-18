---
title: .NET Derleyici Platformu SDK semantik modeli ile çalışma
description: Bu genel bakış, kodunuzu anlamak ve işlemek için kullandığınız türün anlaşılmasını sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 8575988cd98a4c0ba3f24107788f065f7472f55d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156941"
---
# <a name="work-with-semantics"></a>Semantik ile çalışma

[Sözdizimi ağaçları](work-with-syntax.md) kaynak kodun sözlü ve sözdizimi yapısını temsil ediyor. Bu bilgiler tek başına kaynaktaki tüm bildirimleri ve mantığı açıklamak için yeterli olsa da, başvurulan şeyi tanımlamak için yeterli bilgi değildir. Bir ad şu şekilde temsil edilebilir:

- bir tür
- bir alan
- bir yöntem 
- yerel bir değişken

Bunların her biri benzersiz olarak farklı olsa da, tanımlayıcının gerçekte hangisini ifade ettiğini belirlemek genellikle dil kurallarının derin bir şekilde anlaşılmasını gerektirir.

Kaynak kodunda temsil edilen program öğeleri vardır ve programlar derleme dosyalarında paketlenmiş daha önce derlenmiş kitaplıklara da başvurabilir. Kaynak kodu olmamasına ve bu nedenle sözdizimi düğümleri veya ağaçlar kullanılamamasına rağmen, programlar yine de içlerindeki öğelere başvurabilir.

Bu görevler için **Anlamsal modele**ihtiyacınız var.

Kaynak kodun sözdizimi modeline ek olarak, anlamsal bir model dil kurallarını kapsüller ve tanımlayıcıları başvurulan doğru program öğesiyle doğru eşleştirmenin kolay bir yolunu verir.

## <a name="compilation"></a>Derleme

Derleme, tüm derleme başvurularını, derleyici seçeneklerini ve kaynak dosyalarını içeren bir C# veya Visual Basic programını derlemek için gereken her şeyin bir temsilidir.

Tüm bu bilgiler tek bir yerde olduğundan, kaynak kodunda bulunan öğeler daha ayrıntılı olarak açıklanabilir. Derleme, bildirilen her türü, üyeyi veya değişkeni bir sembol olarak temsil eder. Derleme, kaynak kodda bildirilen veya bir derlemeden meta veri olarak aktarılan sembolleri bulmanıza ve ilişkilendirmenize yardımcı olan çeşitli yöntemler içerir.

Sözdizimi ağaçlarına benzer şekilde, derlemeler değişmezdir. Bir derleme oluşturduktan sonra, bu derlemeyi siz veya paylaştığınız başka biri tarafından değiştirilemez. Ancak, varolan bir derlemeden, siz bunu yaparken bir değişiklik belirterek yeni bir derleme oluşturabilirsiniz. Örneğin, ek bir kaynak dosyası veya derleme başvurusu içerebileceği dışında, varolan derlemeyle her yönden aynı olan bir derleme oluşturabilirsiniz.

## <a name="symbols"></a>Simgeleri

Sembol, kaynak kodu tarafından bildirilen veya bir derlemeden meta veri olarak alınan farklı bir öğeyi temsil eder. Her ad alanı, tür, yöntem, özellik, alan, olay, parametre veya yerel değişken bir sembolle temsil edilir.

<xref:Microsoft.CodeAnalysis.Compilation> Türdeki çeşitli yöntemler ve özellikler, sembolleri bulmanıza yardımcı olur. Örneğin, ortak meta veri adına göre bildirilen bir tür için bir sembol bulabilirsiniz. Ayrıca, tüm sembol tablosuna genel ad alanı tarafından köksünün kazınan semboller ağacı olarak da erişebilirsiniz.

Semboller ayrıca derleyicinin kaynaktan veya meta verilerden belirlediği diğer başvurulan simgeler gibi ek bilgiler de içerir. Her sembol <xref:Microsoft.CodeAnalysis.ISymbol>türü, derleyicinin topladığı bilgileri ayrıntılı olarak açıklayan kendi yöntemleri ve özellikleriyle, her biri türetilen ayrı bir arabirimle temsil edilir. Bu özelliklerin çoğu doğrudan diğer sembollere başvurur. Örneğin, <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> özellik, yöntem bildiriminin başvurulettiği gerçek tür simgesini söyler.

Semboller, kaynak kodu ve meta veriler arasında ad alanlarının, türlerinin ve üyelerin ortak bir temsilini sunar. Örneğin, kaynak kodunda bildirilen bir yöntem ve meta verilerden alınan bir yöntemin her ikisi de aynı özelliklere sahip bir yöntemtarafından <xref:Microsoft.CodeAnalysis.IMethodSymbol> temsil edilir.

Semboller api tarafından <xref:System.Reflection> temsil edildiği gibi CLR tip sistemine kavram olarak benzer, ancak onlar sadece türleri daha model açısından daha zengindir. Ad alanları, yerel değişkenler ve etiketlerin tümü sembollerdir. Buna ek olarak, semboller dil kavramlarının bir temsilidir, CLR kavramlarının değil. Bir çok çakışma var, ama birçok anlamlı ayrımlar da vardır. Örneğin, C# veya Visual Basic'teki bir yineleyici yöntemi tek bir semboldür. Ancak, yineleyici yöntemi CLR meta verilerine çevrildiğinde, bu bir tür ve birden çok yöntemdir.

## <a name="semantic-model"></a>Anlamsal model

Semantik bir model, tek bir kaynak dosyasının tüm anlamsal bilgilerini temsil eder. Aşağıdakileri keşfetmek için kullanabilirsiniz:

- Kaynakta belirli bir konumda başvurulan semboller.
- Herhangi bir ifadenin ortaya çıkan türü.
- Hatalar ve uyarılar olan tüm tanılama.
- Değişkenlerin kaynak bölgelerine girip nasıl aktığı.
- Daha spekülatif soruların cevapları.
