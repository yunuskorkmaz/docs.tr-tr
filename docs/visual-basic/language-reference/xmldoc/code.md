---
title: '&lt;kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599758"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="d9080-102">&lt;kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9080-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="d9080-103">Metin kodu çok satırlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9080-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9080-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9080-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9080-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9080-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="d9080-106">Kod olarak işaretlemek için metin.</span><span class="sxs-lookup"><span data-stu-id="d9080-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9080-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9080-107">Remarks</span></span>  
 <span data-ttu-id="d9080-108">Kullanım `<code>` birden fazla satır kodu olarak göstermek için etiket.</span><span class="sxs-lookup"><span data-stu-id="d9080-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="d9080-109">Kullanım [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) belirten bir açıklama metni kodu olarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9080-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="d9080-110">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="d9080-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9080-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9080-111">Example</span></span>  
 <span data-ttu-id="d9080-112">Bu örnekte \<kodu > kullanmaya yönelik örnek kod dahil etmek için etiket `ID` alan.</span><span class="sxs-lookup"><span data-stu-id="d9080-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d9080-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9080-113">See Also</span></span>  
 [<span data-ttu-id="d9080-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d9080-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
