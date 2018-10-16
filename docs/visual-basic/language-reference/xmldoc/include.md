---
title: '&lt;dahil&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 0f143f8c023102f44b41e3898f29d18be0083128
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349114"
---
# <a name="ltincludegt-visual-basic"></a><span data-ttu-id="1ef5d-102">&lt;dahil&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef5d-102">&lt;include&gt; (Visual Basic)</span></span>
<span data-ttu-id="1ef5d-103">Türler ve üyeler, kaynak kodunuzdaki açıklayan başka bir dosyaya ifade eder.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-103">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ef5d-104">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ef5d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ef5d-105">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="1ef5d-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-106">Required.</span></span> <span data-ttu-id="1ef5d-107">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-107">The name of the file containing the documentation.</span></span> <span data-ttu-id="1ef5d-108">Dosya adını içeren bir yol nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-108">The file name can be qualified with a path.</span></span> <span data-ttu-id="1ef5d-109">İçine `filename` çift tırnak işaretleri ("").</span><span class="sxs-lookup"><span data-stu-id="1ef5d-109">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="1ef5d-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-110">Required.</span></span> <span data-ttu-id="1ef5d-111">Etiketleri yolunu `filename` etikete müşteri adayları `name`.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="1ef5d-112">Yolu, çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="1ef5d-112">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="1ef5d-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-113">Required.</span></span> <span data-ttu-id="1ef5d-114">Yorumları önündeki etiketinde ad tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-114">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="1ef5d-115">`Name` sahip bir `id`.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-115">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="1ef5d-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-116">Required.</span></span> <span data-ttu-id="1ef5d-117">Yorumları önünde etiket kimliği.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-117">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="1ef5d-118">Kimliği tek tırnak işaretleri içine (' ').</span><span class="sxs-lookup"><span data-stu-id="1ef5d-118">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef5d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ef5d-119">Remarks</span></span>  
 <span data-ttu-id="1ef5d-120">Kullanım `<include>` türlerini açıklayan yorumlar başka bir dosyaya ve kaynak kodunuzu üyelerine başvurmak için etiket.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-120">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="1ef5d-121">Bu belge açıklamaları doğrudan, kaynak kodu dosyasında yerleştirme için bir alternatifidir.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-121">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="1ef5d-122">`<include>` Etiketini kullanır: W3C XML Path Language (XPath) sürüm 1.0 öneri.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-122">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="1ef5d-123">Özelleştirme yolları hakkında daha fazla bilgi için `<include>` bakın <https://www.w3.org/TR/xpath>.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-123">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef5d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef5d-124">Example</span></span>  
 <span data-ttu-id="1ef5d-125">Bu örnekte `<include>` belge açıklamaları üye adlı bir dosyadan içeri aktarmak için etiket `commentFile.xml`.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-125">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 <span data-ttu-id="1ef5d-126">Biçimi `commentFile.xml` gibidir.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-126">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ef5d-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1ef5d-127">See Also</span></span>  
 [<span data-ttu-id="1ef5d-128">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="1ef5d-128">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
