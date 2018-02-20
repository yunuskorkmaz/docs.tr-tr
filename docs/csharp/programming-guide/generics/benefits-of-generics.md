---
title: "Genel Türlerin Yararları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], benefits
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2eb4aad3d23e459af738045b37ae3f1e8f33da06
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="benefits-of-generics-c-programming-guide"></a>Genel Türlerin Yararları (C# Programlama Kılavuzu)
Genel türler sağlayan ortak dil çalışma zamanı ve C# dili içinde Genelleştirme gerçekleştirilir atama türleri için ve evrensel temel türü tarafından daha önceki sürümlerde bir sınırlama çözüme <xref:System.Object>. Genel bir sınıf oluşturarak, tür kullanımı uyumlu bir koleksiyon oluşturabilirsiniz derleme zamanında.  
  
 Genel olmayan koleksiyon sınıfları kullanma sınırlamaları kullanır kısa bir program yazarak gösterilen <xref:System.Collections.ArrayList> .NET sınıf kitaplığı'ndan koleksiyon sınıfı. Örneği <xref:System.Collections.ArrayList> sınıfı, herhangi bir başvuru veya değer türü depolayabilir.  
  
 [!code-csharp[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_1.cs)]  
  
 Ancak bu kullanışlı bir maliyetlerine neden olur. Eklenen herhangi bir başvuru veya değer türü bir <xref:System.Collections.ArrayList> için örtük olarak başvurmanıza olan <xref:System.Object>. Değer türleri öğeler varsa bunlar listesine eklenir ve bunlar alınırken sarmalanmamış olduğunda bunlar Kutulu gerekir. Atama ve kutulama ve kutudan çıkarma işlemleri performansını düşürebilir; kutulama ve kutudan çıkarma etkisini burada büyük koleksiyon yineleme senaryolarda çok önemli olabilir.  
  
 Diğer derleme zamanı tür denetimi eksiği kısıtlamadır; çünkü bir <xref:System.Collections.ArrayList> her şeye çevirir <xref:System.Object>, istemci kodu bunun gibi bir şey yapmasını önlemek için derleme zamanında bir yolu yoktur:  
  
 [!code-csharp[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_2.cs)]  
  
 Edilebilir ve heterojen bir koleksiyon oluşturuyorsanız, bazen kasıtlı rağmen dizelerini birleştirme ve `ints` tek bir <xref:System.Collections.ArrayList> büyük olasılıkla bir programlama hatası olması ve bu hata çalışma zamanına kadar algılanmaz.  
  
 Sürümlerde 1.0 ve 1.1 C# dilinin, yalnızca kendi türü belirli koleksiyonlar yazarak .NET Framework temel sınıf kitaplığı koleksiyon sınıfları genelleştirilmiş kodda tehlikeleri önlemek. Elbette, böyle bir sınıfın birden fazla veri türü için yeniden kullanılabilir olmadığından, Genelleştirme yararları kaybedebilirsiniz ve sınıfı depolanacak her tür için yeniden gerekebilir.  
  
 Ne <xref:System.Collections.ArrayList> ve benzer diğer sınıflara gerçekten, kullanmayı düşündüğünüz belirli veri türüne bir örnek başına temelinde belirtmek istemci kodu için bir yoldur. Yukarı çevrim için gereksinimini ortadan <xref:System.Object> ve ayrıca derleyici denetimi türü olası yapmak. Diğer bir deyişle, <xref:System.Collections.ArrayList> bir tür parametresi gerekiyor. Tam olarak hangi genel türler sağlamaktır. Genel olarak <xref:System.Collections.Generic.List%601> koleksiyonu içinde <xref:System.Collections.Generic> ad alanı, öğeler koleksiyonuna eklenmeyi aynı işlemi bu benzer:  
  
 [!code-csharp[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/CSharp/benefits-of-generics_3.cs)]  
  
 İçin istemci kodu, yalnızca eklenen sözdizimiyle <xref:System.Collections.Generic.List%601> karşılaştırılan <xref:System.Collections.ArrayList> bildirimi ve örnek oluşturma türü değişkeni. Bu biraz daha kodlama karmaşıklık karşılığında yalnızca daha güvenli olmayan bir liste oluşturabilirsiniz <xref:System.Collections.ArrayList>, ancak Ayrıca önemli ölçüde daha hızlıdır, özellikle liste öğeleri değer türleri olduğunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Kutulama ve Kutudan Çıkarma](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
 [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)  
 [Koleksiyonlar için yönergeler](../../../standard/design-guidelines/guidelines-for-collections.md)   
