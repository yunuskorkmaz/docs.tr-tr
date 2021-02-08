---
description: "Hakkında daha fazla bilgi edinin: BC30202: ' Optional ' bekleniyor"
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 543dbf6226d4d298d46764ee506b55e770c91604
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795553"
---
# <a name="bc30202-optional-expected"></a><span data-ttu-id="43bb4-103">BC30202: ' Optional ' bekleniyor</span><span class="sxs-lookup"><span data-stu-id="43bb4-103">BC30202: 'Optional' expected</span></span>

<span data-ttu-id="43bb4-104">Yordam bildiriminde isteğe bağlı bir bağımsız değişken, ardından gerekli bir bağımsız değişken tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="43bb4-104">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="43bb4-105">İsteğe bağlı bağımsız değişkenden sonraki her bağımsız değişken de isteğe bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43bb4-105">Every argument following an optional argument must also be optional.</span></span>

 <span data-ttu-id="43bb4-106">**Hata kimliği:** BC30202</span><span class="sxs-lookup"><span data-stu-id="43bb4-106">**Error ID:** BC30202</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="43bb4-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="43bb4-107">To correct this error</span></span>

- <span data-ttu-id="43bb4-108">Bağımsız değişkenin gerekli olması amaçlanıyorsa, bağımsız değişken listesindeki ilk isteğe bağlı bağımsız değişkenden önce onu taşıyın.</span><span class="sxs-lookup"><span data-stu-id="43bb4-108">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>

- <span data-ttu-id="43bb4-109">Bağımsız değişkenin isteğe bağlı olması amaçlanıyorsa, `Optional` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="43bb4-109">If the argument is intended to be optional, use the `Optional` keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="43bb4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43bb4-110">See also</span></span>

- [<span data-ttu-id="43bb4-111">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="43bb4-111">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
