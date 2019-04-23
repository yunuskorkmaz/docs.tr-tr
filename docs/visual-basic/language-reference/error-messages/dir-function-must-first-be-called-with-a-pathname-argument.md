---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: d255b8dddd098835764f72b8a166eaa08b0353df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767896"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="8066b-102">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="8066b-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="8066b-103">Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="8066b-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="8066b-104">İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8066b-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8066b-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8066b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="8066b-106">Tedarik bir `PathName` işlev çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="8066b-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8066b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8066b-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
