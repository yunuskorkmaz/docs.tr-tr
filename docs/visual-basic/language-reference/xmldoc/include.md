---
title: '&lt;dahil&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602742"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="9c70a-102">&lt;dahil&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c70a-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="9c70a-103">Türleri ve kaynak kodunuzu üyeleri tanımlayan başka bir dosyaya başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="9c70a-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c70a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c70a-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c70a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c70a-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="9c70a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9c70a-106">Required.</span></span> <span data-ttu-id="9c70a-107">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="9c70a-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="9c70a-108">Dosya adı nitelenmiş bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c70a-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="9c70a-109">İçine `filename` çift tırnak işaretleri ("").</span><span class="sxs-lookup"><span data-stu-id="9c70a-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="9c70a-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9c70a-110">Required.</span></span> <span data-ttu-id="9c70a-111">Etiketleri yolunu `filename` etikete müşteri adayları `name`.</span><span class="sxs-lookup"><span data-stu-id="9c70a-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="9c70a-112">Yolu çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="9c70a-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="9c70a-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9c70a-113">Required.</span></span> <span data-ttu-id="9c70a-114">Açıklamaları önündeki etiketinde ad tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9c70a-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="9c70a-115">`Name` sahip bir `id`.</span><span class="sxs-lookup"><span data-stu-id="9c70a-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="9c70a-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9c70a-116">Required.</span></span> <span data-ttu-id="9c70a-117">Açıklamaları önündeki etiket kimliği.</span><span class="sxs-lookup"><span data-stu-id="9c70a-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="9c70a-118">Kimliği tek tırnak işaretleri içine alın (' ').</span><span class="sxs-lookup"><span data-stu-id="9c70a-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c70a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c70a-119">Remarks</span></span>  
 <span data-ttu-id="9c70a-120">Kullanım `<include>` etiketi başka bir dosya türlerini tanımlamak açıklamaları ve kaynak kodunuzu üyelerinde bakın.</span><span class="sxs-lookup"><span data-stu-id="9c70a-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="9c70a-121">Bu belge açıklamaları doğrudan, kaynak kodu dosyasına yerleştirerek alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="9c70a-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="9c70a-122">`<include>` Etiketini W3C XML Path dili (XPath) sürüm 1.0 öneri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c70a-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="9c70a-123">Daha fazla bilgi için özelleştirme yolları, `<include>` kullanın, şu adreste http://www.w3.org/TR/xpath.</span><span class="sxs-lookup"><span data-stu-id="9c70a-123">More information for ways to customize your `<include>` use is available at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c70a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c70a-124">Example</span></span>  
 <span data-ttu-id="9c70a-125">Bu örnekte `<include>` üye belge açıklamaları olarak adlandırılan bir dosyadan içeri aktarmak için etiket `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="9c70a-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="9c70a-126">Biçimi `commentFile.xml` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="9c70a-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c70a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c70a-127">See Also</span></span>  
 [<span data-ttu-id="9c70a-128">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="9c70a-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
