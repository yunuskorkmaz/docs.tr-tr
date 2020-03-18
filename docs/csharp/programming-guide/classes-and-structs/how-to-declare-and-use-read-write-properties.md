---
title: Okuma yazma özellikleri nasıl beyan edilir ve kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170292"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Okuma yazma özelliklerini bildirme ve kullanma (C# Programlama Kılavuzu)
Özellikler, bir nesnenin verilerine korumasız, denetimsiz ve doğrulanmamış erişimle gelen riskler olmadan ortak veri üyelerinin rahatlığını sağlar. Bu, *accessörler*aracılığıyla gerçekleştirilir: temel veri üyesinden değer atayabilen ve alan özel yöntemler. [Ayarlanan](../../language-reference/keywords/set.md) erişimci veri üyelerinin atanmasını sağlar ve [erişimci veri](../../language-reference/keywords/get.md) üye değerlerini alır.  
  
 Bu örnek, `Person` iki özelliği olan `Name` bir sınıf `Age` gösterir: (dize) ve (int). Her iki `get` `set` özellik de sağlar ve erişilenler, bu nedenle okuma/yazma özellikleri olarak kabul edilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte, `Name` ve `Age` özellikleri [ortak](../../language-reference/keywords/public.md) ve `get` hem `set` bir hem de bir erişimci içerir. Bu, herhangi bir nesnenin bu özellikleri okumasına ve yazmasına olanak tanır. Ancak bazen erişimcilerden birini dışlamak istenir. Örneğin, erişimcinin `set` atlanması özelliğin salt okunur hale getirir:  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 Alternatif olarak, bir aksesuarı herkese açık hale getirebilir, ancak diğerini özel veya korumalı hale getirebilirsiniz. Daha fazla bilgi için [Asimetrik Erişime Erişime Uygunluk'a](./restricting-accessor-accessibility.md)bakın.  
  
 Özellikler beyan edildikten sonra, sınıfın alanları gibi kullanılabilirler. Bu, aşağıdaki ifadelerde olduğu gibi, bir özelliğin değerini alırken ve ayarlarken çok doğal bir sözdizimine izin verir:  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 Özellik `set` yönteminde özel `value` bir değişken in kullanılabildiğini unutmayın. Bu değişken, örneğin, kullanıcının belirttiği değeri içerir:  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 Özelliği bir `Person` nesne üzerinde artımlı `Age` olarak temiz sözdizimine dikkat edin:  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 Özellikleri `set` modellemek için ayrı ve `get` yöntemler kullanıldıysa, eşdeğer kod aşağıdaki gibi görünebilir:  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 Yöntem `ToString` bu örnekte geçersiz kılınmış:  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 `ToString` Programda açıkça kullanılmayana dikkat edin. `WriteLine` Aramalar tarafından varsayılan olarak çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Sınıflar ve Structs](./index.md)
