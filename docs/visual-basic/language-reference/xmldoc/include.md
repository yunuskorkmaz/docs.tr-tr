---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <include> (Visual Basic)'
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8207b74ed74bd529f2da865777e287320b23d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787467"
---
# <a name="include-visual-basic"></a><span data-ttu-id="3f84c-103">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f84c-103">\<include> (Visual Basic)</span></span>

<span data-ttu-id="3f84c-104">Kaynak kodunuzda türleri ve üyeleri açıklayan başka bir dosya anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-104">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f84c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f84c-105">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f84c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f84c-106">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="3f84c-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-107">Required.</span></span> <span data-ttu-id="3f84c-108">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="3f84c-108">The name of the file containing the documentation.</span></span> <span data-ttu-id="3f84c-109">Dosya adı bir yol ile nitelenebilir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-109">The file name can be qualified with a path.</span></span> <span data-ttu-id="3f84c-110">`filename`Çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="3f84c-110">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="3f84c-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-111">Required.</span></span> <span data-ttu-id="3f84c-112">İçindeki etiketlerin yolu, etikete yol `filename` açar `name` .</span><span class="sxs-lookup"><span data-stu-id="3f84c-112">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="3f84c-113">Yolu çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="3f84c-113">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="3f84c-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-114">Required.</span></span> <span data-ttu-id="3f84c-115">Yorumlarla önce gelen etiketteki ad belirleyicisi.</span><span class="sxs-lookup"><span data-stu-id="3f84c-115">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="3f84c-116">`Name` , olur `id` .</span><span class="sxs-lookup"><span data-stu-id="3f84c-116">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="3f84c-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-117">Required.</span></span> <span data-ttu-id="3f84c-118">Açıklamaların önündeki etiketin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3f84c-118">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="3f84c-119">KIMLIĞI tek tırnak işareti (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="3f84c-119">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f84c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f84c-120">Remarks</span></span>  

 <span data-ttu-id="3f84c-121">`<include>`Kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f84c-121">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="3f84c-122">Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-122">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="3f84c-123">`<include>`Etıketı W3C XML Path Language (XPath) sürüm 1,0 önerisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3f84c-123">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="3f84c-124">Kullanımı özelleştirmenin yolları hakkında daha fazla bilgi için `<include>` bkz <https://www.w3.org/TR/xpath> ..</span><span class="sxs-lookup"><span data-stu-id="3f84c-124">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f84c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f84c-125">Example</span></span>  

 <span data-ttu-id="3f84c-126">Bu örnek, `<include>` adlı bir dosyadan üye belge açıklamalarını içeri aktarmak için etiketini kullanır `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="3f84c-126">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="3f84c-127">Biçimi `commentFile.xml` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3f84c-127">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f84c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f84c-128">See also</span></span>

- [<span data-ttu-id="3f84c-129">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="3f84c-129">XML Comment Tags</span></span>](index.md)
