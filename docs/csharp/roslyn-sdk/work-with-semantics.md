---
title: .NET derleme Platform SDK anlam modeli ile çalışma
description: Bu genel bakışta anlamak ve kodunuzun anlam modeli işlemek için kullandığınız türünün bir anlayış sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: cf34e2ab9688325f58cb54755db4142a883fca77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="work-with-semantics"></a>Semantiği ile çalışma

[Sözdizimi ağacı](work-with-syntax.md) kaynak kod sözcük ve söz dizimi yapısını temsil eder. Bu bilgileri tek başına tüm bildirimler ve kaynak mantığında açıklamak için yeterli olsa da, ne başvurulan belirlemek için yeterli bilgi değil. Bir ad gösterebilir:

- bir türü
- Bir alan
- bir yöntemi
- yerel bir değişken

Bunların her biri benzersiz olarak farklı olmasına rağmen hangisinin belirleme tanımlayıcı gerçekte genellikle gerektirir dil kurallarına derin bir anlayış ifade eder. 

Kaynak kodunda temsil program öğeler vardır ve programlar da derleme dosyalarında paketli önceden derlenmiş kitaplıklarına başvuruda bulunabilir. Hiçbir kaynak kodu ve bu nedenle söz dizimi düğüm veya ağaçları, derlemeler için kullanılabilir, ancak programlar hala içerdikleri öğelerine başvurabilir.

Bu görevler için gereksinim duyduğunuz **anlam modeli**.

Kaynak kodu söz dizimi modelinin yanı sıra bir anlam modeli doğru tanımlayıcıları başvurulan doğru bir program öğesi ile eşleşmesi için kolay bir yol vermiş dil kurallarına yalıtır.

## <a name="compilation"></a>Derleme

Bir derleme bir C# veya tüm derleme başvurularını, derleyici seçenekleri ve kaynak dosyaları içeren Visual Basic programı derlemek için gereken her şeyi gösterimidir. 

Bu bilgileri tek bir yerde olduğundan, kaynak kodunda bulunan öğeleri daha ayrıntılı olarak açıklanabilir. Derleme her bildirilen türü, üye veya değişkeni bir simge temsil eder. Derleme çeşitli yardımcı yöntemler içerir bulmak ve ya da kaynak kodunda bildirilen veya silinmiş bir derlemenin meta verilerini içe sembolleri ilişkilendirebilirsiniz.

Sözdizimi ağacı, derlemeleri değişmez benzerdir. Bir derleme oluşturduktan sonra siz veya başkalarının size ile paylaşmayı tarafından değiştirilemez. Ancak, bir değişiklik belirten bunu gibi mevcut bir derlemeden yeni bir derleme oluşturabilirsiniz. Örneğin, bir ek kaynak dosya veya derleme başvurusu içerebilir dışında her şekilde var olan bir derleme aynıdır bir derleme oluşturabilirsiniz.

## <a name="symbols"></a>Simgeleri

Bir simge kaynak kodu tarafından bildirilen veya derleme meta veri olarak içe ayrı bir öğeyi temsil eder. Her ad alanı, tür, yöntemi, özelliği, alan, olay, parametre veya yerel değişken bir simge ile temsil edilir. 

Çeşitli yöntemleri ve özellikleri <xref:Microsoft.CodeAnalysis.Compilation> yazın simgeleri bulmasına yardımcı olur. Örneğin, bir simge için bildirilen bir tür, ortak bir meta veri adına göre bulabilirsiniz. Genel ad alanı tarafından kökü simgelerin ağacı tüm simge tablosunu de erişebilirsiniz.

Semboller Ayrıca kaynak ya da diğer başvurulan simgeler gibi meta veriler derleyici belirler ek bilgileri içerir. Simgenin her tür türetilmiş ayrı bir arabirim tarafından temsil edilen <xref:Microsoft.CodeAnalysis.ISymbol>, her biri kendi yöntemleri ve özellikleri derleyici topladığınız bilgileri ayrıntılı sahip. Bu özelliklerin çoğu doğrudan diğer semboller başvurusu. Örneğin, <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> özelliği yöntem bildirimi başvuran gerçek tür simgesi bildirir.

Simgeler ad alanlarını, türleri ve üyeleri, kaynak kodu ve meta verileri arasında ortak bir gösterimini sunar. Örneğin, kaynak kodunda bildirildi bir yöntem ve meta verilerini içeri aktarılmış bir yöntem her ikisi de belirtilmiştir bir <xref:Microsoft.CodeAnalysis.IMethodSymbol> aynı özelliklere sahip.

Simgeler kavram olarak tarafından temsil edilen CLR türü sistemine benzer <xref:System.Reflection> daha fazlasını türleri model API henüz daha zengin bir seçenektir. Ad alanları, yerel değişkenleri ve etiketleri tüm simgelerdir. Ayrıca, bir dil kavramları, CLR kavramlarını gösterimini simgelerdir. Birçok örtüşme yoktur, ancak birçok anlamlı farklılıklar da vardır. Örneğin, bir yineleyici C# veya Visual Basic tek bir simge yöntemidir. Ancak, yineleyici yöntemi CLR meta verileri çevrildiğinde bir türü ve birden çok yöntem gerekir.

## <a name="semantic-model"></a>Anlam modeli

Anlam modeli için tek bir kaynak dosyası anlamsal tüm bilgilerini temsil eder. Aşağıdakileri keşfetmek için kullanabilirsiniz: 

* Belirli bir kaynak konumda başvurulan simgeler.
* Herhangi bir ifade sonuç türü.
* Hataları ve Uyarıları olan tüm tanılama.
* Nasıl değişkenleri kaynak bölgeler ve bu moddan akışı.
* Daha fazla kurgusal soruların yanıtları.
