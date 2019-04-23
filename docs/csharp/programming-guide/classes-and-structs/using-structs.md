---
title: Yapıları - kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: e90280bf6673b21cfe4c8257f71dd0010cdd73a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974876"
---
# <a name="using-structs-c-programming-guide"></a>Yapıları Kullanma (C# Programlama Kılavuzu)
`struct` Türü basit nesneler gibi temsil etmek için uygun olan `Point`, `Rectangle`, ve `Color`. Temsil eden bir noktası olarak yalnızca olarak uygun olmasına rağmen bir [sınıfı](../../../csharp/language-reference/keywords/class.md) ile [Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [yapı](../../../csharp/language-reference/keywords/struct.md) bazı senaryolarda daha verimli olabilir. Örneğin, bir dizi 1000 bildirirseniz `Point` nesneler, ek bellek ayırır her nesneye başvuran; bu durumda, yapı daha ucuz olabilir. Çünkü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] adlı bir nesne içeren <xref:System.Drawing.Point>, yapı Bu örnekte bunun yerine "Coords" adlı.  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Bu yapı için bir varsayılan (parametresiz) kurucu tanımlamak için bir hatadır. Bu da bir yapı gövdesi bir örnek alanı başlatmak için bir hatadır. Harici olarak erişilebilen Yapı üyeleri yalnızca parametreli bir kurucu, örtük, parametresiz oluşturucusu kullanarak başlatabilirsiniz bir [nesne Başlatıcı](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), veya üye ayrı ayrı sonra yapı erişerek bildirilmiş. Herhangi bir özel ya da aksi takdirde erişilemez üye, özel olarak oluşturucular kullanılmasını gerektirir.
  
 Bir yapı kullanarak nesne oluşturduğunuzda [yeni](../../../csharp/language-reference/keywords/new.md) işleci, oluşturulan ve uygun oluşturucuyu göre adlandırılır [oluşturucunun imza](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir `new` işleci. Böyle bir durumda ayırma daha verimli hale getirir hiçbir oluşturucu çağrısı yoktur. Ancak, alanlar atanmamış kalır ve nesnenin tüm alanları başlatılıncaya kadar kullanılamaz. Bu, alma veya ayarlama özellikleri aracılığıyla değerleri yeteneğinin içerir.
 
 Varsayılan, parametresiz bir oluşturucu kullanılarak bir yapı nesnesinin örneğini oluşturma durumunda, tüm üyeleri göre atanır kendi [varsayılan değerler](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Bir yapının parametrelerle bir oluşturucu yazarken, tüm üyeleri açıkça başlatması gerekir; Aksi halde bir veya daha fazla üye atanmamış kalır ve derleyici hatası CS0171 üretme struct kullanılamaz.  
  
 Sınıflar için olduğundan yapılar için hiçbir devralma yoktur. Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Yapılar, ancak temel sınıfından devralmak <xref:System.Object>. Bir yapı arabirimleri gerçekleştiren ve tam olarak sınıflar gibi yapar.  
  
 Using anahtar sözcüğü bir sınıf bildiremezsiniz `struct`. C# dilinde sınıflar ve yapı birimleri anlamsal olarak farklı. Bir sınıf bir başvuru türü olsa da bir yapı bir değer türüdür. Daha fazla bilgi için [değer türleri](../../../csharp/language-reference/keywords/value-types.md).  
  
 Başvuru türü semantiği gerekmedikçe, bir yapı bunun yerine bildirmek, küçük bir sınıf daha verimli bir şekilde de sistem tarafından işlenebilir.  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Bu örnek gösterir `struct` hem varsayılan hem de parametreli oluşturucuları kullanarak başlatma.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Bu örnekte, yapılar için benzersiz bir özellik gösterilmektedir. Kullanmadan bir Coords nesnesi oluşturur `new` işleci. Word değiştirirseniz `struct` sözcüğünün `class`, program derlenmez.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)
