---
title: 'Nasıl yapılır: (Visual Basic) aşırı yüklenmiş bir yordamı çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 8320bc550c818fd2bea53f75107709eab8456096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706423"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="be4c8-102">Nasıl yapılır: (Visual Basic) aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="be4c8-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="be4c8-103">Bir yordamı aşırı yükleme çağrısının esneklik avantajlarındandır.</span><span class="sxs-lookup"><span data-stu-id="be4c8-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="be4c8-104">Çağıran kod, yordama geçirin ve ardından bunu geçirerek hangi bağımsız değişkenleri ne olursa olsun bir tek yordam adı çağırmak için gereken bilgileri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be4c8-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="be4c8-105">Tanımlanan birden fazla sürümü olan bir yordam çağırmak için</span><span class="sxs-lookup"><span data-stu-id="be4c8-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="be4c8-106">Çağıran kod içinde yordama geçirmeye hangi verileri belirler.</span><span class="sxs-lookup"><span data-stu-id="be4c8-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="be4c8-107">Yordam çağrısı bağımsız değişken listesinde veriyi sunmaktan normal bir şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="be4c8-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="be4c8-108">Bağımsız değişken parametre listesinde yordamı için tanımlanan sürümlerinden birini eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="be4c8-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="be4c8-109">Yordam çağırmak için hangi sürümünü gerekmez.</span><span class="sxs-lookup"><span data-stu-id="be4c8-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="be4c8-110">Visual Basic, bağımsız değişken listesi ile eşleşen sürüm denetim geçer.</span><span class="sxs-lookup"><span data-stu-id="be4c8-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="be4c8-111">Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="be4c8-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="be4c8-112">Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya `Integer`ve ardından her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="be4c8-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="be4c8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be4c8-113">See also</span></span>
- [<span data-ttu-id="be4c8-114">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="be4c8-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="be4c8-115">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="be4c8-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="be4c8-116">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="be4c8-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="be4c8-117">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="be4c8-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="be4c8-118">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="be4c8-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="be4c8-119">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="be4c8-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="be4c8-120">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="be4c8-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="be4c8-121">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="be4c8-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="be4c8-122">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="be4c8-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="be4c8-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="be4c8-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
