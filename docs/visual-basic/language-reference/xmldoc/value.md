---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352180"
---
# <a name="value-visual-basic"></a><span data-ttu-id="a947d-101">\<değeri > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a947d-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="a947d-102">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a947d-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a947d-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a947d-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a947d-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a947d-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="a947d-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="a947d-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a947d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a947d-106">Remarks</span></span>  
 <span data-ttu-id="a947d-107">Bir özelliği anlatmak için `<value>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a947d-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="a947d-108">Visual Studio geliştirme ortamındaki kod Sihirbazı 'nı kullanarak bir özellik eklediğinizde, yeni özellik için bir [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) etiketi ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a947d-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="a947d-109">Ardından, özelliğin temsil ettiği değeri tanımlayan bir `<value>` etiketini el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a947d-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="a947d-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a947d-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a947d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a947d-111">Example</span></span>  
 <span data-ttu-id="a947d-112">Bu örnek, `Counter` özelliğinin hangi değere sahip olduğunu belirlemek için `<value>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a947d-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a947d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a947d-113">See also</span></span>

- [<span data-ttu-id="a947d-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="a947d-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
