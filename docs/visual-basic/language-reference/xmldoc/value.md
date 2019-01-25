---
title: '&lt;değer&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 92c8c2ac7b95e97b37c907e3837bc90dac384b33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558949"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="164ee-102">&lt;değer&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="164ee-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="164ee-103">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="164ee-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="164ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="164ee-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="164ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="164ee-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="164ee-106">Bir özellik için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="164ee-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="164ee-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="164ee-107">Remarks</span></span>  
 <span data-ttu-id="164ee-108">Kullanım `<value>` bir özelliği açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="164ee-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="164ee-109">Visual Studio geliştirme ortamında kod Sihirbazı'nı kullanarak bir özelliği eklediğinizde, bu ekleyeceğini unutmayın bir [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md) yeni bir özellik için etiket.</span><span class="sxs-lookup"><span data-stu-id="164ee-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="164ee-110">Daha sonra el ile eklemeniz bir `<value>` özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="164ee-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="164ee-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="164ee-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="164ee-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="164ee-112">Example</span></span>  
 <span data-ttu-id="164ee-113">Bu örnekte `<value>` hangi değeri açıklamak için etiket `Counter` özelliği tutar.</span><span class="sxs-lookup"><span data-stu-id="164ee-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="164ee-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="164ee-114">See also</span></span>
- [<span data-ttu-id="164ee-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="164ee-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
