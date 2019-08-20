---
title: 'Nasıl yapılır: Okuma yazma özelliklerini bildirme ve kullanma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 010c3d4c1ae976091b5382f00a982400746f6436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596935"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Nasıl yapılır: Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)
Özellikler, bir nesnenin verilerine korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar. Bu, *erişimciler*aracılığıyla gerçekleştirilir: temel alınan veri üyesine değerler atayan ve alan özel yöntemler. [Set](../../language-reference/keywords/set.md) erişimcisi veri üyelerinin atanmasını sağlar ve [Get](../../language-reference/keywords/get.md) erişimcisi veri üyesi değerlerini alır.  
  
 Bu örnek, iki `Person` özelliği olan bir sınıfı gösterir: `Name` (dize) ve `Age` (int). Her iki özellik `get` de `set` ve erişimcileri sağlar, bu nedenle okuma/yazma özellikleri olarak değerlendirilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte `Name` `Age` , ve özellikleri [geneldir](../../language-reference/keywords/public.md) ve hem hem de `get` `set` erişimcisi içerir. Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına izin verir. Ancak erişimcilerinin birini dışlamak bazen tercih edilir. `set` Erişimci atlanırsa, örneğin, özelliği salt okunurdur:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatif olarak, bir erişimciye genel kullanıma sunabilirsiniz, ancak diğerini özel veya korumalı hale getirebilirsiniz. Daha fazla bilgi için bkz. [asimetrik erişimci erişilebilirliği](./restricting-accessor-accessibility.md).  
  
 Özellikler doğrulandıktan sonra, sınıfının alanları gibi kullanılabilirler. Bu, aşağıdaki deyimlerde olduğu gibi bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimi sağlar:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Bir özellik `set` yönteminde özel `value` bir değişken bulunduğunu unutmayın. Bu değişken, kullanıcının belirttiği değeri içerir, örneğin:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 `Age` Bir`Person` nesne üzerindeki özelliği arttırmadan ilgili Temizleme sözdizimine dikkat edin:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Özellikleri modellemek `set` için `get` ayrı ve Yöntemler kullanılmışsa, eşdeğer kod şöyle görünebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` Yöntemi bu örnekte geçersiz kılınır:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 `ToString` Programda açıkça kullanılmadığına dikkat edin. `WriteLine` Çağrılar tarafından varsayılan olarak çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Sınıflar ve Yapılar](./index.md)
