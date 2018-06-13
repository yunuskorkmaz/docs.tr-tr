---
title: Yapıları Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 553a6d1d2e922d1683cb5dbe2fa0b525c9b1e37a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326426"
---
# <a name="using-structs-c-programming-guide"></a>Yapıları Kullanma (C# Programlama Kılavuzu)
`struct` Türüdür Hafif nesneler gibi temsil etmek için uygun `Point`, `Rectangle`, ve `Color`. Bir noktası olarak temsil eden yalnızca olarak uygun olmasına rağmen bir [sınıfı](../../../csharp/language-reference/keywords/class.md) ile [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), [yapısı](../../../csharp/language-reference/keywords/struct.md) bazı senaryolarda daha etkili olabilir. Örneğin, bir dizi 1000 bildirirseniz `Point` nesneleri, ek bellek ayırır her nesneye başvuran; bu durumda, yapı daha ucuz olabilir. Çünkü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] adlı bir nesne içeren <xref:System.Drawing.Point>, yapı Bu örnekte bunun yerine "CoOrds" adlı.  
  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 Yapı için bir varsayılan (parametresiz) Oluşturucu tanımlamak için bir hata var. Ayrıca bir örnek alanındaki yapısı gövdesindeki başlatmak için hatadır. Parametreli Oluşturucu örtük, varsayılan oluşturucu, yalnızca kullanarak dışarıdan erişilebilir Yapı üyeleri başlatabilirsiniz bir [Başlatıcı nesne](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), veya yapı bildirilmiş sonra tek tek üyelere erişme. Herhangi bir özel veya aksi halde erişilemez üye özel oluşturucular kullanılmasını gerektirir.
  
 Yapı nesnesini kullanarak oluşturduğunuzda [yeni](../../../csharp/language-reference/keywords/new.md) işleci, oluşturulan ve uygun oluşturucuyu göre adlandırılır [Oluşturucusu'nın imza](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Sınıfları kullanmadan yapılar oluşturulabilir `new` işleci. Böyle bir durumda ayırma daha verimli hale getirir hiçbir oluşturucu çağrısı yoktur. Ancak, alanları atanmamış kalır ve tüm alanları başlatılıncaya kadar nesnesi kullanılamıyor. Bu, almak veya otomatik uygulanan özellikler değerlerini ayarlamak için kullanamama içerir.
 
 Varsayılan, parametresiz bir kurucusu kullanarak bir yapı nesne örneği, tüm üyeleri göre atanan kendi [varsayılan değerlerin](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Yapı parametrelere sahip bir oluşturucu yazarken, tüm üyeleri açıkça başlatması gerekir; Aksi durumda bir veya daha fazla üye atanmamış kalır ve derleyici hatası CS0171 oluşturan yapısı kullanılamaz.  
  
 İçin sınıflar olarak yapılar için hiçbir devralma yoktur. Yapı başka bir yapı veya sınıfından devralan ve bir sınıfın temel olamaz. Yapılar, ancak temel sınıfından devralan <xref:System.Object>. Yapı arabirimleri uygulayabilir ve bunu yapar tam olarak sınıflar gibi.  
  
 Using anahtar sözcüğü bir sınıfı bildiremezsiniz `struct`. C# ' ta sınıflar ve yapılar anlamsal olarak farklıdır. Bir başvuru türü olsa da bir sınıf yapı bir değer türü ' dir. Daha fazla bilgi için bkz: [değer türleri](../../../csharp/language-reference/keywords/value-types.md).  
  
 Başvuru türü anlamları gerekmedikçe yapı bunun yerine ilan, küçük bir sınıf daha verimli bir şekilde de sistem tarafından işlenebilir.  
  
## <a name="example-1"></a>Örnek 1  
  
### <a name="description"></a>Açıklama  
 Bu örnekte gösterilmiştir `struct` başlatma hem varsayılan hem de parametreli oluşturucular kullanma.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_2.cs)]  
  
## <a name="example-2"></a>Örnek 2  
  
### <a name="description"></a>Açıklama  
 Bu örnek yapılar için benzersiz bir özelliğini gösterir. Kullanmadan bir CoOrds nesnesi oluşturur `new` işleci. Word değiştirirseniz `struct` sözcüğünün `class`, program derlenmez.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_1.cs)]  
  
 [!code-csharp[csProgGuideObjects#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-structs_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md)
