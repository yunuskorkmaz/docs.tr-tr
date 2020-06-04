---
title: Belge açıklamaları için önerilen XML etiketleri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400104"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="a478d-102">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a478d-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="a478d-103">Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a478d-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="a478d-104">XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a478d-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="a478d-105">Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a478d-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="a478d-106">Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="a478d-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a478d-107">Belge açıklamaları ad alanlarına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="a478d-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="a478d-108">Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="a478d-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="a478d-109">Derleyici geçerli XML olan herhangi bir etiketi işler.</span><span class="sxs-lookup"><span data-stu-id="a478d-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="a478d-110">Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a478d-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="a478d-111">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-111">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="a478d-112">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-112">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="a478d-113">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-113">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="a478d-114">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-114">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="a478d-115">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-115">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="a478d-116">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-116">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="a478d-117">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a478d-117">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="a478d-118">(<sup>1</sup> derleyici söz dizimini doğrular.)</span><span class="sxs-lookup"><span data-stu-id="a478d-118">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a478d-119">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `&lt;` ve kullanın `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="a478d-119">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="a478d-120">Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak görünür `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="a478d-120">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a478d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a478d-121">See also</span></span>

- [<span data-ttu-id="a478d-122">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="a478d-122">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="a478d-123">-doc</span><span class="sxs-lookup"><span data-stu-id="a478d-123">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="a478d-124">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a478d-124">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
