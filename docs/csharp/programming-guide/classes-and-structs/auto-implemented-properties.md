---
title: Otomatik uygulanan Özellikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: b5447dea8b510def95041549555de2ed5592e2d2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203580"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimini daha kısa yapın. Nesneleri oluşturmak istemci kodu aynı zamanda tanırlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin erişilebilen özel, anonim destek alanı oluşturur `get` ve `set` erişimcileri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bazı otomatik uygulanan özellikler sahip basit bir sınıfı gösterir:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 C# 6 ve sonraki sürümlerinde, otomatik uygulanan özellikler alanları için benzer şekilde başlatabilirsiniz:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Önceki örnekte gösterilen sınıf değişebilir. Oluşturulduktan sonra istemci kodu nesne değerleri değiştirebilirsiniz. Önemli davranışı (yöntem) yanı sıra veri içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir. Ancak, küçük sınıfları veya çok az kayıpla veya hiç davranışları yalnızca (veriler), bir dizi kapsüllemek ve yapı birimleri için ya da nesneleri sabit olarak ayarlama erişimcisine bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketicilere değişmez) ya da yalnızca bir alma erişimcisi (oluşturucu dışında her yerde değişmez) bildirme.  Daha fazla bilgi için [nasıl yapılır: Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
