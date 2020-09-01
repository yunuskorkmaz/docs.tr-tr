---
description: Yöntem parametreleri-C# başvurusu
title: Yöntem parametreleri-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134412"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="752d6-103">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="752d6-103">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="752d6-104">[İçinde](./in-parameter-modifier.md), [ref](./ref.md) veya [Out](./out-parameter-modifier.md)olmadan bir yöntem için belirtilen parametreler, çağrılan yönteme değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="752d6-104">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="752d6-105">Bu değer yönteminde değiştirilebilir, ancak denetim çağıran yordama geri geçtiğinde değiştirilen değer korunmaz.</span><span class="sxs-lookup"><span data-stu-id="752d6-105">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="752d6-106">Bir yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="752d6-106">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="752d6-107">Bu bölümde, yöntem parametrelerini bildirirken kullanabileceğiniz anahtar sözcükler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="752d6-107">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="752d6-108">[params](./params.md) , bu parametrenin değişken sayıda bağımsız değişken götüreolabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="752d6-108">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="752d6-109">[' de](./in-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ancak çağrılan yöntemin yalnızca okuduğunuzu belirtir.</span><span class="sxs-lookup"><span data-stu-id="752d6-109">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="752d6-110">[ref](./ref.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından okunabilir veya yazılabilir olabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="752d6-110">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="752d6-111">[Out](./out-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından yazıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="752d6-111">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="752d6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="752d6-112">See also</span></span>

- [<span data-ttu-id="752d6-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="752d6-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="752d6-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="752d6-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="752d6-115">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="752d6-115">C# Keywords</span></span>](./index.md)
