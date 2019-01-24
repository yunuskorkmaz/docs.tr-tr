---
title: '&#39;Dir&#39; işlevi önce çağrılmalıdır ile bir &#39;PathName&#39; bağımsız değişken'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518494"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="972fc-102">&#39;Dir&#39; işlevi önce çağrılmalıdır ile bir &#39;PathName&#39; bağımsız değişken</span><span class="sxs-lookup"><span data-stu-id="972fc-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="972fc-103">Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="972fc-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="972fc-104">İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="972fc-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="972fc-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="972fc-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="972fc-106">Tedarik bir `PathName` işlev çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="972fc-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972fc-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="972fc-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
