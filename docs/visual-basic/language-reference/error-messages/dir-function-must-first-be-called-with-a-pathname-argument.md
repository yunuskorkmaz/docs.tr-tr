---
description: "' PathName ' işlevi hakkında daha fazla bilgi için önce ' PathName ' bağımsız değişkeniyle çağrılmalıdır"
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: ee492a269d41e8c9fe1fddbd59210b59fbe8618c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796593"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="fe732-103">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="fe732-103">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="fe732-104">İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez.</span><span class="sxs-lookup"><span data-stu-id="fe732-104">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="fe732-105">İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe732-105">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fe732-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fe732-106">To correct this error</span></span>

- <span data-ttu-id="fe732-107">`PathName`İşlev çağrısında bir bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="fe732-107">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe732-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe732-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
