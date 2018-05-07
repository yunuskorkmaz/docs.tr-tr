---
title: Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 756e235dacc3fcb2bf741d1d426e8dfcb53bf19b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
İlave bir mantık özellik gerektiğinde C# 3.0 ve sonraki sürümlerinde, otomatik uygulanan özellikler özellik bildirimi daha kısa hale getirir. Bunlar ayrıca nesneleri oluşturmak istemci kodu sağlar. Aşağıdaki örnekte gösterildiği gibi bir özelliği bildirme, derleyici özelliğin yalnızca erişilebilir bir özel, anonim yedekleme alanını oluşturur `get` ve `set` erişimciler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bazı otomatik uygulanan özellikler olan basit bir sınıfı gösterir:  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 C# 6 ve üzeri, otomatik uygulanan özellikler benzer şekilde alanlara başlatabilirsiniz:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Önceki örnekte gösterilen sınıfı değişebilir. Oluşturulduktan sonra istemci kodu nesnelerindeki değerleri değiştirebilirsiniz. Veri yanı sıra önemli davranışları (yöntemleri) içeren karmaşık sınıflarda ortak özellikler sağlamak gereklidir. Ancak, küçük sınıf ya da yalnızca bir değer (veri) kümesini kapsüllemek ve çok az kayıpla veya hiç davranışları yapının için ya da nesneleri değişmez olarak set erişimcisi bildirerek yaptığınız [özel](../../../csharp/language-reference/keywords/private.md) (tüketiciye değişmez) ya da yalnızca bir get erişimcisine (değişmez Oluşturucusu dışında her yerde) bildirme.  Daha fazla bilgi için bkz: [nasıl yapılır: Auto-Implemented özelliklerle hafif bir sınıf uygulama](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Bu kaynak kodunuzdan erişilebilir olmadığından öznitelikleri otomatik uygulanan özellikler ancak yedekleme alanları üzerinde açıkça izin verilir. Öznitelik bir özelliğin yedekleme alanı kullanmanız gerekiyorsa, yalnızca normal bir özellik oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
