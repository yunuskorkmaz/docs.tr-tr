---
title: Yöntem Parametreleri - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713382"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="54e7e-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="54e7e-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="54e7e-103">Bir yöntem için bildirilen [parametreler,](./in-parameter-modifier.md) [ref](./ref.md) veya [out](./out-parameter-modifier.md), değer olarak adlandırılan yönteme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="54e7e-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="54e7e-104">Yöntemde bu değer değiştirilebilir, ancak denetim arama yordamına geri geçtiğinde değiştirilen değer tutulmaz.</span><span class="sxs-lookup"><span data-stu-id="54e7e-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="54e7e-105">Yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54e7e-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="54e7e-106">Bu bölümde yöntem parametreleri bildirirken kullanabileceğiniz anahtar kelimeler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="54e7e-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="54e7e-107">[params](./params.md) bu parametre bağımsız değişken sayıda bağımsız değişken alabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e7e-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="54e7e-108">bu parametrenin başvuru tarafından geçirildiğini, ancak yalnızca çağrılan yöntemle okunduğunu [belirtir.](./in-parameter-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="54e7e-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="54e7e-109">[ref,](./ref.md) bu parametrenin referans la geçirildiğini ve çağrılan yöntemle okunabileceğini veya yazılabileceğine belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e7e-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="54e7e-110">[bu](./out-parameter-modifier.md) parametrenin başvuru ile geçirildiğini ve çağrılan yöntemle yazıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54e7e-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="54e7e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e7e-111">See also</span></span>

- [<span data-ttu-id="54e7e-112">C# Referans</span><span class="sxs-lookup"><span data-stu-id="54e7e-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54e7e-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="54e7e-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54e7e-114">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="54e7e-114">C# Keywords</span></span>](./index.md)
