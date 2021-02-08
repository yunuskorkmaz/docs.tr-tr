---
description: 'Hakkında daha fazla bilgi edinin: belge açıklamaları için önerilen XML etiketleri (Visual Basic)'
title: Belge açıklamaları için önerilen XML etiketleri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 5d3451d98b66817de143cfbddbcb6121de57ca8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787454"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="1cc97-103">Belge Açıklamaları için Önerilen XML Etiketleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cc97-103">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>

<span data-ttu-id="1cc97-104">Visual Basic Derleyicisi, kodunuzdaki belge açıklamalarını bir XML dosyasına işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1cc97-104">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="1cc97-105">XML dosyasını belgelere işlemek için ek araçlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cc97-105">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="1cc97-106">Türler ve tür üyeleri gibi kod yapılarında XML yorumlarına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1cc97-106">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="1cc97-107">Kısmi türler için, türünün yalnızca bir kısmı XML yorumlarına sahip olabilir, ancak üyelerini açıklama eklemek için herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="1cc97-107">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc97-108">Belge açıklamaları ad alanlarına uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="1cc97-108">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="1cc97-109">Bunun nedeni, bir ad alanının birçok derlemeyi yaymasına ve tüm derlemelerin aynı anda yüklenebilmesidir.</span><span class="sxs-lookup"><span data-stu-id="1cc97-109">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="1cc97-110">Derleyici geçerli XML olan herhangi bir etiketi işler.</span><span class="sxs-lookup"><span data-stu-id="1cc97-110">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="1cc97-111">Aşağıdaki Etiketler kullanıcı belgelerinde yaygın olarak kullanılan işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cc97-111">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|<span data-ttu-id="1cc97-112">[\<exception>](exception.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-112">[\<exception>](exception.md) <sup>1</sup></span></span>|<span data-ttu-id="1cc97-113">[\<include>](include.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-113">[\<include>](include.md) <sup>1</sup></span></span>|[\<list>](list.md)|  
|[\<para>](para.md)|<span data-ttu-id="1cc97-114">[\<param>](param.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-114">[\<param>](param.md) <sup>1</sup></span></span>|[\<paramref>](paramref.md)|  
|<span data-ttu-id="1cc97-115">[\<permission>](permission.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-115">[\<permission>](permission.md) <sup>1</sup></span></span>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|<span data-ttu-id="1cc97-116">[\<see>](see.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-116">[\<see>](see.md) <sup>1</sup></span></span>|<span data-ttu-id="1cc97-117">[\<seealso>](seealso.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-117">[\<seealso>](seealso.md) <sup>1</sup></span></span>|[\<summary>](summary.md)|  
|<span data-ttu-id="1cc97-118">[\<typeparam>](typeparam.md)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1cc97-118">[\<typeparam>](typeparam.md) <sup>1</sup></span></span>|[\<value>](value.md)||  
  
 <span data-ttu-id="1cc97-119">(<sup>1</sup> derleyici söz dizimini doğrular.)</span><span class="sxs-lookup"><span data-stu-id="1cc97-119">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc97-120">Bir belge açıklamasının metninde Açılı ayraçların görünmesini istiyorsanız, `&lt;` ve kullanın `&gt;` .</span><span class="sxs-lookup"><span data-stu-id="1cc97-120">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="1cc97-121">Örneğin, dize `"&lt;text in angle brackets&gt;"` olarak görünür `<text in angle brackets>` .</span><span class="sxs-lookup"><span data-stu-id="1cc97-121">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc97-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cc97-122">See also</span></span>

- [<span data-ttu-id="1cc97-123">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="1cc97-123">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="1cc97-124">-doc</span><span class="sxs-lookup"><span data-stu-id="1cc97-124">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="1cc97-125">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1cc97-125">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
