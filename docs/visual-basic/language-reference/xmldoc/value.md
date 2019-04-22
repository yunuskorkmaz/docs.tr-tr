---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 2938d485bf6c547c792431b93fc8959c9c36befa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821420"
---
# <a name="value-visual-basic"></a><span data-ttu-id="ae2d1-102">\<Değer > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae2d1-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="ae2d1-103">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae2d1-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae2d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae2d1-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="ae2d1-106">Bir özellik için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae2d1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae2d1-107">Remarks</span></span>  
 <span data-ttu-id="ae2d1-108">Kullanım `<value>` bir özelliği açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="ae2d1-109">Visual Studio geliştirme ortamında kod Sihirbazı'nı kullanarak bir özelliği eklediğinizde, bu ekleyeceğini unutmayın bir [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md) yeni bir özellik için etiket.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="ae2d1-110">Daha sonra el ile eklemeniz bir `<value>` özelliği temsil eden bir değeri açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="ae2d1-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae2d1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae2d1-112">Example</span></span>  
 <span data-ttu-id="ae2d1-113">Bu örnekte `<value>` hangi değeri açıklamak için etiket `Counter` özelliği tutar.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ae2d1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae2d1-114">See also</span></span>

- [<span data-ttu-id="ae2d1-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="ae2d1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
