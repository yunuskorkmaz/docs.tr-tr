---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352259"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="2c06a-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c06a-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="2c06a-102">Specifies a remarks section for the member.</span><span class="sxs-lookup"><span data-stu-id="2c06a-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c06a-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c06a-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c06a-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c06a-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2c06a-105">A description of the member.</span><span class="sxs-lookup"><span data-stu-id="2c06a-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c06a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c06a-106">Remarks</span></span>  
 <span data-ttu-id="2c06a-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="2c06a-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="2c06a-108">This information appears in the Object Browser.</span><span class="sxs-lookup"><span data-stu-id="2c06a-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="2c06a-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="2c06a-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2c06a-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="2c06a-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c06a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c06a-111">Example</span></span>  
 <span data-ttu-id="2c06a-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span><span class="sxs-lookup"><span data-stu-id="2c06a-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2c06a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c06a-113">See also</span></span>

- [<span data-ttu-id="2c06a-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="2c06a-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
