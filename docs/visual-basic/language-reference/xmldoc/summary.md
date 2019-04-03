---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 0fbe07884f55b7e6f460929e54520de5f718e1af
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815011"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="4007a-102">\<Özet > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4007a-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="4007a-103">Üye özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4007a-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4007a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4007a-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4007a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4007a-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4007a-106">Nesne bir özeti.</span><span class="sxs-lookup"><span data-stu-id="4007a-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4007a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4007a-107">Remarks</span></span>  
 <span data-ttu-id="4007a-108">Kullanım `<summary>` bir türü veya tür üyesi açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="4007a-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="4007a-109">Kullanım [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) ek bilgiler bir tür tanımı eklemek için.</span><span class="sxs-lookup"><span data-stu-id="4007a-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="4007a-110">Metni `<summary>` etiketi, yalnızca kaynağı olan IntelliSense içinde türü hakkında bilgi ve Nesne Tarayıcısı'nda da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4007a-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="4007a-111">Nesne tarayıcı hakkında daha fazla bilgi için bkz: [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="4007a-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="4007a-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="4007a-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4007a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4007a-113">Example</span></span>  
 <span data-ttu-id="4007a-114">Bu örnekte `<summary>` açıklamak için etiket `ResetCounter` yöntemi ve `Counter` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4007a-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4007a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4007a-115">See also</span></span>

- [<span data-ttu-id="4007a-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="4007a-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
