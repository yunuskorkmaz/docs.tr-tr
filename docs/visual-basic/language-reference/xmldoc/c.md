---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="991f1-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="991f1-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="991f1-103">İçindeki bir açıklama metni kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="991f1-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="991f1-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="991f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="991f1-105">Parameters</span></span>  
  
|<span data-ttu-id="991f1-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="991f1-106">Parameter</span></span>|<span data-ttu-id="991f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="991f1-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="991f1-108">Kod olarak belirtmek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="991f1-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="991f1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="991f1-109">Remarks</span></span>  
 <span data-ttu-id="991f1-110">`<c>` Etiketi bir açıklama metni kodu olarak işaretlenmelidir belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="991f1-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="991f1-111">Kullanım [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) birden fazla satır kodu olarak belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="991f1-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="991f1-112">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="991f1-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="991f1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="991f1-113">Example</span></span>  
 <span data-ttu-id="991f1-114">Bu örnekte `<c>` belirtmek için Özet bölümündeki etiketi `Counter` kodudur.</span><span class="sxs-lookup"><span data-stu-id="991f1-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="991f1-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="991f1-115">See Also</span></span>  
 [<span data-ttu-id="991f1-116">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="991f1-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
