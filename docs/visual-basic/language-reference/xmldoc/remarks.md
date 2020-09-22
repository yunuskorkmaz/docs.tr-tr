---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 70078752495240ab8c72fe1bbecdca554166fb22
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866420"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="aaf1b-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaf1b-101">\<remarks> (Visual Basic)</span></span>

<span data-ttu-id="aaf1b-102">Üye için bir açıklamalar bölümü belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaf1b-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf1b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaf1b-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf1b-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aaf1b-104">Parameters</span></span>  

 `description`  
 <span data-ttu-id="aaf1b-105">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="aaf1b-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf1b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaf1b-106">Remarks</span></span>  

 <span data-ttu-id="aaf1b-107">`<remarks>`İle belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için etiketini kullanın [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="aaf1b-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="aaf1b-108">Bu bilgiler Nesne Tarayıcısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aaf1b-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="aaf1b-109">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="aaf1b-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="aaf1b-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="aaf1b-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf1b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="aaf1b-111">Example</span></span>  

 <span data-ttu-id="aaf1b-112">Bu örnek, `<remarks>` yönteminin ne yaptığını açıklamak için etiketini kullanır `UpdateRecord` .</span><span class="sxs-lookup"><span data-stu-id="aaf1b-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf1b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaf1b-113">See also</span></span>

- [<span data-ttu-id="aaf1b-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="aaf1b-114">XML Comment Tags</span></span>](index.md)
