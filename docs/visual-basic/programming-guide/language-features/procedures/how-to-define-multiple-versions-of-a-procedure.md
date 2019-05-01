---
title: 'Nasıl yapılır: Bir yordam (Visual Basic) birden fazla sürümünü tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: fc7a8e18394b904f0c22a80f71dee091d4f786ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863837"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="5897f-102">Nasıl yapılır: Bir yordam (Visual Basic) birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="5897f-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="5897f-103">Bir yordam tarafından birden çok sürümü tanımlayabilirsiniz *aşırı yükleme* , her sürüm için aynı ada ancak farklı parametre listesini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5897f-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="5897f-104">Aşırı yükleme amacı, ada göre ayırmak zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5897f-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="5897f-105">Daha fazla bilgi için [yordam aşırı yüklemesi](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5897f-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="5897f-106">Bir yordamın birden fazla sürümünü tanımlama</span><span class="sxs-lookup"><span data-stu-id="5897f-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="5897f-107">Yazma bir `Sub` veya `Function` bildirim deyimindeki tanımlamak istediğiniz yordamı her sürümü için.</span><span class="sxs-lookup"><span data-stu-id="5897f-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="5897f-108">Her bildiriminde aynı yordam adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5897f-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="5897f-109">Önünde `Sub` veya `Function` anahtar sözcüğü ile her bildirimindeki [aşırı](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5897f-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="5897f-110">İsteğe bağlı olarak atlayabilirsiniz `Overloads` bildirimleri hiçbirinde dahil, ancak bildirimlerinde, her bildiriminde eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5897f-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="5897f-111">Her bildirim deyimindeki burada çağıran kod söz konusu sürüme ait parametre listesi ile eşleşen bağımsız değişkenleri sağlayan özel durumu işlemek için yordamı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="5897f-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="5897f-112">Test etmek hangi parametrelerini çağıran kod tarafından sağlanan yok.</span><span class="sxs-lookup"><span data-stu-id="5897f-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="5897f-113">Visual Basic için yordamı'nın eşleşen sürümünün denetim geçer.</span><span class="sxs-lookup"><span data-stu-id="5897f-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="5897f-114">Yordamı her bir sürümü sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="5897f-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5897f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5897f-115">Example</span></span>  
 <span data-ttu-id="5897f-116">Aşağıdaki örnekte tanımlayan bir `Sub` Müşteri'nin Dengeleme karşı bir işlem göndermeniz için yordamı.</span><span class="sxs-lookup"><span data-stu-id="5897f-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="5897f-117">Kullandığı `Overloads` iki yordamı müşterinin adı ve diğer hesap numarası tarafından kabul eden bir sürümünü tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5897f-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="5897f-118">Çağıran kod olarak ya da Müşteri Kimliği edinebilirsiniz bir `String` veya `Integer`ve sonra her iki durumda da aynı çağıran deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5897f-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="5897f-119">Bu sürümleri çağırma hakkında bilgi için `post` yordamı bkz [nasıl yapılır: Aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="5897f-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5897f-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5897f-120">Compiling the Code</span></span>  
 <span data-ttu-id="5897f-121">Her aşırı yüklü sürümü farklı parametre listesi ancak aynı yordam adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5897f-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5897f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5897f-122">See also</span></span>

- [<span data-ttu-id="5897f-123">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5897f-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5897f-124">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5897f-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5897f-125">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="5897f-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="5897f-126">Nasıl yapılır: İsteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="5897f-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="5897f-127">Nasıl yapılır: Belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="5897f-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="5897f-128">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="5897f-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="5897f-129">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="5897f-129">Overload Resolution</span></span>](./overload-resolution.md)
