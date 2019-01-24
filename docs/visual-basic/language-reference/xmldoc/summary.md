---
title: '&lt;Özet&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 899a3343d9758aab79f5aaa77ede26e92f8c07ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551019"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="6a9e6-102">&lt;Özet&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a9e6-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="6a9e6-103">Üye özetini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a9e6-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a9e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a9e6-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="6a9e6-106">Nesne bir özeti.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9e6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a9e6-107">Remarks</span></span>  
 <span data-ttu-id="6a9e6-108">Kullanım `<summary>` bir türü veya tür üyesi açıklamak için etiket.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="6a9e6-109">Kullanım [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) ek bilgiler bir tür tanımı eklemek için.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="6a9e6-110">Metni `<summary>` etiketi, yalnızca kaynağı olan IntelliSense içinde türü hakkında bilgi ve Nesne Tarayıcısı'nda da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="6a9e6-111">Nesne tarayıcı hakkında daha fazla bilgi için bkz: [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="6a9e6-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="6a9e6-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a9e6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a9e6-113">Example</span></span>  
 <span data-ttu-id="6a9e6-114">Bu örnekte `<summary>` açıklamak için etiket `ResetCounter` yöntemi ve `Counter` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6a9e6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a9e6-115">See also</span></span>
- [<span data-ttu-id="6a9e6-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6a9e6-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
