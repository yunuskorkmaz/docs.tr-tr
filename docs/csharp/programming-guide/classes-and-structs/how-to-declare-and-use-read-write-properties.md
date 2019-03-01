---
title: 'Nasıl yapılır: Okuma yazma özellikleri - bildirme ve kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: b4dc9364e64f7ebfd495671b852b98d8f56c80b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969048"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Nasıl yapılır: Okuma yazma özellikleri bildirme ve kullanma (C# Programlama Kılavuzu)
Özellikler, ortak veri üyeleri olmadan bir nesnenin verilere korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskleri kolaylık sağlar. Bu aracılığıyla gerçekleştirilir *erişimcileri*: atayın ve temel alınan veri üyesinden değerleri almak özel yöntemler. [Ayarlamak](../../../csharp/language-reference/keywords/set.md) erişimci veri üyeleri atanmasına olanak sağlar ve [alma](../../../csharp/language-reference/keywords/get.md) erişimci veri üyesi değerler alır.  
  
 Bu örnek, gösterir bir `Person` sınıfı iki özelliğe sahiptir: `Name` (dize) ve `Age` (int). Her iki özellik sağlayan `get` ve `set` kabul edilir şekilde erişimcileri okuma/yazma özellikleri.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte, `Name` ve `Age` özellikleri [genel](../../../csharp/language-reference/keywords/public.md) ve her ikisi de dahil bir `get` ve `set` erişimcisi. Bu, herhangi bir nesne okuma ve yazma bu özellikleri sağlar. Bu bazen ancak erişimcileri biri hariç tutmak için önerilir. Atlama `set` erişimci salt okunur özelliği gibi yapar:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatif olarak, bir erişimci genel olarak kullanıma sunar ancak diğer özel veya korumalı hale getirin. Daha fazla bilgi için [asimetrik erişimci erişilebilirliği](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Bildirilen özellikler sonra sınıfın alanları değilmiş gibi bunlar kullanılabilir. Bu hem alma hem de aşağıdaki deyimleri olduğu gibi bir özelliğin değerini ayarlamak çok doğal bir sözdizimi sağlar:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Bir özelliğin unutmayın `set` yöntemi özel bir `value` değişkeni kullanılabilir. Bu değişken, kullanıcının belirttiğiniz, örneğin değeri içerir:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Artan temiz söz dizimi fark `Age` özelliği bir `Person` nesnesi:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Ayrı varsa `set` ve `get` yöntemler, Özellikler modellemek için kullanılmış, eşdeğer kod şu şekilde görünebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Bu örnekte yöntemi geçersiz kılmışsa:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 Dikkat `ToString` programda açıkça kullanılmaz. Varsayılan olarak tarafından çağrılan `WriteLine` çağırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
