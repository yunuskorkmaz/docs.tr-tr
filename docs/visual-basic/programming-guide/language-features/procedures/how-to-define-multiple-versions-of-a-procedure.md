---
title: "Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1abeaa6806252005dd3abfab3ff60bafa0c0cef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="aadb4-102">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aadb4-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="aadb4-103">Birden çok sürümü tarafından bir yordam tanımlayabilirsiniz *aşırı yüklemesi* , aynı adlı ancak farklı parametre listesini her sürüm için kullanma.</span><span class="sxs-lookup"><span data-stu-id="aadb4-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="aadb4-104">Aşırı yükleme amacı, ada göre ayırt zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="aadb4-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="aadb4-105">Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="aadb4-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="aadb4-106">Bir yordamın birden fazla sürümünü tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="aadb4-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="aadb4-107">Yazma bir `Sub` veya `Function` bildirimi deyimi tanımlamak istediğiniz yordamı her sürümü.</span><span class="sxs-lookup"><span data-stu-id="aadb4-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="aadb4-108">Aynı yordamı adı her bildiriminde kullanın.</span><span class="sxs-lookup"><span data-stu-id="aadb4-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="aadb4-109">Öncesinde `Sub` veya `Function` anahtar sözcüğü ile her bildiriminde [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="aadb4-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="aadb4-110">İsteğe bağlı olarak atlayabilirsiniz `Overloads` bildirimlerin hiçbirinde dahil, ancak bildirimlerden, her bildiriminde içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="aadb4-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="aadb4-111">Her bildirim deyimi burada çağıran kodu bu sürüme ait parametre listesi eşleşen bağımsız değişken sağlayan özel durumu işlemek için bir yordam kod yazın.</span><span class="sxs-lookup"><span data-stu-id="aadb4-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="aadb4-112">Test etmek için hangi parametreleri tarafından sağlanan çağıran kodu yok.</span><span class="sxs-lookup"><span data-stu-id="aadb4-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="aadb4-113">yordamınız eşleşen sürümü denetimine geçirir.</span><span class="sxs-lookup"><span data-stu-id="aadb4-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="aadb4-114">Her bir sürümü yordamını sonlandırmak `End Sub` veya `End Function` uygun şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="aadb4-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aadb4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="aadb4-115">Example</span></span>  
 <span data-ttu-id="aadb4-116">Aşağıdaki örnek tanımlayan bir `Sub` Müşteri'nin Bakiye karşı bir işlem sonrası için yordamı.</span><span class="sxs-lookup"><span data-stu-id="aadb4-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="aadb4-117">Kullandığı `Overloads` yordamın adı ve diğer müşteri hesap numarası tarafından kabul eden bir iki sürümünü tanımlamak üzere anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="aadb4-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="aadb4-118">Çağrıyı yapan kod olarak ya da müşteri kimliği elde edebilirsiniz bir `String` veya bir `Integer`ve ardından her iki durumda da aynı arama deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aadb4-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="aadb4-119">Bu sürümleri çağrı hakkında bilgi için `post` yordamı, bkz: [nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="aadb4-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aadb4-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="aadb4-120">Compiling the Code</span></span>  
 <span data-ttu-id="aadb4-121">Aşırı yüklenmiş sürümlerinizi her farklı parametre listesi ancak aynı yordam adı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="aadb4-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadb4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aadb4-122">See Also</span></span>  
 [<span data-ttu-id="aadb4-123">Yordamları</span><span class="sxs-lookup"><span data-stu-id="aadb4-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="aadb4-124">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="aadb4-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="aadb4-125">Sorun giderme yordamları</span><span class="sxs-lookup"><span data-stu-id="aadb4-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="aadb4-126">Nasıl yapılır: isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="aadb4-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="aadb4-127">Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="aadb4-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="aadb4-128">Yordamları aşırı yüklemeye ilişkin düşünceler</span><span class="sxs-lookup"><span data-stu-id="aadb4-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="aadb4-129">Aşırı yükleme çözümü</span><span class="sxs-lookup"><span data-stu-id="aadb4-129">Overload Resolution</span></span>](./overload-resolution.md)
