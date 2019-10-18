---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524668"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="10f8b-102">\<remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10f8b-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="10f8b-103">Üye için bir açıklamalar bölümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="10f8b-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f8b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10f8b-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="10f8b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10f8b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="10f8b-106">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="10f8b-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10f8b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10f8b-107">Remarks</span></span>  
 <span data-ttu-id="10f8b-108">[@No__t_2summary >](../../../visual-basic/language-reference/xmldoc/summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için `<remarks>` etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="10f8b-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="10f8b-109">Bu bilgiler Nesne Tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="10f8b-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="10f8b-110">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="10f8b-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="10f8b-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="10f8b-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f8b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="10f8b-112">Example</span></span>  
 <span data-ttu-id="10f8b-113">Bu örnek, `UpdateRecord` yönteminin ne yaptığını açıklamak için `<remarks>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="10f8b-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="10f8b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f8b-114">See also</span></span>

- [<span data-ttu-id="10f8b-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="10f8b-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
