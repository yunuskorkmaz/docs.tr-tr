---
title: Otomatik uygulanan özellikler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 44f3beb9de8c9d339c42db26bb9c510998abc7d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597142"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
C# 3,0 ve sonraki sürümlerde, özellik erişimcilerinde ek bir mantık gerekmediği zaman otomatik uygulanan özellikler özellik bildirimini daha kısa hale getirir. Ayrıca, istemci kodunun nesne oluşturmasını da sağlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve `set` Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 C# 6 ve sonrasında, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Önceki örnekte gösterilen sınıf değişebilir ' dir. İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir. Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir. Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [özel](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get bildirerek nesneleri sabit yapmalısınız. erişimci (Oluşturucu dışında her yerde sabit).  Daha fazla bilgi için [nasıl yapılır: Otomatik uygulanan özelliklerle](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)hafif bir sınıf uygulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [Değiştiriciler](../../language-reference/keywords/modifiers.md)
