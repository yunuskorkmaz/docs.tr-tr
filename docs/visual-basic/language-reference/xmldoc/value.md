---
title: '&lt;değer&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602465"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="a1411-102">&lt;değer&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1411-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="a1411-103">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1411-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1411-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1411-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1411-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1411-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="a1411-106">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="a1411-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1411-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1411-107">Remarks</span></span>  
 <span data-ttu-id="a1411-108">Kullanım `<value>` bir özelliğini açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="a1411-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="a1411-109">Visual Studio geliştirme ortamında kod Sihirbazı'nı kullanarak bir özelliği eklediğinizde, onu ekleyeceksiniz Not bir [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md) yeni özellik için etiketi.</span><span class="sxs-lookup"><span data-stu-id="a1411-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="a1411-110">Daha sonra el ile eklemeniz bir `<value>` özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="a1411-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="a1411-111">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="a1411-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1411-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1411-112">Example</span></span>  
 <span data-ttu-id="a1411-113">Bu örnekte `<value>` hangi değeri açıklamak için etiket `Counter` özelliği ayrı tutma.</span><span class="sxs-lookup"><span data-stu-id="a1411-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a1411-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1411-114">See Also</span></span>  
 [<span data-ttu-id="a1411-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a1411-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
