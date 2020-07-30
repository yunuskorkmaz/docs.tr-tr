---
title: cref özniteliği-C# Programlama Kılavuzu
description: Cref özniteliği hakkında bilgi edinin. Cref özniteliği "kod başvurusu" anlamına gelir ve etiketin iç metninin bir kod öğesi olduğunu belirtir.
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 31fa1a3f182d7b72a1dfbe1ce47386f87fbbff75
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382002"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="229c2-104">cref özniteliği (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="229c2-104">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="229c2-105">`cref`XML belgesi etiketindeki özniteliği "kod başvurusu" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="229c2-105">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="229c2-106">Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="229c2-106">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="229c2-107">[Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçları, `cref` otomatik olarak tür veya üyenin belgelendiği sayfaya köprüler oluşturmak için öznitelikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="229c2-107">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="229c2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="229c2-108">Example</span></span>

<span data-ttu-id="229c2-109">Aşağıdaki örnek, `cref` etiketlerinde kullanılan öznitelikleri gösterir [\<see>](./see.md) .</span><span class="sxs-lookup"><span data-stu-id="229c2-109">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="229c2-110">Derlendiğinde, program aşağıdaki XML dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="229c2-110">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="229c2-111">`cref`Yöntemin özniteliği, `GetZero` Örneğin, derleyicisinin tarafından öğesine dönüştürüldüğünü unutmayın `"M:TestNamespace.TestClass.GetZero"` .</span><span class="sxs-lookup"><span data-stu-id="229c2-111">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="229c2-112">"D:" öneki "method" anlamına gelir ve DocFX ve Sandrole gibi belge araçları tarafından tanınan bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="229c2-112">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="229c2-113">Tüm ön eklerin listesi için bkz. [XML dosyasını işleme](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="229c2-113">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="229c2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="229c2-114">See also</span></span>

- [<span data-ttu-id="229c2-115">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="229c2-115">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="229c2-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="229c2-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
