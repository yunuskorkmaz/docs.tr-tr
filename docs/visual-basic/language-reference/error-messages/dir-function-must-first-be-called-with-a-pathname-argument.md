---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323648"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="edba5-102">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="edba5-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="edba5-103">Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="edba5-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="edba5-104">İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="edba5-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="edba5-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="edba5-105">To correct this error</span></span>  
  
1. <span data-ttu-id="edba5-106">Tedarik bir `PathName` işlev çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="edba5-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edba5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edba5-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
