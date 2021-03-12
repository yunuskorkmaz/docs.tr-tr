---
title: Otomatik uygulanan özellikler-C# Programlama Kılavuzu
description: C# ' de otomatik uygulanan bir özellik için, compteri, yalnızca özelliğin get ve set erişimcileri aracılığıyla erişilen özel, anonim bir destek alanı oluşturur.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: ef3e2d6dd5851801ea06d65b87c2274d8e44b4f1
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190287"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)

C# 3,0 ve üzeri sürümlerde otomatik uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediği zaman özellik bildirimini daha kısa hale getirir. Ayrıca, istemci kodunun nesne oluşturmasını da sağlar. Aşağıdaki örnekte gösterildiği gibi bir özellik bildirdiğinizde, derleyici yalnızca özelliğin `get` ve Erişimcilerde erişilebilen özel, anonim bir destek alanı oluşturur `set` . C# 9 ve sonraki sürümlerde, `init` erişimciler otomatik olarak uygulanan özellikler olarak da bildirilebilecek.
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bazı otomatik uygulanmış özelliklere sahip basit bir sınıfı göstermektedir:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Arabirimlerde otomatik uygulanan özellikler bildiremezsiniz. Otomatik uygulanan özellikler özel bir örnek yedekleme alanı bildirir ve arabirimler örnek alanlarını bildiremeyebilir. Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her bir tür tarafından uygulanması gereken erişimcilere sahip bir özellik bildirir.

C# 6 ve üzeri sürümlerde, alanlarla aynı şekilde otomatik uygulanan özellikler başlatabilirsiniz:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Önceki örnekte gösterilen sınıf değişebilir ' dir. İstemci kodu, oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir. Önemli davranışları (Yöntemler) ve verileri içeren karmaşık sınıflarda, genellikle ortak özelliklerin olması gerekir. Ancak, yalnızca bir değer kümesini (veri) kapsülleyen ve çok az davranışlara sahip olan küçük sınıflar veya yapılar için, nesneleri sabit hale getirmek üzere aşağıdaki seçeneklerden birini kullanmanız gerekir:

* Yalnızca bir `get` erişimci bildirin (Oluşturucu dışında her yerde sabit).
* Bir `get` erişimci ve erişimci bildirin `init` (nesne oluşturma sırasında her yerde sabit).
* `set`Erişimciyi [özel](../../language-reference/keywords/private.md) olarak bildirin (Sabit-müşteriler).

Daha fazla bilgi için bkz. [Otomatik uygulanan özelliklerle hafif bir sınıf uygulama](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [Değiştiriciler](../../language-reference/keywords/index.md)
