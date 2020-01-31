---
title: cref özniteliği- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 2a9b9966a28b62c41ac6091268ae172bae3a40d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793436"
---
# <a name="cref-attribute-c-programming-guide"></a>cref özniteliği (C# Programlama Kılavuzu)

XML belgesi etiketindeki `cref` özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları, tür veya üyenin belgelendiği sayfaya otomatik olarak köprüler oluşturmak için `cref` özniteliklerini kullanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, [\<`cref` >](./see.md) etiketlerinde kullanılan öznitelikleri gösterir.

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

Derlendiğinde, program aşağıdaki XML dosyasını oluşturur. Örneğin, `GetZero` yöntemi için `cref` özniteliğinin `"M:TestNamespace.TestClass.GetZero"`için derleyici tarafından dönüştürüldüğünü unutmayın. "D:" öneki "method" anlamına gelir ve DocFX ve Sandrole gibi belge araçları tarafından tanınan bir kuraldır. Tüm ön eklerin listesi için bkz. [XML dosyasını işleme](./processing-the-xml-file.md).

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example> 
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass 
            {
                static int Main() 
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks> 
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks> 
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML belge açıklamaları](./index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
