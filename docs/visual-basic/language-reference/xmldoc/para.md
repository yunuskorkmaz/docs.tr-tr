---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cb80f4b39bee128790b311732adf1202dbbc6993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601731"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="08666-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08666-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="08666-103">İçeriği bir paragraf olarak biçimlendirilmiş olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08666-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08666-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08666-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08666-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08666-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="08666-106">Paragraf metni.</span><span class="sxs-lookup"><span data-stu-id="08666-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08666-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08666-107">Remarks</span></span>  
 <span data-ttu-id="08666-108">`<para>` Gibi olan bir etiketi kullanmak için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<açıklamalar >](../../../visual-basic/language-reference/xmldoc/remarks.md), veya [ \<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md), ve yapı metne eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="08666-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="08666-109">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="08666-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08666-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="08666-110">Example</span></span>  
 <span data-ttu-id="08666-111">Bu örnekte `<para>` için Açıklamalar bölümüne bölmek için etiket `UpdateRecord` iki paragraf içine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08666-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="08666-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08666-112">See Also</span></span>  
 [<span data-ttu-id="08666-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="08666-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
