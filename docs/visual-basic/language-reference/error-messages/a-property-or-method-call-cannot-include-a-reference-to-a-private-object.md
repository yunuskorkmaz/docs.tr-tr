---
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 00237d795fb62fbae426e0015d8e64d5fabb4c32
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162680"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="7f799-102">Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.</span><span class="sxs-lookup"><span data-stu-id="7f799-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="7f799-103">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="7f799-103">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="7f799-104">İstemci bir işlem dışı bileşenin özelliğini veya yöntemini çağırdı ve bağımsız değişkenlerden biri olarak özel bir nesneye başvuru geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="7f799-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>

- <span data-ttu-id="7f799-105">İşlem dışı bir bileşen, istemcisi üzerinde bir geri çağırma yöntemi çağırdı ve özel bir nesneye başvuru geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="7f799-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>

- <span data-ttu-id="7f799-106">İşlem dışı bir bileşen, bir özel nesneye bir başvuruyu, oluşturduğu bir olayın bağımsız değişkeni olarak geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="7f799-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>

- <span data-ttu-id="7f799-107">İstemci `ByRef` , işlediği bir olayın bağımsız değişkenine özel nesne başvurusu atamaya çalıştı.</span><span class="sxs-lookup"><span data-stu-id="7f799-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7f799-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7f799-108">To correct this error</span></span>

- <span data-ttu-id="7f799-109">Başvuruyu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7f799-109">Remove the reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f799-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f799-110">See also</span></span>

- [<span data-ttu-id="7f799-111">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7f799-111">Private</span></span>](../modifiers/private.md)
