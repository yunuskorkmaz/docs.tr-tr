---
title: '&lt;verir&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598371"
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="c3912-102">&lt;verir&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3912-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="c3912-103">Özellik veya işlev dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3912-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3912-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3912-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3912-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3912-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c3912-106">Dönüş değeri açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c3912-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3912-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3912-107">Remarks</span></span>  
 <span data-ttu-id="c3912-108">Kullanım `<returns>` dönüş değeri tanımlamak bir yöntem bildirimi açıklamasını etiketinde.</span><span class="sxs-lookup"><span data-stu-id="c3912-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="c3912-109">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="c3912-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3912-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3912-110">Example</span></span>  
 <span data-ttu-id="c3912-111">Bu örnekte `<returns>` ne açıklamak için etiket `DoesRecordExist` işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3912-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c3912-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3912-112">See Also</span></span>  
 [<span data-ttu-id="c3912-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c3912-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
