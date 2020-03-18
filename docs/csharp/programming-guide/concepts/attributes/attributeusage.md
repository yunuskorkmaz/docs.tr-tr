---
title: ÖznitelikKullanım (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668724"
---
# <a name="attributeusage-c"></a>ÖznitelikKullanım (C#)

Özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler. <xref:System.AttributeUsageAttribute>özel öznitelik tanımlarına uyguladığınız bir özniteliktir. Öznitelik, `AttributeUsage` aşağıdakileri denetlemenizi sağlar:

- Hangi program öğeleriöze uygulanabilir. Kullanımını kısıtlamadığınız sürece, aşağıdaki program öğelerinden herhangi biri için bir öznitelik uygulanabilir:
  - derleme
  - modül
  - alan
  - event
  - method
  - param
  - özellik
  - return
  - type
- Bir öznitelik birden çok kez tek bir program öğesine uygulanabilir olup olmadığını.
- Özniteliklerin türetilmiş sınıflar tarafından devralınmış olup olmadığı.

Varsayılan ayarlar açıkça uygulandığında aşağıdaki örnek gibi görünür:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

Bu örnekte, `NewAttribute` sınıf desteklenen herhangi bir program öğesine uygulanabilir. Ancak her varlık için yalnızca bir kez uygulanabilir. Öznitelik, taban sınıfa uygulandığında türetilmiş sınıflar tarafından devralınan.

Ve <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> bağımsız değişkenler isteğe bağlıdır, bu nedenle aşağıdaki kod aynı etkiye sahiptir:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

İlk <xref:System.AttributeUsageAttribute> bağımsız değişken numaralandırmanın <xref:System.AttributeTargets> bir veya daha fazla öğesi olmalıdır. Birden çok hedef türü, aşağıdaki örnekte görüldüğü gibi, OR işleciyle birlikte bağlanabilir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

C# 7.3'ten başlayarak, öznitelikler otomatik olarak uygulanan bir özellik için özellik veya destek alanına uygulanabilir. Öznitelik, öznitelikte `field` belirtici belirtmediğiniz sürece özellik için geçerlidir. Her ikisi de aşağıdaki örnekte gösterilir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

<xref:System.AttributeUsageAttribute.AllowMultiple> Bağımsız değişken `true`ise, aşağıdaki örnekte gösterildiği gibi, ortaya çıkan öznitelik tek bir varlığa birden fazla kez uygulanabilir:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

Bu durumda, `MultiUseAttribute` '' olarak `AllowMultiple` `true`ayarlandığı için tekrar tekrar uygulanabilir. Birden çok öznitelik uygulamak için gösterilen her iki biçim de geçerlidir.

<xref:System.AttributeUsageAttribute.Inherited> Ise, `false`o zaman öznitelik atfedilen bir sınıftan türetilen sınıflar tarafından devralınan değildir. Örnek:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

Bu durumda `NonInheritedAttribute` miras `DClass` yoluyla uygulanmaz.

## <a name="remarks"></a>Açıklamalar

Öznitelik `AttributeUsage` tek kullanımlık bir özniteliktir, aynı sınıfa birden fazla kez uygulanamaz. `AttributeUsage`<xref:System.AttributeUsageAttribute>için bir takma addır.

Daha fazla bilgi için bkz: [Yansıma (C#) kullanarak Özniteliklere Erişim.](accessing-attributes-by-using-reflection.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, öznitelik ve <xref:System.AttributeUsageAttribute.Inherited> <xref:System.AttributeUsageAttribute> <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkenlerin etkisini ve bir sınıfa uygulanan özel özniteliklerin nasıl numaralandırılabildiğini gösterir.

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>Örnek Çıktı

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- <xref:System.Reflection>
- [C# Programlama Kılavuzu](../..//index.md)
- [Öznitelikler](../../../..//standard/attributes/index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler](index.md)
- [Özel Öznitelikler oluşturma (C#)](creating-custom-attributes.md)
- [Yansıma (C#) kullanarak Özniteliklere Erişim](accessing-attributes-by-using-reflection.md)
