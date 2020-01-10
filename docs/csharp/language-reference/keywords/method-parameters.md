---
title: Yöntem parametreleri- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713382"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="acfe0-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="acfe0-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="acfe0-103">[İçinde](./in-parameter-modifier.md), [ref](./ref.md) veya [Out](./out-parameter-modifier.md)olmadan bir yöntem için belirtilen parametreler, çağrılan yönteme değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acfe0-103">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="acfe0-104">Bu değer yönteminde değiştirilebilir, ancak denetim çağıran yordama geri geçtiğinde değiştirilen değer korunmaz.</span><span class="sxs-lookup"><span data-stu-id="acfe0-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="acfe0-105">Bir yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acfe0-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="acfe0-106">Bu bölümde, yöntem parametrelerini bildirirken kullanabileceğiniz anahtar sözcükler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="acfe0-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="acfe0-107">[params](./params.md) , bu parametrenin değişken sayıda bağımsız değişken götüreolabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="acfe0-107">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="acfe0-108">[' de](./in-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ancak çağrılan yöntemin yalnızca okuduğunuzu belirtir.</span><span class="sxs-lookup"><span data-stu-id="acfe0-108">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="acfe0-109">[ref](./ref.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından okunabilir veya yazılabilir olabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="acfe0-109">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="acfe0-110">[Out](./out-parameter-modifier.md) bu parametrenin başvuruya göre geçtiğini ve çağrılan yöntem tarafından yazıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acfe0-110">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="acfe0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acfe0-111">See also</span></span>

- [<span data-ttu-id="acfe0-112">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="acfe0-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="acfe0-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="acfe0-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="acfe0-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="acfe0-114">C# Keywords</span></span>](./index.md)
