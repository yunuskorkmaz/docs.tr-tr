---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875180"
---
# <a name="value-visual-basic"></a><span data-ttu-id="41e4b-101">\<value> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41e4b-101">\<value> (Visual Basic)</span></span>

<span data-ttu-id="41e4b-102">Bir özelliğin açıklamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41e4b-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e4b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41e4b-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e4b-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41e4b-104">Parameters</span></span>  

 `property-description`  
 <span data-ttu-id="41e4b-105">Özelliği için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="41e4b-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e4b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41e4b-106">Remarks</span></span>  

 <span data-ttu-id="41e4b-107">`<value>`Bir özelliği anlatmak için etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="41e4b-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="41e4b-108">Visual Studio geliştirme ortamındaki kod Sihirbazı 'nı kullanarak bir özellik eklediğinizde, [\<summary>](summary.md) yeni özellik için bir etiket ekleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="41e4b-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](summary.md) tag for the new property.</span></span> <span data-ttu-id="41e4b-109">Ardından `<value>` , özelliğin temsil ettiği değeri tanımlayacak şekilde el ile bir etiket eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="41e4b-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="41e4b-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="41e4b-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41e4b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="41e4b-111">Example</span></span>  

 <span data-ttu-id="41e4b-112">Bu örnek, `<value>` özelliğin hangi değere sahip olduğunu belirlemek için etiketini kullanır `Counter` .</span><span class="sxs-lookup"><span data-stu-id="41e4b-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="41e4b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41e4b-113">See also</span></span>

- [<span data-ttu-id="41e4b-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="41e4b-114">XML Comment Tags</span></span>](index.md)
