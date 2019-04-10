---
title: Sıra sayısı geçerli değil
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 28f78161e14604c1f59872801855ccc918faec58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299260"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="ba3d3-102">Sıra sayısı geçerli değil</span><span class="sxs-lookup"><span data-stu-id="ba3d3-102">Ordinal is not valid</span></span>
<span data-ttu-id="ba3d3-103">Çağrınız bir dinamik bağlantı kitaplığı (DLL) belirtilen bir sayıyı bir yordam adı yerine kullanılacak kullanarak `#num` söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="ba3d3-104">Bu hata, aşağıdaki olası nedenleri vardır:</span><span class="sxs-lookup"><span data-stu-id="ba3d3-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="ba3d3-105">Dönüştürülecek girişiminde `#num` başarısız bir sıra ifadesi.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="ba3d3-106">`#num` Belirtilen herhangi bir işlev DLL'de belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="ba3d3-107">Bir tür kitaplığı içinde geçersiz bir sıra numarası, iç kullanımından kaynaklanan geçersiz bir bildirim var.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba3d3-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ba3d3-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ba3d3-109">İfade geçerli bir sayı temsil ettiğinden emin olun veya yordam adına göre arama.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="ba3d3-110">Emin `#num` DLL içinde geçerli bir işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="ba3d3-111">Kodu açıklama olarak ekleyerek soruna yordam çağrısı yalıtın.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="ba3d3-112">Yazma bir `Declare` yordam ve rapor türü kitaplığı satıcıya sorun için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3d3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba3d3-113">See also</span></span>

- [<span data-ttu-id="ba3d3-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="ba3d3-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
