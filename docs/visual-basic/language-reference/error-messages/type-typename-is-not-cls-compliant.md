---
description: 'Hakkında daha fazla bilgi edinin: BC40041: Type <typename> CLS uyumlu değil'
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: a1e807dba64f2fce70b0fb39147087d91ca80fbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675045"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a><span data-ttu-id="48a8f-103">BC40041: tür \<typename> CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="48a8f-103">BC40041: Type \<typename> is not CLS-compliant</span></span>

<span data-ttu-id="48a8f-104">Değişken, özellik veya işlev dönüşü, CLS uyumlu olmayan bir veri türü ile birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48a8f-104">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>

 <span data-ttu-id="48a8f-105">Bir uygulamanın [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a8f-105">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>

 <span data-ttu-id="48a8f-106">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="48a8f-106">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="48a8f-107">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="48a8f-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="48a8f-108">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="48a8f-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="48a8f-109">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="48a8f-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="48a8f-110">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="48a8f-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="48a8f-111">**Hata kimliği:** BC40041</span><span class="sxs-lookup"><span data-stu-id="48a8f-111">**Error ID:** BC40041</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="48a8f-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="48a8f-112">To correct this error</span></span>

- <span data-ttu-id="48a8f-113">Uygulamanızın CLS uyumlu olması gerekiyorsa, bu öğenin veri türünü en yakın CLS uyumlu türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48a8f-113">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="48a8f-114">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48a8f-114">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="48a8f-115">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="48a8f-115">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="48a8f-116">Uygulamanızın CLS uyumlu olması gerekmiyorsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="48a8f-116">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="48a8f-117">Bununla birlikte, uyumsuzluğun farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48a8f-117">You should be aware of its noncompliance, however.</span></span>
