---
title: Otomatik uygulanan özellikler-C# Programlama Kılavuzu
description: C# ' de otomatik uygulanan bir özellik için, compteri, yalnızca özelliğin get ve set erişimcileri aracılığıyla erişilen özel, anonim bir destek alanı oluşturur.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474481"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)

C# 3,0 ve üzeri sürümlerde otomatik uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediği zaman özellik bildirimini daha kısa hale getirir. Ayrıca, istemci kodunun nesne oluşturmasını da sağlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur `set` .
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Arabirimlerde otomatik uygulanan özellikler bildiremezsiniz. Otomatik uygulanan özellikler özel bir örnek yedekleme alanı bildirir ve arabirimler örnek alanlarını bildiremeyebilir. Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her bir tür tarafından uygulanması gereken erişimcilere sahip bir özellik bildirir.

C# 6 ve üzeri sürümlerde, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Önceki örnekte gösterilen sınıf değişebilir ' dir. İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir. Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir. Bununla birlikte, yalnızca bir değer kümesini (veri) kapsülleyen ve hiç davranışlarına sahip olan küçük sınıflar veya yapılar için, küme erişimcisini [Private](../../language-reference/keywords/private.md) (Sabit-tüketiciler) olarak bildirerek veya yalnızca bir get erişimcisi bildirerek (Oluşturucu dışında sabit olarak) nesneleri sabit hale getirebilirsiniz.  Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [Değiştiriciler](/dotnet/csharp/language-reference/keywords)
