---
title: .NET derleyici Platformu SDK'sı anlam modeli ile çalışma
description: Bu genel bakışta anlamak ve kodunuzun anlam modeli kullandığınız türünün bir anlayış sağlar.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: cf34e2ab9688325f58cb54755db4142a883fca77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706643"
---
# <a name="work-with-semantics"></a>Semantik ile çalışma

[Sözdizimi ağacı](work-with-syntax.md) kaynak kodu sözcük ve söz dizimi yapısını temsil eder. Bu bilgiler yalnızca tüm bildirimlerinin ve kaynak mantığı tanımlamak için yeterli olsa da, hangi başvurulan belirlemek için yeterli bilgi değil. Bir ad temsil edebilir:

- bir türü
- Bir alan
- bir yöntemi
- bir yerel değişken

Her birinde benzersiz bir şekilde farklı olmasına karşın, hangisinin belirleyen bir tanımlayıcı gerçekten genellikle gerektirir derin bir anlayış dil kuralları ifade eder. 

Kaynak kodunda temsil program öğelerini vardır ve programları daha önce derlenmiş kitaplıkları, derleme dosyalarında paketlenmiş de başvurabilirsiniz. Kaynak kodu yok ve bu nedenle hiçbir sözdizimi düğümü veya ağaçları derlemeler için kullanılabilir, ancak program içinde öğeleri yine de başvurabilir.

Bu görevler için gereksinim duyduğunuz **anlam modeli**.

Kaynak kodunun sözdizimsel modelinin yanı sıra bir anlam modeli doğru tanımlayıcıları başvurulan doğru programı öğeyle eşleşmesi için kolay bir yol vererek dil kuralları kapsüller.

## <a name="compilation"></a>Derleme

Derlemek için gereken her şeyi gösterimi bir derleme ise bir C# veya Visual Basic programı, tüm derleme başvuruları, derleyici seçenekleri ve kaynak dosyaları içerir. 

Bu bilgileri tek bir yerde olduğu için kaynak kodunda içerilen öğelerin daha ayrıntılı olarak açıklanabilir. Derleme her bildirilen tür, üye veya değişken bir sembol temsil eder. Yardımcı yöntemler çeşitli derleme içeren bulun ve ya da kaynak kodunda bildirilen veya bir derlemenin meta verilerini içe simgeleri ilişkilendirebilirsiniz.

Benzer şekilde bir söz dizimi ağacı, derlemeleri sabittir. Bir derleme oluşturduktan sonra siz veya başkaları ile paylaşımı tarafından değiştirilemez. Ancak, bir değişiklik belirten bunu gibi mevcut bir derlemeden yeni bir derleme oluşturabilirsiniz. Örneğin, bir ek kaynak dosyası veya bütünleştirilmiş kod başvurusu içerebilir dışında aynı olan her bir şekilde mevcut bir derleme, derleme oluşturabilirsiniz.

## <a name="symbols"></a>Simgeleri

Bir sembol kaynak kodu tarafından bildirilen veya derleme meta verileri olarak içeri aktarılan ayrı bir öğeyi temsil eder. Her ad alanı, türü, yöntem, özellik, alan, olay, parametre veya yerel değişken bir simge ile temsil edilir. 

Çeşitli yöntemleri ve özellikleri <xref:Microsoft.CodeAnalysis.Compilation> yazın sembolleri bulmasına yardımcı olur. Örneğin, bir sembol için bildirilen bir tür ortak meta veriler adıyla bulabilirsiniz. Tüm sembol tablosu simgeleri genel ad alanı tarafından kök erişim izni verilmiş bir ağaç olarak da erişebilirsiniz.

Simgeler, ayrıca derleyicinin kaynak ya da diğer başvurulan semboller gibi meta verileri belirleyen ek bilgiler içermektedir. Sembol her tür türetilen ayrı bir arabirim tarafından temsil edilen <xref:Microsoft.CodeAnalysis.ISymbol>, her biri kendi yöntemlerini ve özelliklerini derleyici topladığınız bilgileri gerçekleşen. Bu özelliklerin çoğu, doğrudan diğer semboller başvurusu. Örneğin, <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> özelliği bildirir, yöntem bildiriminde başvuran gerçek tür simgesi.

Semboller ad alanları, türler ve üyeler, kaynak kodu ve meta verileri arasında ortak bir gösterimini sunar. Örneğin, kaynak kodunda bildirilen bir yöntemi ve meta verileri içeri aktarılan bir yöntemi her ikisi tarafından temsil edilir bir <xref:Microsoft.CodeAnalysis.IMethodSymbol> aynı özelliklere sahip.

Semboller tarafından temsil edilen CLR tür sistemine kavramsal olarak benzer <xref:System.Reflection> API henüz bunlar daha fazlasını türleri modellemek, daha zengin. Ad alanları, yerel değişkenleri ve etiketleri tüm simgelerdir. Ayrıca, bir dil kavramları, CLR kavramlarını gösterimini simgelerdir. Birçok örtüşme vardır, ancak de birçok anlamlı farklılıklar vardır. Örneğin, bir yineleyici yöntem içinde C# veya Visual Basic tek bir simge. Ancak, yineleyici yöntem CLR meta verileri çevrilir yaparken, bir tür ve birden çok yöntem vardır.

## <a name="semantic-model"></a>Anlam modeli

Anlam modeli, tek bir kaynak dosyası için anlamsal tüm bilgileri temsil eder. Aşağıdakileri keşfetmek için kullanabilirsiniz: 

* Belirli bir kaynak konumda başvurulan simgeler.
* Herhangi bir ifade sonuç türü.
* Tüm tanılama hataları ve Uyarıları.
* Nasıl kaynak bölge içine ve dışına değişkenleri akış.
* Daha fazla kurgusal soruları yanıtlar.
