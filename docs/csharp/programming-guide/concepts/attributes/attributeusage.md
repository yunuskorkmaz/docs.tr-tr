---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589323"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler. <xref:System.AttributeUsageAttribute> özel öznitelik tanımları için geçerli bir özniteliktir. `AttributeUsage` Özniteliği denetimi sağlar:

- Hangi program öğeleri özniteliği uygulanabilir. Kullanımını kısıtlamak sürece aşağıdaki program öğelerin herhangi bir öznitelik uygulanabilir:
  - derleme
  - modül
  - alan
  - olay
  - yöntemi
  - param
  - özellik
  - return
  - türü
- Olup öznitelik birden çok kez tek bir program öğesine uygulanabilir.
- Olup öznitelikleri türetilmiş sınıflar tarafından devralınır.

Varsayılan ayarları açıkça uygulandığında aşağıdaki örnekteki gibi görünür:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

Bu örnekte, `NewAttribute` sınıfı için herhangi bir desteklenen bir program öğesine uygulanabilir. Ancak, her varlık için yalnızca bir kez uygulanabilir. Öznitelik, bir temel sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.

<xref:System.AttributeUsageAttribute.AllowMultiple> Ve <xref:System.AttributeUsageAttribute.Inherited> aşağıdaki kodu aynı etkiye sahiptir. Bu nedenle bağımsız değişken isteğe bağlıdır:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

İlk <xref:System.AttributeUsageAttribute> bağımsız değişkeni olmalıdır bir veya daha fazla öğeleri <xref:System.AttributeTargets> sabit listesi. Birden çok hedef türü OR işlecini aşağıdaki örnekte gösterildiği gibi birlikte bağlanabilir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

C# 7.3 başlayarak, özellik ya da yedekleme alanını otomatik olarak uygulanan bir özellik için öznitelikleri uygulanabilir. Siz belirtmediğiniz sürece özniteliği özelliğine uygulanır `field` öznitelikte tanımlayıcısı. Her ikisi de, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Varsa <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkeni `true`, sonra elde edilen özniteliği birden çok kez tek bir varlık için aşağıdaki örnekte gösterildiği gibi uygulanabilir:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

Bu durumda, `MultiUseAttribute` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`. Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.

Varsa <xref:System.AttributeUsageAttribute.Inherited> olduğu `false`, öznitelik, öznitelik atanmış bir sınıftan türetilmiş sınıflar tarafından devralınan değil sonra. Örneğin:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

Bu durumda `NonInheritedAttribute` için uygulanmaz `DClass` devralma aracılığıyla.

## <a name="remarks"></a>Açıklamalar

`AttributeUsage` Özniteliği, bir tek kullanımlık özniteliğin birden çok kez aynı sınıfa uygulanamaz. `AttributeUsage` için bir diğer addır <xref:System.AttributeUsageAttribute>.

Daha fazla bilgi için [yansıma (C#) kullanarak erişen özniteliklerle](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, etkisini gösterir <xref:System.AttributeUsageAttribute.Inherited> ve <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkenleri <xref:System.AttributeUsageAttribute> özniteliği ve nasıl bir sınıfa uygulanan özel öznitelikler listelenebilir.

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
- [Özel öznitelikler (C#) oluşturma](creating-custom-attributes.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md)
