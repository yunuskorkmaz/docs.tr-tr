---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826619"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="5f468-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f468-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="5f468-103">Bir veya daha fazla bildirilmiş üye değişkenleri, olayları tetikleyebilen bir sınıf örneğine başvurduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f468-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f468-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f468-104">Remarks</span></span>  
 <span data-ttu-id="5f468-105">Bir değişken kullanarak tanımlandığında `WithEvents`, bir yöntem kullanarak değişkenin olaylarını işler bildirimli olarak belirtebilirsiniz `Handles` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5f468-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="5f468-106">Kullanabileceğiniz `WithEvents` yalnızca düzeyinde sınıfı veya modülü.</span><span class="sxs-lookup"><span data-stu-id="5f468-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="5f468-107">Bildirim bağlamı başka bir deyişle bir `WithEvents` değişken bir sınıf veya modül olmalıdır ve bir kaynak dosyası, ad alanı, yapı ya da yordamın olamaz.</span><span class="sxs-lookup"><span data-stu-id="5f468-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="5f468-108">Kullanamazsınız `WithEvents` yapı üyesi üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5f468-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="5f468-109">Yalnızca bağımsız değişkenleri bildirebilirsiniz; dizi değildir — ile `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="5f468-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5f468-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="5f468-110">Rules</span></span>  
  
-   <span data-ttu-id="5f468-111">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="5f468-111">**Element Types.**</span></span> <span data-ttu-id="5f468-112">Bildirmeniz gerekir `WithEvents` kabul edebilir, böylece nesne değişkenleri olmasını değişkenleri sınıfı örneği.</span><span class="sxs-lookup"><span data-stu-id="5f468-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="5f468-113">Ancak, bunları olarak bildiremezsiniz `Object`.</span><span class="sxs-lookup"><span data-stu-id="5f468-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="5f468-114">Bunları, olayları tetikleyebilen belirli sınıf olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f468-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="5f468-115">`WithEvents` Bu bağlamda değiştirici kullanılabilir: [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5f468-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f468-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f468-116">See also</span></span>

- [<span data-ttu-id="5f468-117">İşleme</span><span class="sxs-lookup"><span data-stu-id="5f468-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="5f468-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="5f468-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="5f468-119">Olaylar</span><span class="sxs-lookup"><span data-stu-id="5f468-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
