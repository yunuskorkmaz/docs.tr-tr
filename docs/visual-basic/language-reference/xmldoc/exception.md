---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 157287ce5c85ec51f1711934cf9a5e4f568957ef
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977194"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="d81e3-102">\<Özel Durum > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d81e3-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="d81e3-103">Hangi özel durumlar atılabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="d81e3-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d81e3-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d81e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d81e3-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="d81e3-106">Geçerli derleme ortamdan kullanılabilir bir özel durum başvuru.</span><span class="sxs-lookup"><span data-stu-id="d81e3-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="d81e3-107">Belirtilen özel var ve çevirir derleyici denetler `member` kurallı öğesi adı ' % s'çıkış XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="d81e3-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="d81e3-108">`member` çift tırnak içinde yer almalıdır ("").</span><span class="sxs-lookup"><span data-stu-id="d81e3-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d81e3-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="d81e3-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d81e3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d81e3-110">Remarks</span></span>  
 <span data-ttu-id="d81e3-111">Kullanım `<exception>` hangi özel durumlar atılabilir belirtmek için etiket.</span><span class="sxs-lookup"><span data-stu-id="d81e3-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="d81e3-112">Bu etiket, bir yöntem tanımına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d81e3-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="d81e3-113">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="d81e3-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d81e3-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="d81e3-114">Example</span></span>  
 <span data-ttu-id="d81e3-115">Bu örnekte `<exception>` açıklayan bir özel durum etiketi, `IntDivide` işlevi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d81e3-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d81e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d81e3-116">See also</span></span>
- [<span data-ttu-id="d81e3-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d81e3-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
