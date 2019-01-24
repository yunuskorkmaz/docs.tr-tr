---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 5932ddb55a4dab48267cdd9b9f321cec8660d77a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662328"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="6ab2c-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ab2c-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="6ab2c-103">İçerik paragraf olarak biçimlendirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ab2c-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ab2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ab2c-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="6ab2c-106">Paragraf metni.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ab2c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ab2c-107">Remarks</span></span>  
 <span data-ttu-id="6ab2c-108">`<para>` Gibi olan bir etiketi içinde kullanmak için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), veya [ \<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md), ve metnin yapısını eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="6ab2c-109">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ab2c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ab2c-110">Example</span></span>  
 <span data-ttu-id="6ab2c-111">Bu örnekte `<para>` için Açıklamalar bölümüne ayırmak için etiket `UpdateRecord` iki paragraf yönteme.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ab2c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ab2c-112">See also</span></span>
- [<span data-ttu-id="6ab2c-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="6ab2c-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
