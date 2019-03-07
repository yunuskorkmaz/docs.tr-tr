---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cbb8e3b1e67150473159835ba2cd58d9ddf0c1c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479019"
---
# <a name="para-visual-basic"></a><span data-ttu-id="138e4-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="138e4-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="138e4-103">İçerik paragraf olarak biçimlendirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="138e4-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="138e4-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="138e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="138e4-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="138e4-106">Paragraf metni.</span><span class="sxs-lookup"><span data-stu-id="138e4-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="138e4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="138e4-107">Remarks</span></span>  
 <span data-ttu-id="138e4-108">`<para>` Gibi olan bir etiketi içinde kullanmak için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md), veya [ \<döndürür >](../../../visual-basic/language-reference/xmldoc/returns.md), ve metnin yapısını eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="138e4-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="138e4-109">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="138e4-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="138e4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="138e4-110">Example</span></span>  
 <span data-ttu-id="138e4-111">Bu örnekte `<para>` için Açıklamalar bölümüne ayırmak için etiket `UpdateRecord` iki paragraf yönteme.</span><span class="sxs-lookup"><span data-stu-id="138e4-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="138e4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="138e4-112">See also</span></span>
- [<span data-ttu-id="138e4-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="138e4-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
