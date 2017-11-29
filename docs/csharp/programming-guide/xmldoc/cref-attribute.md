---
title: "cref Özniteliği (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cffba9083b22813be3dd0379b244f4d078f8549
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="c4bfc-102">cref Özniteliği (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c4bfc-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="c4bfc-103">`cref` Bir XML belgeleri etiketinde öznitelik "kod başvurusu" anlamına gelir</span><span class="sxs-lookup"><span data-stu-id="c4bfc-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="c4bfc-104">Bu etiket iç metni türü, yöntemi veya özelliği gibi bir kod öğesi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="c4bfc-105">Belge Araçlar [Sandcastle](https://github.com/EWSoftware/SHFB) kullanmak `cref` burada tür veya üye belgelenmiştir sayfasına köprüler otomatik olarak oluşturmak için öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4bfc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4bfc-106">Example</span></span>  
 <span data-ttu-id="c4bfc-107">Aşağıdaki örnekte gösterildiği `cref` olarak kullanılan öznitelikler [ \<bkz >](../../../csharp/programming-guide/xmldoc/see.md) etiketler.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]  
  
 <span data-ttu-id="c4bfc-108">Derlendiğinde program şu XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="c4bfc-109">Dikkat `cref` için öznitelik `GetZero` yöntemi, örneğin, dönüştürülmüş derleyicisi tarafından `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="c4bfc-110">"/ M:" öneki "yöntemi" anlamına gelir ve Sandcastle gibi belgeleri araçları tarafından tanınan bir kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="c4bfc-111">Önekleri tam bir listesi için bkz: [XML dosyasını işleme](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="c4bfc-111">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
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
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
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
  
## <a name="see-also"></a><span data-ttu-id="c4bfc-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4bfc-112">See Also</span></span>  
 [<span data-ttu-id="c4bfc-113">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="c4bfc-113">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="c4bfc-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="c4bfc-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
