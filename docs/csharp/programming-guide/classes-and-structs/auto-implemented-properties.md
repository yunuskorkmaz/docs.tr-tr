---
title: Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 0d32dfd626cb8484e935dd0e8608c2e29d3ecbde
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560167"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimini daha kısa yapın. Nesneleri oluşturmak istemci kodu aynı zamanda tanırlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin erişilebilen özel, anonim destek alanı oluşturur `get` ve `set` erişimcileri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bazı otomatik uygulanan özellikler sahip basit bir sınıfı gösterir:  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 C# 6 ve sonraki sürümlerinde, otomatik uygulanan özellikler alanları için benzer şekilde başlatabilirsiniz:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Önceki örnekte gösterilen sınıf değişebilir. Oluşturulduktan sonra istemci kodu nesne değerleri değiştirebilirsiniz. Önemli davranışı (yöntem) yanı sıra veri içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir. Ancak, küçük sınıfları veya çok az kayıpla veya hiç davranışları yalnızca (veriler), bir dizi kapsüllemek ve yapı birimleri için ya da nesneleri sabit olarak ayarlama erişimcisine bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketicilere değişmez) ya da yalnızca bir alma erişimcisi (oluşturucu dışında her yerde değişmez) bildirme.  Daha fazla bilgi için [nasıl yapılır: bir basit sınıf Implemented Properties ile uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Bu kaynak kodunuzdan erişilebilir olmadığından öznitelikleri otomatik uygulanan özellikler ancak açıkça destekleyen alanlar izin verilir. Bir öznitelik özelliğinin destek alanı üzerinde kullanmanız gerekirse, normal bir özellik oluşturmanız yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
