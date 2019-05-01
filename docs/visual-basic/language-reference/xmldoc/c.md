---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938599"
---
# <a name="c-visual-basic"></a><span data-ttu-id="68366-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68366-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="68366-103">Metin açıklama içinde kod olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="68366-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68366-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68366-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="68366-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68366-105">Parameters</span></span>  
  
|<span data-ttu-id="68366-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="68366-106">Parameter</span></span>|<span data-ttu-id="68366-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68366-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="68366-108">Kod olarak belirtmek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="68366-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68366-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68366-109">Remarks</span></span>  
 <span data-ttu-id="68366-110">`<c>` Etiket metin açıklama içinde kod olarak işaretlenmelidir göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="68366-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="68366-111">Kullanım [ \<kod >](../../../visual-basic/language-reference/xmldoc/code.md) çok satırlı kod olarak belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="68366-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="68366-112">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="68366-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68366-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="68366-113">Example</span></span>  
 <span data-ttu-id="68366-114">Bu örnekte `<c>` etiket belirtmek için Özet bölümünde `Counter` kodudur.</span><span class="sxs-lookup"><span data-stu-id="68366-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="68366-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68366-115">See also</span></span>

- [<span data-ttu-id="68366-116">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="68366-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
