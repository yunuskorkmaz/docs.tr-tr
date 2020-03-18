---
title: Otomatik Uygulanan Özellikler - C# Programlama Kılavuzu
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170331"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Otomatik Uygulanan Özellikler (C# Programlama Kılavuzu)

C# 3.0 ve sonraki durumlarda, otomatik olarak uygulanan özellikler, özellik erişimcilerinde ek bir mantık gerekmediğinde özellik bildirimini daha kısa yapar. Ayrıca, istemci kodunun nesneler oluşturmasını da sağlarlar. Aşağıdaki örnekte gösterildiği gibi bir özelliği beyan ettiğinizde, derleyici yalnızca mülkün `get` ve `set` erişime sahip olanların aracılığıyla erişilebilen özel, anonim bir destek alanı oluşturur.
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bazı otomatik uygulanan özelliklere sahip basit bir sınıfı gösterir:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Arabirimlerde otomatik olarak uygulanan özellikleri bildiremezsiniz. Otomatik olarak uygulanan özellikler özel örnek destek alanı bildirir ve arabirimler örnek alanlarını beyan emeyebilir. Bir gövde tanımlamadan bir arabirimde bir özelliği bildirmek, bu arabirimi uygulayan her tür tarafından uygulanması gereken erişimci bir özelliği bildirir.

C# 6 ve sonraki durumlarda, otomatik olarak uygulanan özellikleri alanlara benzer şekilde başharfekleyebilirsiniz:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

Önceki örnekte gösterilen sınıf mutable. İstemci kodu oluşturulduktan sonra nesnelerdeki değerleri değiştirebilir. Önemli davranış (yöntem) yanı sıra veri içeren karmaşık sınıflarda, genellikle ortak özelliklere sahip olmak gereklidir. Ancak, yalnızca bir değer kümesini (veri) kapsülleyen ve çok az veya hiç davranışı olmayan küçük sınıflar veya yapılar için, ayarlanan erişimi [özel](../../language-reference/keywords/private.md) (tüketicilere değişmez) olarak beyan ederek veya yalnızca bir erişime sahip (oluşturucu hariç her yerde değişmez) beyan ederek nesneleri değişmez hale getirmelisiniz.  Daha fazla bilgi için, [otomatik olarak uygulanan özelliklere sahip hafif bir sınıfın nasıl uygulanacağını](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)görün.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikler](./properties.md)
- [Değiştiriciler](/dotnet/csharp/language-reference/keywords)
