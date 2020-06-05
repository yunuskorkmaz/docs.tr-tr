---
title: <typename> türü CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386964"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="f0beb-102">\<typename> türü CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="f0beb-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="f0beb-103">Değişken, özellik veya işlev dönüşü, CLS uyumlu olmayan bir veri türü ile birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0beb-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="f0beb-104">Bir uygulamanın [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için, yalnızca CLS uyumlu türler kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0beb-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="f0beb-105">Aşağıdaki Visual Basic veri türleri CLS uyumlu değildir:</span><span class="sxs-lookup"><span data-stu-id="f0beb-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="f0beb-106">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f0beb-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="f0beb-107">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f0beb-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="f0beb-108">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f0beb-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="f0beb-109">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f0beb-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="f0beb-110">**Hata kimliği:** BC40041</span><span class="sxs-lookup"><span data-stu-id="f0beb-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0beb-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f0beb-111">To correct this error</span></span>  
  
- <span data-ttu-id="f0beb-112">Uygulamanızın CLS uyumlu olması gerekiyorsa, bu öğenin veri türünü en yakın CLS uyumlu türle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f0beb-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="f0beb-113">Örneğin, yerine `UInteger` `Integer` 2.147.483.647 üzerinde değer aralığına ihtiyacınız yoksa, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0beb-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="f0beb-114">Genişletilmiş aralığa ihtiyacınız varsa, `UInteger` ile değiştirebilirsiniz `Long` .</span><span class="sxs-lookup"><span data-stu-id="f0beb-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="f0beb-115">Uygulamanızın CLS uyumlu olması gerekmiyorsa, herhangi bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f0beb-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="f0beb-116">Bununla birlikte, uyumsuzluğun farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0beb-116">You should be aware of its noncompliance, however.</span></span>
