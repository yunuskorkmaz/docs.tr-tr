---
title: "Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff5967c1b09ad59f249297b1cf0a4ed900faf4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="a468d-102">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a468d-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="a468d-103">Bir yordamı aşırı yükleme avantajı çağrının esneklik olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a468d-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="a468d-104">Çağrıyı yapan kod yordamlara geçirmek ve onu geçirerek hangi bağımsız değişkenleri olsun tek bir yordam adları çağırmak için gereken bilgileri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a468d-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="a468d-105">Tanımlanan birden fazla sürümü olan bir yordam çağırma için</span><span class="sxs-lookup"><span data-stu-id="a468d-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="a468d-106">Arama kodda yordamlara geçirmek için hangi verilerin belirler.</span><span class="sxs-lookup"><span data-stu-id="a468d-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="a468d-107">Yordam çağrısı bağımsız değişken listesinde veri sunma normal bir şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="a468d-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="a468d-108">Bağımsız değişkenler yordam için tanımlanan sürümlerinden birini parametre listesinde eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a468d-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="a468d-109">Hangi sürümünü çağırmak için yordamının gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a468d-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a468d-110">bağımsız değişken listesi eşleşen sürüm denetimi geçirir.</span><span class="sxs-lookup"><span data-stu-id="a468d-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="a468d-111">Aşağıdaki örnek çağrıları `post` yordam içinde bildirilen [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="a468d-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="a468d-112">Müşteri Kimliği alır, olup olmadığını belirleyen bir `String` veya bir `Integer`ve ardından her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="a468d-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a468d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a468d-113">See Also</span></span>  
 [<span data-ttu-id="a468d-114">Yordamları</span><span class="sxs-lookup"><span data-stu-id="a468d-114">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="a468d-115">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a468d-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="a468d-116">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a468d-116">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="a468d-117">Sorun giderme yordamları</span><span class="sxs-lookup"><span data-stu-id="a468d-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="a468d-118">Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="a468d-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="a468d-119">Nasıl yapılır: isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="a468d-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="a468d-120">Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="a468d-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="a468d-121">Yordamları aşırı yüklemeye ilişkin düşünceler</span><span class="sxs-lookup"><span data-stu-id="a468d-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="a468d-122">Aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="a468d-122">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="a468d-123">Aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="a468d-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
