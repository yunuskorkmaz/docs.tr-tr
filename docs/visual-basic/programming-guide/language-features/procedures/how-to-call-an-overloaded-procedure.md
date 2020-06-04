---
title: 'Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: de101309fa1edaaddc3defc5759d9293fbef684c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388549"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="1d1c9-102">Nasıl yapılır: Aşırı Yüklenmiş Bir Yordamı Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d1c9-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="1d1c9-103">Bir yordamı aşırı yükleme avantajı, çağrının esnekliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="1d1c9-104">Çağıran kod, yordama geçmesi için gereken bilgileri elde edebilir ve ardından tek bir yordam adı çağırarak, hangi bağımsız değişken geçirdiğine bakılmaksızın onu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="1d1c9-105">Birden fazla sürümü tanımlanmış bir yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="1d1c9-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="1d1c9-106">Çağıran kodda, yordama geçirilecek verileri saptayın.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="1d1c9-107">Yordam çağrısını, verileri bağımsız değişken listesinde sunarak normal şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="1d1c9-108">Bağımsız değişkenlerin, yordam için tanımlanan sürümlerden birindeki parametre listesiyle eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="1d1c9-109">Hangi yordamın hangi sürüme çağrılacağını belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="1d1c9-110">Visual Basic, denetimi bağımsız değişken listenizden eşleşen sürüme geçirir.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="1d1c9-111">Aşağıdaki örnek, `post` [nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama konusunda](./how-to-define-multiple-versions-of-a-procedure.md)belirtilen yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="1d1c9-112">Müşteri kimliğini edinir, bir veya bir olduğunu belirler `String` `Integer` ve her iki durumda da aynı yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="1d1c9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d1c9-113">See also</span></span>

- [<span data-ttu-id="1d1c9-114">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="1d1c9-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1d1c9-115">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="1d1c9-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1d1c9-116">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1d1c9-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="1d1c9-117">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="1d1c9-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="1d1c9-118">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1d1c9-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="1d1c9-119">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="1d1c9-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="1d1c9-120">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="1d1c9-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="1d1c9-121">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="1d1c9-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="1d1c9-122">Aşırı yükleme çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="1d1c9-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="1d1c9-123">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="1d1c9-123">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
