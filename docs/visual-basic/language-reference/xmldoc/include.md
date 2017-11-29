---
title: '&lt;dahil&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22eebaa8da8ef082e132cfdf8cb68498bfe16d73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="79001-102">&lt;dahil&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79001-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="79001-103">Türleri ve kaynak kodunuzu üyeleri tanımlayan başka bir dosyaya başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="79001-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79001-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79001-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79001-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79001-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="79001-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="79001-106">Required.</span></span> <span data-ttu-id="79001-107">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="79001-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="79001-108">Dosya adı nitelenmiş bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79001-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="79001-109">İçine `filename` çift tırnak işaretleri ("").</span><span class="sxs-lookup"><span data-stu-id="79001-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="79001-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="79001-110">Required.</span></span> <span data-ttu-id="79001-111">Etiketleri yolunu `filename` etikete müşteri adayları `name`.</span><span class="sxs-lookup"><span data-stu-id="79001-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="79001-112">Yolu çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="79001-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="79001-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="79001-113">Required.</span></span> <span data-ttu-id="79001-114">Açıklamaları önündeki etiketinde ad tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="79001-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="79001-115">`Name`sahip bir `id`.</span><span class="sxs-lookup"><span data-stu-id="79001-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="79001-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="79001-116">Required.</span></span> <span data-ttu-id="79001-117">Açıklamaları önündeki etiket kimliği.</span><span class="sxs-lookup"><span data-stu-id="79001-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="79001-118">Kimliği tek tırnak işaretleri içine alın (' ').</span><span class="sxs-lookup"><span data-stu-id="79001-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79001-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79001-119">Remarks</span></span>  
 <span data-ttu-id="79001-120">Kullanım `<include>` etiketi başka bir dosya türlerini tanımlamak açıklamaları ve kaynak kodunuzu üyelerinde bakın.</span><span class="sxs-lookup"><span data-stu-id="79001-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="79001-121">Bu belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="79001-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="79001-122">`<include>` Etiketini W3C XML Path dili (XPath) sürüm 1.0 öneri kullanır.</span><span class="sxs-lookup"><span data-stu-id="79001-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="79001-123">Daha fazla bilgi için özelleştirme yolları, `<include>` http://www.w3.org/TR/xpath kullanım kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79001-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79001-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="79001-124">Example</span></span>  
 <span data-ttu-id="79001-125">Bu örnekte `<include>` üye belge açıklamaları olarak adlandırılan bir dosyadan içeri aktarmak için etiket `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="79001-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="79001-126">Biçimi `commentFile.xml` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="79001-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79001-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79001-127">See Also</span></span>  
 [<span data-ttu-id="79001-128">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="79001-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
