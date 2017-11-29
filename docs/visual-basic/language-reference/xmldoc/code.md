---
title: '&lt;kod&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7c1d8ab3db0c36c6a2935b9ffbef15e87df5ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="461fc-102">&lt;kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="461fc-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="461fc-103">Metin kodu çok satırlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="461fc-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="461fc-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="461fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="461fc-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="461fc-106">Kod olarak işaretlemek için metin.</span><span class="sxs-lookup"><span data-stu-id="461fc-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="461fc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="461fc-107">Remarks</span></span>  
 <span data-ttu-id="461fc-108">Kullanım `<code>` birden fazla satır kodu olarak göstermek için etiket.</span><span class="sxs-lookup"><span data-stu-id="461fc-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="461fc-109">Kullanım [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) belirten bir açıklama metni kodu olarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="461fc-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="461fc-110">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="461fc-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="461fc-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="461fc-111">Example</span></span>  
 <span data-ttu-id="461fc-112">Bu örnekte \<kodu > kullanmaya yönelik örnek kod dahil etmek için etiket `ID` alan.</span><span class="sxs-lookup"><span data-stu-id="461fc-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="461fc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="461fc-113">See Also</span></span>  
 [<span data-ttu-id="461fc-114">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="461fc-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
