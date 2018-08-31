---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331365"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="c7274-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7274-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="c7274-103">Bir sözcük, parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="c7274-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7274-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7274-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7274-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7274-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c7274-106">Başvurmak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="c7274-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="c7274-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="c7274-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7274-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7274-108">Remarks</span></span>  
 <span data-ttu-id="c7274-109">`<paramref>` Etiketi bir sözcüğün bir parametre olduğunu belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7274-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="c7274-110">XML dosyası, bu parametreyi belirgin bir şekilde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7274-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="c7274-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="c7274-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7274-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7274-112">Example</span></span>  
 <span data-ttu-id="c7274-113">Bu örnekte `<paramref>` başvurmak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c7274-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c7274-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7274-114">See Also</span></span>  
 [<span data-ttu-id="c7274-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="c7274-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
