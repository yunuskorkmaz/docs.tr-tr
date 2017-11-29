---
title: "&lt;özel durum&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="1962d-102">&lt;özel durum&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1962d-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="1962d-103">Hangi özel durum belirtir.</span><span class="sxs-lookup"><span data-stu-id="1962d-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1962d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1962d-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1962d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1962d-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="1962d-106">Geçerli derleme ortamından kullanılabilir bir özel durum referansı.</span><span class="sxs-lookup"><span data-stu-id="1962d-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="1962d-107">Belirtilen özel durum var ve çevirir derleyici denetler `member` XML çıktısında kurallı öğesi adı.</span><span class="sxs-lookup"><span data-stu-id="1962d-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="1962d-108">`member`çift tırnak işaretleri içinde görünmesi gerekir ("").</span><span class="sxs-lookup"><span data-stu-id="1962d-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="1962d-109">Bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="1962d-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1962d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1962d-110">Remarks</span></span>  
 <span data-ttu-id="1962d-111">Kullanım `<exception>` etiketi hangi özel durum belirtin.</span><span class="sxs-lookup"><span data-stu-id="1962d-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="1962d-112">Bu etiket için bir yöntem tanımını uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1962d-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="1962d-113">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="1962d-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1962d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1962d-114">Example</span></span>  
 <span data-ttu-id="1962d-115">Bu örnek kullanır `<exception>` bir özel durum açıklamak için etiket, `IntDivide` işlevi throw.</span><span class="sxs-lookup"><span data-stu-id="1962d-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1962d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1962d-116">See Also</span></span>  
 [<span data-ttu-id="1962d-117">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="1962d-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
