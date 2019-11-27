---
title: 'Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 83e96e271f6613aa325d59a0ca2fce9fc69fe059
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350481"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="68c78-102">Nasıl yapılır: Bir Yordamın Birden Fazla Sürümünü Tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68c78-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="68c78-103">Aynı adı ancak her sürüm için farklı bir parametre listesini kullanarak, onu *aşırı* yükleyerek birden çok sürümde bir yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68c78-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="68c78-104">Aşırı yükleme amacı, bir yordamın adına göre ayrım yapmadan daha yakından ilgili birkaç sürümünü tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="68c78-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="68c78-105">Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="68c78-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="68c78-106">Bir yordamın birden fazla sürümünü tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="68c78-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="68c78-107">Tanımlamak istediğiniz yordamın her sürümü için bir `Sub` veya `Function` bildirim bildirimi yazın.</span><span class="sxs-lookup"><span data-stu-id="68c78-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="68c78-108">Her bildirimde aynı yordam adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="68c78-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="68c78-109">Her bildirimdeki `Sub` veya `Function` anahtar sözcüğünün önüne [aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="68c78-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="68c78-110">İsteğe bağlı olarak bildirimlerinizde `Overloads` atlayabilirsiniz, ancak bu bildirimi herhangi bir bildirime eklerseniz, her bildirime dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68c78-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="68c78-111">Her bildirim ifadesinin ardından, çağıran kodun bu sürümün parametre listesiyle eşleşen bağımsız değişkenler sağladığı belirli bir durumu işlemek için yordam kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="68c78-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="68c78-112">Çağıran kodun sağladığı parametreleri test etmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="68c78-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="68c78-113">Visual Basic, denetimi prosedürünün eşleşen sürümüne geçirir.</span><span class="sxs-lookup"><span data-stu-id="68c78-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="68c78-114">Yordamın her sürümünü, `End Sub` veya `End Function` ifadesiyle uygun şekilde sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="68c78-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68c78-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="68c78-115">Example</span></span>  
 <span data-ttu-id="68c78-116">Aşağıdaki örnek, bir müşterinin bakiyesine karşı bir işlem göndermek için bir `Sub` yordamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68c78-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="68c78-117">Yordamın, müşteriyi adı ve diğer hesap numarasına göre kabul eden iki sürümü tanımlamak için `Overloads` anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="68c78-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="68c78-118">Çağıran kod, müşteri kimliğini bir `String` veya `Integer`olarak edinebilir ve sonra aynı çağırma ifadesini her iki durumda da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="68c78-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="68c78-119">`post` yordamının bu sürümlerini çağırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı aşırı yüklenmiş bir yordam](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="68c78-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68c78-120">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="68c78-120">Compiling the Code</span></span>  
 <span data-ttu-id="68c78-121">Aşırı yüklenmiş sürümlerden her birinin aynı yordam adına, ancak farklı bir parametre listesine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="68c78-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c78-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68c78-122">See also</span></span>

- [<span data-ttu-id="68c78-123">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="68c78-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="68c78-124">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="68c78-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="68c78-125">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="68c78-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="68c78-126">Nasıl yapılır: İsteğe Bağlı Parametreler İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="68c78-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="68c78-127">Nasıl yapılır: Belirsiz Sayıda Parametre İsteyen Bir Yordamı Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="68c78-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="68c78-128">Yordamları Aşırı Yüklemeye İlişkin Düşünceler</span><span class="sxs-lookup"><span data-stu-id="68c78-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="68c78-129">Aşırı Yükleme Çözümü</span><span class="sxs-lookup"><span data-stu-id="68c78-129">Overload Resolution</span></span>](./overload-resolution.md)
