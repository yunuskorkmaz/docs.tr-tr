---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <value> (Visual Basic)'
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 80a3ef875eea4418d28d60dac1818f3390c361ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640257"
---
# <a name="value-visual-basic"></a><span data-ttu-id="de4f6-103">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de4f6-103">\<value> (Visual Basic)</span></span>

<span data-ttu-id="de4f6-104">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4f6-104">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de4f6-105">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="de4f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de4f6-106">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="de4f6-107">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="de4f6-107">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de4f6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de4f6-108">Remarks</span></span>  

 <span data-ttu-id="de4f6-109">`<value>`Bir özelliği anlatmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="de4f6-109">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="de4f6-110">Visual Studio geliştirme ortamındaki kod Sihirbazı 'nı kullanarak bir özellik eklediğinizde, [\<summary>](summary.md) yeni özellik için bir etiket ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="de4f6-110">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="de4f6-111">Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de4f6-111">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="de4f6-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="de4f6-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de4f6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="de4f6-113">Example</span></span>  

 <span data-ttu-id="de4f6-114">Bu örnek, `<value>` özelliğin hangi değere sahip olduğunu belirlemek için etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="de4f6-114">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="de4f6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de4f6-115">See also</span></span>

- [<span data-ttu-id="de4f6-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="de4f6-116">XML Comment Tags</span></span>](index.md)
