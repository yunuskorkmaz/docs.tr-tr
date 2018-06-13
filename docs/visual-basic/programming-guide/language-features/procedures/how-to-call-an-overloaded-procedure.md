---
title: 'Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 802a312d6ec6640594f3c6b662202d1ffcf2376d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649132"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="b6368-102">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6368-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="b6368-103">Bir yordamı aşırı yükleme avantajı çağrının esneklik olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b6368-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="b6368-104">Çağrıyı yapan kod yordamlara geçirmek ve onu geçirerek hangi bağımsız değişkenleri olsun tek bir yordam adları çağırmak için gereken bilgileri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6368-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="b6368-105">Tanımlanan birden fazla sürümü olan bir yordam çağırma için</span><span class="sxs-lookup"><span data-stu-id="b6368-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="b6368-106">Arama kodda yordamlara geçirmek için hangi verilerin belirler.</span><span class="sxs-lookup"><span data-stu-id="b6368-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="b6368-107">Yordam çağrısı bağımsız değişken listesinde veri sunma normal bir şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="b6368-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="b6368-108">Bağımsız değişkenler yordam için tanımlanan sürümlerinden birini parametre listesinde eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6368-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="b6368-109">Hangi sürümünü çağırmak için yordamının gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b6368-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="b6368-110">Visual Basic, bağımsız değişken listesi eşleşen sürüm denetimi geçirir.</span><span class="sxs-lookup"><span data-stu-id="b6368-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="b6368-111">Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="b6368-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="b6368-112">Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya bir `Integer`ve ardından her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="b6368-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b6368-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6368-113">See Also</span></span>  
 [<span data-ttu-id="b6368-114">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b6368-114">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b6368-115">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="b6368-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b6368-116">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="b6368-116">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="b6368-117">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="b6368-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="b6368-118">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b6368-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="b6368-119">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="b6368-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="b6368-120">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="b6368-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="b6368-121">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="b6368-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="b6368-122">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="b6368-122">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="b6368-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="b6368-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
