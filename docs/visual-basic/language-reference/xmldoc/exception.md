---
title: '&lt;özel durum&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 047805ad91d87550da80448fd10883ae58647bd6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081294"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="3b508-102">&lt;özel durum&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b508-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="3b508-103">Hangi özel durumlar atılabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b508-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b508-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b508-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3b508-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b508-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="3b508-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="3b508-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="3b508-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="3b508-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="3b508-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="3b508-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3b508-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="3b508-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b508-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b508-110">Remarks</span></span>  
 <span data-ttu-id="3b508-111">Kullanım `<exception>` hangi özel durumlar atılabilir belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="3b508-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="3b508-112">Bu etiket, bir yöntem tanımına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3b508-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="3b508-113">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="3b508-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b508-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b508-114">Example</span></span>  
 <span data-ttu-id="3b508-115">Bu örnekte `<exception>` açıklayan bir özel durum etiketi, `IntDivide` işlevi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b508-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3b508-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b508-116">See Also</span></span>  
 [<span data-ttu-id="3b508-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="3b508-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
