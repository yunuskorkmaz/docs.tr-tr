---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: df8749ca9d6c92cf9ef95f03eea2704812ff495a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872879"
---
# <a name="include-visual-basic"></a><span data-ttu-id="54dc4-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54dc4-101">\<include> (Visual Basic)</span></span>

<span data-ttu-id="54dc4-102">Kaynak kodunuzda türleri ve üyeleri açıklayan başka bir dosya anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54dc4-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54dc4-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="54dc4-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54dc4-104">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="54dc4-105">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-105">Required.</span></span> <span data-ttu-id="54dc4-106">Belgeleri içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="54dc4-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="54dc4-107">Dosya adı bir yol ile nitelenebilir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="54dc4-108">`filename`Çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="54dc4-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="54dc4-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-109">Required.</span></span> <span data-ttu-id="54dc4-110">İçindeki etiketlerin yolu, etikete yol `filename` açar `name` .</span><span class="sxs-lookup"><span data-stu-id="54dc4-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="54dc4-111">Yolu çift tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="54dc4-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="54dc4-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-112">Required.</span></span> <span data-ttu-id="54dc4-113">Yorumlarla önce gelen etiketteki ad belirleyicisi.</span><span class="sxs-lookup"><span data-stu-id="54dc4-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="54dc4-114">`Name` , olur `id` .</span><span class="sxs-lookup"><span data-stu-id="54dc4-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="54dc4-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-115">Required.</span></span> <span data-ttu-id="54dc4-116">Açıklamaların önündeki etiketin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="54dc4-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="54dc4-117">KIMLIĞI tek tırnak işareti (' ') içine alın.</span><span class="sxs-lookup"><span data-stu-id="54dc4-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54dc4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54dc4-118">Remarks</span></span>  

 <span data-ttu-id="54dc4-119">`<include>`Kaynak kodunuzda türleri ve üyeleri tanımlayan başka bir dosyadaki açıklamalara başvurmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54dc4-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="54dc4-120">Bu, belge açıklamalarını doğrudan kaynak kodu dosyanıza yerleştirmeye alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="54dc4-121">`<include>`Etıketı W3C XML Path Language (XPath) sürüm 1,0 önerisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="54dc4-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="54dc4-122">Kullanımı özelleştirmenin yolları hakkında daha fazla bilgi için `<include>` bkz <https://www.w3.org/TR/xpath> ..</span><span class="sxs-lookup"><span data-stu-id="54dc4-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54dc4-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="54dc4-123">Example</span></span>  

 <span data-ttu-id="54dc4-124">Bu örnek, `<include>` adlı bir dosyadan üye belge açıklamalarını içeri aktarmak için etiketini kullanır `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="54dc4-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="54dc4-125">Biçimi `commentFile.xml` aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="54dc4-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54dc4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54dc4-126">See also</span></span>

- [<span data-ttu-id="54dc4-127">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="54dc4-127">XML Comment Tags</span></span>](index.md)
