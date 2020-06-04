---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400027"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="375a8-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="375a8-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="375a8-102">Üye için bir açıklamalar bölümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="375a8-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="375a8-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="375a8-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="375a8-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="375a8-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="375a8-105">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="375a8-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="375a8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="375a8-106">Remarks</span></span>  
 <span data-ttu-id="375a8-107">`<remarks>`İle belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için etiketini kullanın [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="375a8-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="375a8-108">Bu bilgiler Nesne Tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="375a8-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="375a8-109">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="375a8-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="375a8-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="375a8-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="375a8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="375a8-111">Example</span></span>  
 <span data-ttu-id="375a8-112">Bu örnek, `<remarks>` yönteminin ne yaptığını açıklamak için etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="375a8-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="375a8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="375a8-113">See also</span></span>

- [<span data-ttu-id="375a8-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="375a8-114">XML Comment Tags</span></span>](index.md)
