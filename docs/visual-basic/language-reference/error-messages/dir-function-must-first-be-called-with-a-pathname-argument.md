---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874456"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="00946-102">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="00946-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="00946-103">İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez.</span><span class="sxs-lookup"><span data-stu-id="00946-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="00946-104">İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="00946-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00946-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="00946-105">To correct this error</span></span>  
  
1. <span data-ttu-id="00946-106">`PathName`İşlev çağrısında bir bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="00946-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00946-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00946-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
