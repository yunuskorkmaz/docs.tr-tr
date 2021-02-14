---
description: "Hakkında daha fazla bilgi edinin: ' dir ' işlevi önce bir ' PathName ' bağımsız değişkeniyle çağrılmalıdır"
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 076828978b27911a97a4767cde1b1d7b04317a31
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479978"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="9acdd-103">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="9acdd-103">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="9acdd-104">İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez.</span><span class="sxs-lookup"><span data-stu-id="9acdd-104">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="9acdd-105">İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9acdd-105">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9acdd-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9acdd-106">To correct this error</span></span>

- <span data-ttu-id="9acdd-107">`PathName`İşlev çağrısında bir bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9acdd-107">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="9acdd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9acdd-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
