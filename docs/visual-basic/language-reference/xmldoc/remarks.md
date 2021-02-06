---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <remarks> (Visual Basic)'
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 4b0584abbe85a7ecc73e25dd1f6ec321962b88a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640413"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="e3f9c-103">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3f9c-103">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="e3f9c-104">Üye için bir açıklamalar bölümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-104">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3f9c-105">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3f9c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3f9c-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="e3f9c-107">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-107">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3f9c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3f9c-108">Remarks</span></span>  

 <span data-ttu-id="e3f9c-109">`<remarks>`İle belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için etiketini kullanın [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="e3f9c-109">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="e3f9c-110">Bu bilgiler Nesne Tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-110">This information appears in the Object Browser.</span></span> <span data-ttu-id="e3f9c-111">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e3f9c-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e3f9c-112">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3f9c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3f9c-113">Example</span></span>  

 <span data-ttu-id="e3f9c-114">Bu örnek, `<remarks>` yönteminin ne yaptığını açıklamak için etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="e3f9c-114">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e3f9c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-115">See also</span></span>

- [<span data-ttu-id="e3f9c-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="e3f9c-116">XML Comment Tags</span></span>](index.md)
