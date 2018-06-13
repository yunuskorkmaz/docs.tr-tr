---
title: '&lt;Özet&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602658"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="0a58f-102">&lt;Özet&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a58f-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="0a58f-103">Üye özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a58f-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a58f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a58f-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a58f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a58f-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0a58f-106">Nesne özeti.</span><span class="sxs-lookup"><span data-stu-id="0a58f-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a58f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a58f-107">Remarks</span></span>  
 <span data-ttu-id="0a58f-108">Kullanım `<summary>` bir tür veya bir tür üyesi açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="0a58f-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="0a58f-109">Kullanım [ \<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md) türü açıklaması için ek bilgiler eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0a58f-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="0a58f-110">Metni `<summary>` etiket IntelliSense türüyle ilgili bilgiler yalnızca kaynağı ve ayrıca nesne tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0a58f-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="0a58f-111">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="0a58f-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="0a58f-112">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="0a58f-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a58f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a58f-113">Example</span></span>  
 <span data-ttu-id="0a58f-114">Bu örnekte `<summary>` açıklamak için etiket `ResetCounter` yöntemi ve `Counter` özelliği.</span><span class="sxs-lookup"><span data-stu-id="0a58f-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0a58f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a58f-115">See Also</span></span>  
 [<span data-ttu-id="0a58f-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="0a58f-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
