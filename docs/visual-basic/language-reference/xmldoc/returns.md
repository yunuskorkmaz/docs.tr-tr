---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 5a0ff0da7cf26a1cea75a5b2e4678593d9b72f54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827172"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="c518d-102">\<döndürür > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c518d-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="c518d-103">Özellik veya işlev dönüş değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c518d-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c518d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c518d-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c518d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c518d-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c518d-106">Dönüş değeri bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c518d-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c518d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c518d-107">Remarks</span></span>  
 <span data-ttu-id="c518d-108">Kullanım `<returns>` dönüş değeri tanımlamak bir yöntem bildiriminde yorum etiketi.</span><span class="sxs-lookup"><span data-stu-id="c518d-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="c518d-109">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="c518d-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c518d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c518d-110">Example</span></span>  
 <span data-ttu-id="c518d-111">Bu örnekte `<returns>` ne açıklamak için etiket `DoesRecordExist` işlevi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c518d-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c518d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c518d-112">See also</span></span>

- [<span data-ttu-id="c518d-113">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c518d-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
