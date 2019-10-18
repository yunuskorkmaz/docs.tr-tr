---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524607"
---
# <a name="value-visual-basic"></a><span data-ttu-id="6e5d4-102">\<value > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e5d4-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="6e5d4-103">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e5d4-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e5d4-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6e5d4-106">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e5d4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e5d4-107">Remarks</span></span>  
 <span data-ttu-id="6e5d4-108">Bir özelliği anlatmak için `<value>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="6e5d4-109">Visual Studio geliştirme ortamındaki kod Sihirbazı 'nı kullanarak bir özellik eklediğinizde, yeni özellik için bir [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) etiketi ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="6e5d4-110">Ardından, özelliğin temsil ettiği değeri tanımlayan bir `<value>` etiketini el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6e5d4-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e5d4-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e5d4-112">Example</span></span>  
 <span data-ttu-id="6e5d4-113">Bu örnek, `Counter` özelliğinin hangi değere sahip olduğunu belirlemek için `<value>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6e5d4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e5d4-114">See also</span></span>

- [<span data-ttu-id="6e5d4-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6e5d4-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
