---
title: 'Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e8f8e438dc749e7f5f0d33aeaa26dfbcf4c29f3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="d4a71-102">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4a71-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="d4a71-103">Bir yordam çağrısı için bağımsız değişken listesi parantez içinde yordam adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a71-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="d4a71-104">Yordam tanımlar her gerekli parametre için karşılık gelen bir bağımsız değişken sağlayın ve isteğe bağlı olarak bağımsız değişkenleri sağlayın `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d4a71-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="d4a71-105">Sağladığınız değil, bir `Optional` çağrısında parametre, sonraki tüm bağımsız değişkenleri sağlamış olursunuz, onun yerine bağımsız değişken listesinde işaretlemek için virgül içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d4a71-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="d4a71-106">Bir veri türünde bir bağımsız değişken gibi kendi karşılık gelen bir parametre farklı geçirmek istiyorsanız, `Byte` için `String`, tür denetlemesi anahtarı ayarlayabilirsiniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) için `Off`.</span><span class="sxs-lookup"><span data-stu-id="d4a71-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="d4a71-107">Varsa `Option Strict` olan `On`, ya da kullanmalıdır dönüşümleri veya açık dönüşüm anahtar sözcükleri genişletme.</span><span class="sxs-lookup"><span data-stu-id="d4a71-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="d4a71-108">Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d4a71-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="d4a71-109">Daha fazla bilgi için bkz: [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d4a71-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="d4a71-110">Bir yordama bağımsız değişkenlerden biri veya daha fazla geçirmek için</span><span class="sxs-lookup"><span data-stu-id="d4a71-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="d4a71-111">Arama deyiminde parantez yordamı adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="d4a71-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="d4a71-112">Parantez içinde bir bağımsız değişken listesi yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d4a71-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="d4a71-113">Bağımsız değişkenler virgülle ayırın ve yordam tanımlar her gerekli parametre için bir bağımsız değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="d4a71-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="d4a71-114">Her değişken için karşılık gelen bir parametre türü yordamı bir veri türüne dönüştürülebilir değerlendiren geçerli bir ifade tanımlar olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d4a71-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="d4a71-115">Bir parametre olarak tanımlanmışsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md), bağımsız değişken listesinde içerebilir veya onu atlayın.</span><span class="sxs-lookup"><span data-stu-id="d4a71-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="d4a71-116">Yordam atlarsanız, bu parametre için tanımlanan varsayılan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4a71-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="d4a71-117">Bir bağımsız değişken atlarsanız bir `Optional` parametre ve başka bir parametre sonra parametre listesinde, bağımsız değişken listesinde fazladan bir virgül tarafından belirtilmemiş bağımsız değişkeni yerine işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4a71-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="d4a71-118">Aşağıdaki örnek Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.</span><span class="sxs-lookup"><span data-stu-id="d4a71-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     <span data-ttu-id="d4a71-119">Önceki örnekte görüntülenecek ileti dizesi gerekli ilk bağımsız sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4a71-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="d4a71-120">İleti kutusu görüntülenecek düğmeleri belirten isteğe bağlı ikinci parametre için bir bağımsız değişken atlar.</span><span class="sxs-lookup"><span data-stu-id="d4a71-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="d4a71-121">Çağrısı bir değer sağlamaz çünkü `MsgBox` varsayılan değeri kullanır `MsgBoxStyle.OKOnly`, yalnızca görüntüleyen bir **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d4a71-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="d4a71-122">Bağımsız değişken listesinde ikinci virgülle belirtilmemişse ikinci bağımsız değişkeni yerine işaretler ve son dize için isteğe bağlı üçüncü parametresi, geçirilen `MsgBox`, başlık çubuğunda görüntülenecek metni olduğu.</span><span class="sxs-lookup"><span data-stu-id="d4a71-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a71-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4a71-123">See also</span></span>

 [<span data-ttu-id="d4a71-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d4a71-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="d4a71-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="d4a71-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="d4a71-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="d4a71-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="d4a71-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="d4a71-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="d4a71-128">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d4a71-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="d4a71-129">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="d4a71-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="d4a71-130">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d4a71-130">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="d4a71-131">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d4a71-131">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="d4a71-132">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="d4a71-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="d4a71-133">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4a71-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
