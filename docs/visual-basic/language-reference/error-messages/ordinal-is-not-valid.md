---
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593609"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="086e8-102">Sıra sayısı geçerli değil</span><span class="sxs-lookup"><span data-stu-id="086e8-102">Ordinal is not valid</span></span>
<span data-ttu-id="086e8-103">Aramanız için dinamik bağlantı kitaplığı (DLL) gösterilen bir yordamı adı yerine bir sayı kullanmak üzere kullanarak `#num` sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="086e8-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="086e8-104">Bu hata, aşağıdaki olası nedenleri vardır:</span><span class="sxs-lookup"><span data-stu-id="086e8-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="086e8-105">Dönüştürme girişimi `#num` başarısız bir sıra ifadesi.</span><span class="sxs-lookup"><span data-stu-id="086e8-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="086e8-106">`#num` Belirtilen herhangi bir işlev DLL'de belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="086e8-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="086e8-107">Tür kitaplığı geçersiz bir sıra numarası iç kullanımını kaynaklanan geçersiz bir bildirim sahiptir.</span><span class="sxs-lookup"><span data-stu-id="086e8-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="086e8-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="086e8-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="086e8-109">Ada göre yordam çağrısı veya geçerli bir sayı ifadeyi temsil emin olun.</span><span class="sxs-lookup"><span data-stu-id="086e8-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="086e8-110">Emin olun `#num` geçerli bir işlev DLL tanımlar.</span><span class="sxs-lookup"><span data-stu-id="086e8-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="086e8-111">Kodu yorum tarafından soruna yordam çağrısı yalıtma.</span><span class="sxs-lookup"><span data-stu-id="086e8-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="086e8-112">Yazma bir `Declare` yordam ve rapor türü kitaplığı satıcıya sorun bildirimi.</span><span class="sxs-lookup"><span data-stu-id="086e8-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="086e8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="086e8-113">See Also</span></span>  
 [<span data-ttu-id="086e8-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="086e8-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
