---
title: '&lt;para&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2a034974ed94b18da374fbd372063ea4d575440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="e2c8f-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c8f-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="e2c8f-103">İçeriği bir paragraf olarak biçimlendirilmiş olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2c8f-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2c8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2c8f-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e2c8f-106">Paragraf metni.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2c8f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2c8f-107">Remarks</span></span>  
 <span data-ttu-id="e2c8f-108">`<para>` Gibi olan bir etiketi kullanmak için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md), veya [ \<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md), ve yapı metne eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="e2c8f-109">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c8f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2c8f-110">Example</span></span>  
 <span data-ttu-id="e2c8f-111">Bu örnekte `<para>` için Açıklamalar bölümüne bölmek için etiket `UpdateRecord` iki paragraf içine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e2c8f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c8f-112">See Also</span></span>  
 [<span data-ttu-id="e2c8f-113">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="e2c8f-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
