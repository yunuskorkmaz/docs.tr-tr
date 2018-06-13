---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955934"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler. <xref:System.AttributeUsageAttribute> özel öznitelik tanımları için uygulamanıza bir özniteliktir. `AttributeUsage` Özniteliği denetimi sağlar:

- Hangi program öğeleri öznitelik için uygulanabilir. Kısıtlama sürece, kullanımdır herhangi bir program öğesi için bir öznitelik uygulanabilir:
  - derleme
  - modül
  - alan
  - olay
  - yöntemi
  - Param
  - özellik
  - return
  - türü
- Olup bir öznitelik birden çok kez tek bir program öğesi için uygulanabilir.
- Olup öznitelikleri türetilmiş sınıflar tarafından devralınır.

Varsayılan ayarları açıkça uygulandığında aşağıdaki gibi görünür:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

Bu örnekte, `NewAttribute` sınıfı, tüm desteklenen bir program öğesi için uygulanabilir. Ancak yalnızca bir kez her varlık için uygulanabilir. Öznitelik, bir temel sınıf uygulandığında türetilen sınıflar tarafından devralınır.

<xref:System.AttributeUsageAttribute.AllowMultiple> Ve <xref:System.AttributeUsageAttribute.Inherited> değişkenleridir isteğe bağlı, aşağıdaki kodu aynı etkiye sahiptir:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

İlk <xref:System.AttributeUsageAttribute> bağımsız değişkeni, bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> numaralandırması. Birden çok hedef türleri, aşağıdaki örnekte gösterildiği gibi OR işleci birlikte bağlanabilir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

C# 7.3 içinde başlayarak, öznitelikler özelliği veya yedekleme alanını otomatik uygulanan bir özellik için uygulanabilir. Belirtmediğiniz sürece öznitelik özelliğine uygular `field` öznitelikte tanımlayıcısı. Her ikisi de aşağıdaki örnekte gösterilir:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Varsa <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkeni `true`, sonuçta elde edilen özniteliği birden çok kez tek bir varlık için aşağıdaki örnekte gösterildiği gibi uygulanabilir sonra:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

Bu durumda, `MultiUseAttribute` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`. Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.

Varsa <xref:System.AttributeUsageAttribute.Inherited> olan `false`, öznitelik öznitelikli sınıfından türetilen sınıflar tarafından devralınır değil sonra. Örneğin:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

Bu durumda `NonInheritedAttribute` için uygulanmaz `DClass` devralma aracılığıyla.

## <a name="remarks"></a>Açıklamalar

`AttributeUsage` Özniteliktir tek kullanımlık özniteliği--birden çok kez aynı sınıfa uygulanamaz. `AttributeUsage` bir diğer adı için <xref:System.AttributeUsageAttribute>.

Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, etkisini gösterir <xref:System.AttributeUsageAttribute.Inherited> ve <xref:System.AttributeUsageAttribute.AllowMultiple> bağımsız değişkenleri <xref:System.AttributeUsageAttribute> özniteliğini ve bir sınıfa uygulanan özel öznitelikler nasıl listelenebilir.

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

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [C# Programlama Kılavuzu](../..//index.md)  
 [Öznitelikler](../../../..//standard/attributes/index.md)  
 [Yansıma (C#)](../reflection.md)  
 [Öznitelikler](index.md)  
 [Özel öznitelikler (C#) oluşturma](creating-custom-attributes.md)  
 [Yansıma (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md)
