---
title: Belge açıklamaları için önerilen Etiketler-C# Programlama Kılavuzu
description: Belge açıklamaları için önerilen Etiketler hakkında bilgi edinin. Önerilen etiketlerin listesini görün ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 65bca6f979c5ffd91507b571a4f049377315192d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381521"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="68c5f-104">Belge açıklamaları için önerilen Etiketler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="68c5f-104">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="68c5f-105">C# derleyicisi kodunuzda belge açıklamalarını işler ve adı **/doc** komut satırı seçeneğinde belirttiğiniz BIR dosyada xml olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="68c5f-105">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="68c5f-106">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68c5f-106">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="68c5f-107">Etiketler, türler ve tür üyeleri gibi kod yapıları üzerinde işlenir.</span><span class="sxs-lookup"><span data-stu-id="68c5f-107">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="68c5f-108">Belge açıklamaları bir ad alanına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="68c5f-108">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="68c5f-109">Derleyici geçerli XML olan herhangi bir etiketi işleyecek.</span><span class="sxs-lookup"><span data-stu-id="68c5f-109">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="68c5f-110">Aşağıdaki Etiketler kullanıcı belgelerinde genel olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="68c5f-110">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="68c5f-111">Etiketler</span><span class="sxs-lookup"><span data-stu-id="68c5f-111">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc>](./inheritdoc.md)|[\<returns>](./returns.md)|
  
<span data-ttu-id="68c5f-112">( \* derleyicinin söz dizimini doğruladığını gösterir.)</span><span class="sxs-lookup"><span data-stu-id="68c5f-112">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="68c5f-113">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, ve sırasıyla ve olan HTML kodlamasını kullanın `<` `>` `&lt;` `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="68c5f-113">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="68c5f-114">Bu kodlama aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="68c5f-114">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="68c5f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68c5f-115">See also</span></span>

- [<span data-ttu-id="68c5f-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68c5f-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="68c5f-117">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="68c5f-117">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="68c5f-118">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="68c5f-118">XML documentation comments</span></span>](./index.md)
