---
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 64f56b2ecace0ceafb310a175ea605e6959b7256
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871396"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="43375-102">Sıra sayısı geçerli değil</span><span class="sxs-lookup"><span data-stu-id="43375-102">Ordinal is not valid</span></span>

<span data-ttu-id="43375-103">Bir dinamik bağlantı kitaplığı (DLL) çağrısı, söz dizimini kullanarak bir yordam adı yerine bir sayı kullanmak için belirtilmiştir `#num` .</span><span class="sxs-lookup"><span data-stu-id="43375-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="43375-104">Bu hatanın olası nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="43375-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="43375-105">`#num`İfadeyi bir sıraya dönüştürme girişimi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="43375-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="43375-106">`#num`BELIRTILEN dll 'de herhangi bir işlev belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="43375-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="43375-107">Bir tür kitaplığında geçersiz bir sıra numarası iç kullanımına neden olan geçersiz bir bildirim vardır.</span><span class="sxs-lookup"><span data-stu-id="43375-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="43375-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="43375-108">To correct this error</span></span>  
  
1. <span data-ttu-id="43375-109">İfadenin geçerli bir sayıyı temsil ettiğinden emin olun veya yordamı ada göre çağırın.</span><span class="sxs-lookup"><span data-stu-id="43375-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="43375-110">`#num`DLL 'de geçerli bir işlev tanımladığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="43375-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="43375-111">Kodu açıklama ekleyerek soruna neden olan yordam çağrısını yalıtın.</span><span class="sxs-lookup"><span data-stu-id="43375-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="43375-112">`Declare`Yordam için bir ifade yazın ve sorunu tür kitaplığı satıcısına bildirin.</span><span class="sxs-lookup"><span data-stu-id="43375-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43375-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43375-113">See also</span></span>

- [<span data-ttu-id="43375-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="43375-114">Declare Statement</span></span>](../statements/declare-statement.md)
