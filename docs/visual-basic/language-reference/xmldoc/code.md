---
title: '&lt;kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566313"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="2b60d-102">&lt;kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b60d-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="2b60d-103">Metnin birden çok kod satırlarını olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b60d-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b60d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b60d-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b60d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b60d-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="2b60d-106">Kod olarak işaretlemek için metni.</span><span class="sxs-lookup"><span data-stu-id="2b60d-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b60d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b60d-107">Remarks</span></span>  
 <span data-ttu-id="2b60d-108">Kullanım `<code>` çok satırlı kod olarak belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="2b60d-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="2b60d-109">Kullanım [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) gösteren metin açıklamasını içinde kod olarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="2b60d-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="2b60d-110">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="2b60d-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b60d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b60d-111">Example</span></span>  
 <span data-ttu-id="2b60d-112">Bu örnekte \<kod > kullanmak için örnek kod dahil etmek için etiket `ID` alan.</span><span class="sxs-lookup"><span data-stu-id="2b60d-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2b60d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b60d-113">See also</span></span>
- [<span data-ttu-id="2b60d-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="2b60d-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
