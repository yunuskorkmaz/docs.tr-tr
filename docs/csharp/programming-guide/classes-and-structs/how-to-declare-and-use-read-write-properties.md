---
title: Okuma yazma özelliklerini bildirme ve kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 2865feb74692e7075c92a9ee2b5cd2a7735a8e62
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971021"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)
Özellikler, bir nesnenin verilerine korumasız, denetlenmeyen ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar. Bu, *erişimciler*aracılığıyla gerçekleştirilir: temel alınan veri üyesine değerler atayan ve alan özel yöntemler. [Set](../../language-reference/keywords/set.md) erişimcisi veri üyelerinin atanmasını sağlar ve [Get](../../language-reference/keywords/get.md) erişimcisi veri üyesi değerlerini alır.  
  
 Bu örnek, iki özelliği olan bir `Person` sınıfını gösterir: `Name` (dize) ve `Age` (int). Her iki özellik de `get` ve `set` erişimcileri sağlar, bu nedenle okuma/yazma özellikleri olarak değerlendirilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte, `Name` ve `Age` özellikleri [geneldir](../../language-reference/keywords/public.md) ve hem `get` hem de `set` erişimcisi içerir. Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına izin verir. Ancak erişimcilerinin birini dışlamak bazen tercih edilir. Örneğin `set` erişimcisini atlayarak, özelliği salt okunurdur:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatif olarak, bir erişimciye genel kullanıma sunabilirsiniz, ancak diğerini özel veya korumalı hale getirebilirsiniz. Daha fazla bilgi için bkz. [asimetrik erişimci erişilebilirliği](./restricting-accessor-accessibility.md).  
  
 Özellikler doğrulandıktan sonra, sınıfının alanları gibi kullanılabilirler. Bu, aşağıdaki deyimlerde olduğu gibi bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimi sağlar:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Bir özellik `set` yönteminde özel bir `value` değişkeninin kullanılabildiğini unutmayın. Bu değişken, kullanıcının belirttiği değeri içerir, örneğin:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Bir `Person` nesnesindeki `Age` özelliğini arttırmadan ilgili Temizleme sözdizimine dikkat edin:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Özellikleri modellemek için ayrı `set` ve `get` yöntemleri kullanılmışsa, eşdeğer kod şöyle görünebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` yöntemi bu örnekte geçersiz kılınır:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 `ToString` programda açıkça kullanılmadığından emin olun. `WriteLine` çağrıları tarafından varsayılan olarak çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Veri Erişimi](./properties.md)
- [Sınıflar ve Yapılar](./index.md)
