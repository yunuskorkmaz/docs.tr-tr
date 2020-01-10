---
title: <summary> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 63c65e11a274779015cf99859b7fa67bb536529d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711694"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="2ab35-102">\<Özet > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2ab35-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="2ab35-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ab35-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ab35-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ab35-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2ab35-105">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="2ab35-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ab35-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ab35-106">Remarks</span></span>  
 <span data-ttu-id="2ab35-107">\<Özet > etiketi, bir tür veya tür üyesini tanımlamakta kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ab35-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="2ab35-108">Bir tür açıklamasına ek bilgi eklemek için [\<açıklamaları >](./remarks.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ab35-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="2ab35-109">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçlarını etkinleştirmek için [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ab35-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="2ab35-110">\<Summary > etiketinin metni, IntelliSense 'teki tür hakkındaki tek bilgi kaynağıdır ve ayrıca Nesne Tarayıcısı penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2ab35-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="2ab35-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2ab35-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="2ab35-112">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ab35-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab35-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab35-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="2ab35-114">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="2ab35-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="2ab35-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab35-115">Example</span></span>  
 <span data-ttu-id="2ab35-116">Aşağıdaki örnek, genel bir türe `cref` başvurusunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ab35-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="2ab35-117">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="2ab35-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ab35-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab35-118">See also</span></span>

- [<span data-ttu-id="2ab35-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ab35-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2ab35-120">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="2ab35-120">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
