---
description: 'Daha fazla bilgi edinin: nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma (Visual Basic)'
title: 'Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 6a67a598bd4a42964fd8fc01bc22b1b919f5e2a9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472598"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="fb7f2-103">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb7f2-103">How to: Call an Overloaded Procedure (Visual Basic)</span></span>

<span data-ttu-id="fb7f2-104">Bir yordamı aşırı yükleme avantajı, çağrının esnekliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-104">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="fb7f2-105">Çağıran kod, yordama geçmesi için gereken bilgileri elde edebilir ve ardından tek bir yordam adı çağırarak, hangi bağımsız değişken geçirdiğine bakılmaksızın onu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-105">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="fb7f2-106">Birden fazla sürümü tanımlanmış bir yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="fb7f2-106">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="fb7f2-107">Çağıran kodda, yordama geçirilecek verileri saptayın.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-107">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="fb7f2-108">Yordam çağrısını, verileri bağımsız değişken listesinde sunarak normal şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-108">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="fb7f2-109">Bağımsız değişkenlerin, yordam için tanımlanan sürümlerden birindeki parametre listesiyle eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-109">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="fb7f2-110">Hangi yordamın hangi sürüme çağrılacağını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-110">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="fb7f2-111">Visual Basic, denetimi bağımsız değişken listenizden eşleşen sürüme geçirir.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-111">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="fb7f2-112">Aşağıdaki örnek, `post` [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama konusunda](./how-to-define-multiple-versions-of-a-procedure.md)belirtilen yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-112">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="fb7f2-113">Müşteri kimliğini edinir, bir veya bir olduğunu belirler `String` `Integer` ve her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-113">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="fb7f2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb7f2-114">See also</span></span>

- [<span data-ttu-id="fb7f2-115">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="fb7f2-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fb7f2-116">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fb7f2-116">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fb7f2-117">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="fb7f2-117">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="fb7f2-118">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="fb7f2-118">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="fb7f2-119">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fb7f2-119">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="fb7f2-120">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="fb7f2-120">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="fb7f2-121">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="fb7f2-121">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="fb7f2-122">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="fb7f2-122">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="fb7f2-123">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="fb7f2-123">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="fb7f2-124">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="fb7f2-124">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
