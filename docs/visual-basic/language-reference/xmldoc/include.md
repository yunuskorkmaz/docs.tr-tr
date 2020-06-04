---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400117"
---
# <a name="include-visual-basic"></a><span data-ttu-id="9248c-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9248c-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="9248c-102">Kaynak kodunuzda türleri ve üyeleri açıklayan başka bir dosya anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9248c-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9248c-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9248c-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="9248c-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9248c-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="9248c-105">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9248c-105">Required.</span></span> <span data-ttu-id="9248c-106">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="9248c-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="9248c-107">Dosya adı bir yol ile nitelenebilir.</span><span class="sxs-lookup"><span data-stu-id="9248c-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="9248c-108">`filename`Çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="9248c-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="9248c-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9248c-109">Required.</span></span> <span data-ttu-id="9248c-110">İçindeki etiketlerin yolu, etikete yol `filename` açar `name` .</span><span class="sxs-lookup"><span data-stu-id="9248c-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="9248c-111">Yolu çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="9248c-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="9248c-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9248c-112">Required.</span></span> <span data-ttu-id="9248c-113">Yorumlarla önce gelen etiketteki ad belirleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9248c-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="9248c-114">`Name`, olur `id` .</span><span class="sxs-lookup"><span data-stu-id="9248c-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="9248c-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9248c-115">Required.</span></span> <span data-ttu-id="9248c-116">Açıklamaların önündeki etiketin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9248c-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="9248c-117">KIMLIĞI tek tırnak işareti (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="9248c-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9248c-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9248c-118">Remarks</span></span>  
 <span data-ttu-id="9248c-119">`<include>`Kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9248c-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="9248c-120">Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="9248c-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="9248c-121">`<include>`Etıketı W3C XML Path Language (XPath) sürüm 1,0 önerisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9248c-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="9248c-122">Kullanımı özelleştirmenin yolları hakkında daha fazla bilgi için `<include>` bkz <https://www.w3.org/TR/xpath> ..</span><span class="sxs-lookup"><span data-stu-id="9248c-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9248c-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9248c-123">Example</span></span>  
 <span data-ttu-id="9248c-124">Bu örnek, `<include>` adlı bir dosyadan üye belge açıklamalarını içeri aktarmak için etiketini kullanır `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="9248c-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9248c-125">Biçimi `commentFile.xml` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="9248c-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9248c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9248c-126">See also</span></span>

- [<span data-ttu-id="9248c-127">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="9248c-127">XML Comment Tags</span></span>](index.md)
