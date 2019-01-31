---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 828c715d9aaceef17d030113e7eda302f025ca9d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282600"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="584a7-102">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="584a7-102">'Dir' function must first be called with a 'PathName' argument</span></span>
<span data-ttu-id="584a7-103">Bir ilk çağrı `Dir` işlevi içermez `PathName` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="584a7-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="584a7-104">İlk çağrıda `Dir` içermelidir bir `PathName`, ancak sonraki çağrılar `Dir` sonraki öğeyi almak için parametreleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="584a7-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="584a7-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="584a7-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="584a7-106">Tedarik bir `PathName` işlev çağrısında bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="584a7-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584a7-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="584a7-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
