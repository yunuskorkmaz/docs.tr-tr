---
title: '&lt;özel durum&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: f29b8e01239f46b0d56319ba3da1a8fe179a17e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601159"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="b09bc-102">&lt;özel durum&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b09bc-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="b09bc-103">Hangi özel durum belirtir.</span><span class="sxs-lookup"><span data-stu-id="b09bc-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b09bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b09bc-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b09bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b09bc-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="b09bc-106">Geçerli derleme ortamından kullanılabilir bir özel durum referansı.</span><span class="sxs-lookup"><span data-stu-id="b09bc-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="b09bc-107">Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="b09bc-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="b09bc-108">`member` çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="b09bc-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b09bc-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="b09bc-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b09bc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b09bc-110">Remarks</span></span>  
 <span data-ttu-id="b09bc-111">Kullanım `<exception>` etiketi hangi özel durum belirtin.</span><span class="sxs-lookup"><span data-stu-id="b09bc-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="b09bc-112">Bu etiket için bir yöntem tanımını uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b09bc-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="b09bc-113">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="b09bc-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b09bc-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b09bc-114">Example</span></span>  
 <span data-ttu-id="b09bc-115">Bu örnek kullanır `<exception>` bir özel durum açıklamak için etiket, `IntDivide` işlevi throw.</span><span class="sxs-lookup"><span data-stu-id="b09bc-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b09bc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b09bc-116">See Also</span></span>  
 [<span data-ttu-id="b09bc-117">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="b09bc-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
