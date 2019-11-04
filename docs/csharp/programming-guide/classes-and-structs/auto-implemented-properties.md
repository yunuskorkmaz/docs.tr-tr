---
title: Otomatik uygulanan özellikler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 212fdde3a5ecc8b0a43e33bec3537bd57b1387e9
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419408"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)
C# 3,0 ve sonraki sürümlerde, özellik erişimcilerinde ek bir mantık gerekmediği zaman otomatik uygulanan özellikler özellik bildirimini daha kısa hale getirir. Ayrıca, istemci kodunun nesne oluşturmasını da sağlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve `set` erişimcileri aracılığıyla erişilebilen özel, anonim bir destek alanı oluşturur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 C# 6 ve sonrasında, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 Önceki örnekte gösterilen sınıf değişebilir ' dir. İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir. Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir. Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [özel](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get bildirerek nesneleri sabit yapmalısınız. erişimci (Oluşturucu dışında her yerde sabit).  Daha fazla bilgi için bkz. [nasıl yapılır: otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Erişimi](./properties.md)
- [Değiştiriciler](/dotnet/csharp/language-reference/keywords)
