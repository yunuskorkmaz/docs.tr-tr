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
ms.openlocfilehash: f13fdae9617fa2af21978979cad6f90a15140a4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970005"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="f75ba-102">Nasıl yapılır: (Visual Basic) aşırı yüklenmiş bir yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="f75ba-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="f75ba-103">Bir yordamı aşırı yükleme çağrısının esneklik avantajlarındandır.</span><span class="sxs-lookup"><span data-stu-id="f75ba-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="f75ba-104">Çağıran kod, yordama geçirin ve ardından bunu geçirerek hangi bağımsız değişkenleri ne olursa olsun bir tek yordam adı çağırmak için gereken bilgileri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f75ba-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="f75ba-105">Tanımlanan birden fazla sürümü olan bir yordam çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f75ba-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="f75ba-106">Çağıran kod içinde yordama geçirmeye hangi verileri belirler.</span><span class="sxs-lookup"><span data-stu-id="f75ba-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="f75ba-107">Yordam çağrısı bağımsız değişken listesinde veriyi sunmaktan normal bir şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="f75ba-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="f75ba-108">Bağımsız değişken parametre listesinde yordamı için tanımlanan sürümlerinden birini eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f75ba-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="f75ba-109">Yordam çağırmak için hangi sürümünü gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f75ba-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="f75ba-110">Visual Basic, bağımsız değişken listesi ile eşleşen sürüm denetim geçer.</span><span class="sxs-lookup"><span data-stu-id="f75ba-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="f75ba-111">Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="f75ba-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="f75ba-112">Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya `Integer`ve ardından her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="f75ba-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="f75ba-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f75ba-113">See also</span></span>
- [<span data-ttu-id="f75ba-114">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f75ba-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f75ba-115">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f75ba-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f75ba-116">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f75ba-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="f75ba-117">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="f75ba-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="f75ba-118">Nasıl yapılır: Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="f75ba-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="f75ba-119">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="f75ba-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="f75ba-120">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="f75ba-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="f75ba-121">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="f75ba-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="f75ba-122">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="f75ba-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="f75ba-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="f75ba-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
