---
title: 'Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: d6a7083e1c0cf0dc5c076a69dee15fc39e234d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Nasıl yapılır: okuma yazma özellikleri (C# programlama Kılavuzu) bildirme ve kullanma
Özellikler, ortak veri üyeleri nesnenin verileri korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri olmadan kolaylık sağlar. Bu aracılığıyla gerçekleştirilir *erişimciler*: atayın ve temel alınan veri üyeden değerleri almak özel yöntemler. [Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci atanması, veri üyelerin sağlar ve [almak](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerlerini alır.  
  
 Bu örnek gösteren bir `Person` iki özelliğe sahip sınıfı: `Name` (dize) ve `Age` (int). Her iki özellik sağlamak `get` ve `set` kabul edilen şekilde erişimciler okuma/yazma özellikleri.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte, `Name` ve `Age` özellikleri [ortak](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi. Bu, bu özellikleri okumasına ve yazmasına herhangi bir nesne sağlar. Bu bazen ancak erişimciler birini dışlamak için önerilir. Atlama `set` erişimci salt okunur özelliği gibi yapar:  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Alternatif olarak, bir erişimci genel olarak kullanıma ancak diğer özel veya korumalı hale getirin. Daha fazla bilgi için bkz: [asimetrik erişimci erişilebilirliğini](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Özellikler bildirilen sonra bunlar sınıfın alanları değilmiş gibi kullanılabilir. Bu hem alma ve aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlama çok doğal bir sözdizimi sağlar:  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Bir özelliğin unutmayın `set` özel bir yöntem `value` değişkeni, kullanılabilir. Bu değişken kullanıcı belirtilen, örneğin değer içeriyor:  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Ayrı varsa `set` ve `get` yöntemleri özellikleri model kullanıldı, eşdeğer kod şuna benzeyebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Bu örnekte, yöntem geçersiz:  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Dikkat `ToString` açıkça programa kullanılmaz. Varsayılan olarak tarafından çağrılan `WriteLine` çağrıları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
