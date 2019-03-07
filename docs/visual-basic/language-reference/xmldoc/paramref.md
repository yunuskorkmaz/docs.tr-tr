---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 49ed974dabe747c383fa1ffa85371afecc4d2f5d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484290"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="4216c-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4216c-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="4216c-103">Bir sözcük, parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="4216c-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4216c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4216c-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4216c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4216c-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4216c-106">Başvurmak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="4216c-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="4216c-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="4216c-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4216c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4216c-108">Remarks</span></span>  
 <span data-ttu-id="4216c-109">`<paramref>` Etiketi bir sözcüğün bir parametre olduğunu belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4216c-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="4216c-110">XML dosyası, bu parametreyi belirgin bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4216c-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="4216c-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="4216c-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4216c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4216c-112">Example</span></span>  
 <span data-ttu-id="4216c-113">Bu örnekte `<paramref>` başvurmak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4216c-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4216c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4216c-114">See also</span></span>
- [<span data-ttu-id="4216c-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="4216c-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
