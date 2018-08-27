---
title: Yapıları Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 553a6d1d2e922d1683cb5dbe2fa0b525c9b1e37a
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925336"
---
# <a name="using-structs-c-programming-guide"></a>Yapıları Kullanma (C# Programlama Kılavuzu)
`struct` Türü basit nesneler gibi temsil etmek için uygun olan `Point`, `Rectangle`, ve `Color`. Temsil eden bir noktası olarak yalnızca olarak uygun olmasına rağmen bir [sınıfı](../../../csharp/language-reference/keywords/class.md) ile [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [yapı](../../../csharp/language-reference/keywords/struct.md) bazı senaryolarda daha verimli olabilir. Örneğin, bir dizi 1000 bildirirseniz `Point` nesneler, ek bellek ayırır her nesneye başvuran; bu durumda, yapı daha ucuz olabilir. Çünkü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] adlı bir nesne içeren <xref:System.Drawing.Point>, yapı Bu örnekte bunun yerine "CoOrds" adlı.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Bu yapı için bir varsayılan (parametresiz) kurucu tanımlamak için bir hatadır. Bu da bir yapı gövdesi bir örnek alanı başlatmak için bir hatadır. Harici olarak erişilebilen Yapı üyeleri yalnızca parametreli bir kurucu, örtük, varsayılan oluşturucu kullanarak başlatabilirsiniz bir [nesne Başlatıcı](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), veya struct bildirildikten sonra tarafından ayrı ayrı üyeleri erişme. Herhangi bir özel ya da aksi takdirde erişilemez üye, özel olarak oluşturucular kullanılmasını gerektirir.
  
 Bir yapı kullanarak nesne oluşturduğunuzda [yeni](../../../csharp/language-reference/keywords/new.md) işleci, oluşturulan ve uygun oluşturucuyu göre adlandırılır [oluşturucunun imza](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir `new` işleci. Böyle bir durumda ayırma daha verimli hale getirir hiçbir oluşturucu çağrısı yoktur. Ancak, alanlar atanmamış kalır ve nesnenin tüm alanları başlatılıncaya kadar kullanılamaz. Bu almak veya otomatik uygulanan özelliklerin değerlerini ayarlamak için yükleyememesine içerir.
 
 Varsayılan, parametresiz bir oluşturucu kullanılarak bir yapı nesnesinin örneğini oluşturma durumunda, tüm üyeleri göre atanır kendi [varsayılan değerler](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Bir yapının parametrelerle bir oluşturucu yazarken, tüm üyeleri açıkça başlatması gerekir; Aksi halde bir veya daha fazla üye atanmamış kalır ve derleyici hatası CS0171 üretme struct kullanılamaz.  
  
 Sınıflar için olduğundan yapılar için hiçbir devralma yoktur. Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Yapılar, ancak temel sınıfından devralmak <xref:System.Object>. Bir yapı arabirimleri gerçekleştiren ve tam olarak sınıflar gibi yapar.  
  
 Using anahtar sözcüğü bir sınıf bildiremezsiniz `struct`. C# dilinde sınıflar ve yapı birimleri anlamsal olarak farklı. Bir sınıf bir başvuru türü olsa da bir yapı bir değer türüdür. Daha fazla bilgi için [değer türleri](../../../csharp/language-reference/keywords/value-types.md).  
  
 Başvuru türü semantiği gerekmedikçe, bir yapı bunun yerine bildirmek, küçük bir sınıf daha verimli bir şekilde de sistem tarafından işlenebilir.  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Bu örnek gösterir `struct` hem varsayılan hem de parametreli oluşturucuları kullanarak başlatma.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Bu örnekte, yapılar için benzersiz bir özellik gösterilmektedir. Kullanmadan bir CoOrds nesnesi oluşturur `new` işleci. Word değiştirirseniz `struct` sözcüğünün `class`, program derlenmez.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)
