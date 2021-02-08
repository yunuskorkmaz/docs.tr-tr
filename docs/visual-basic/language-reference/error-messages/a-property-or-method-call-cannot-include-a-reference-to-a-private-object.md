---
description: 'Hakkında daha fazla bilgi edinin: bir özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken olarak veya dönüş değeri olarak başvuru içeremez'
title: Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 8fe570c9ed789a5bac36aafa9b1ec2f507a55d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797204"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="b5db8-103">Özellik veya yöntem çağrısı, bir özel nesneye bağımsız değişken ya da dönüş değeri olarak başvuru içeremez.</span><span class="sxs-lookup"><span data-stu-id="b5db8-103">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="b5db8-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="b5db8-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="b5db8-105">İstemci bir işlem dışı bileşenin özelliğini veya yöntemini çağırdı ve bağımsız değişkenlerden biri olarak özel bir nesneye başvuru geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="b5db8-105">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>

- <span data-ttu-id="b5db8-106">İşlem dışı bir bileşen, istemcisi üzerinde bir geri çağırma yöntemi çağırdı ve özel bir nesneye başvuru geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="b5db8-106">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>

- <span data-ttu-id="b5db8-107">İşlem dışı bir bileşen, bir özel nesneye bir başvuruyu, oluşturduğu bir olayın bağımsız değişkeni olarak geçirmeye çalıştı.</span><span class="sxs-lookup"><span data-stu-id="b5db8-107">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>

- <span data-ttu-id="b5db8-108">İstemci `ByRef` , işlediği bir olayın bağımsız değişkenine özel nesne başvurusu atamaya çalıştı.</span><span class="sxs-lookup"><span data-stu-id="b5db8-108">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b5db8-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b5db8-109">To correct this error</span></span>

- <span data-ttu-id="b5db8-110">Başvuruyu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b5db8-110">Remove the reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5db8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5db8-111">See also</span></span>

- [<span data-ttu-id="b5db8-112">Özel</span><span class="sxs-lookup"><span data-stu-id="b5db8-112">Private</span></span>](../modifiers/private.md)
