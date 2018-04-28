---
title: 'Nasıl yapılır: Yordam Oluşturma (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e23358e26dbc993b0f9290a8491a3c66717b4c6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="9374c-102">Nasıl yapılır: Yordam Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9374c-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="9374c-103">Bir başlangıç bildirimi deyimi arasında bir yordam alın (`Sub` veya `Function`) hem de bitiş bildirimi deyimi (`End Sub` veya `End Function`).</span><span class="sxs-lookup"><span data-stu-id="9374c-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="9374c-104">Tüm yordamın kodu arasında bu deyimleri arasındadır.</span><span class="sxs-lookup"><span data-stu-id="9374c-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="9374c-105">Başlangıç ve bitiş deyimleri dışında herhangi bir yordam olmalıdır bir yordam başka bir yordam içeremez.</span><span class="sxs-lookup"><span data-stu-id="9374c-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="9374c-106">Farklı yerlerde aynı görevi gerçekleştiren kodu varsa, görev bir yordam olarak bir kez yazma ve daha sonra kodunuzda farklı yerlerden çağırın.</span><span class="sxs-lookup"><span data-stu-id="9374c-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="9374c-107">Bir değer döndürmeyen bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9374c-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="9374c-108">Diğer herhangi bir yordam dışında kullanmak bir `Sub` deyimi, arkasından bir `End Sub` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9374c-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="9374c-109">İçinde `Sub` deyimi, izleyin `Sub` yordamı sonra parantez içinde parametre listesi adı olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="9374c-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="9374c-110">Yordam kod deyimleri arasında yerleştirin `Sub` ve `End Sub` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="9374c-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="9374c-111">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9374c-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="9374c-112">Diğer herhangi bir yordam dışında kullanmak bir `Function` deyimi, arkasından bir `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9374c-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="9374c-113">İçinde `Function` deyimi, izleyin `Function` yordamı, ardından parantez parametre listesinde adıyla anahtar sözcüğü ve ardından bir `As` dönüş değeri veri türünü belirten yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9374c-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="9374c-114">Yordam kod deyimleri arasında yerleştirin `Function` ve `End Function` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="9374c-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="9374c-115">Kullanım bir `Return` deyimi çağıran kodu değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9374c-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="9374c-116">Yeni yordamınız kodu eski, yinelenen blok ile bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="9374c-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="9374c-117">Eski kod erişime sahip olduğu bir yerde yeni bir yordam tanımlamak emin olun.</span><span class="sxs-lookup"><span data-stu-id="9374c-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="9374c-118">Çağıran tek bir deyimde olan yinelenen görev gerçekleştirmek deyimleri, eski, yinelenen kod bloğunda Değiştir `Sub` veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="9374c-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="9374c-119">Yordamınız ise bir `Function` bir değer döndüren, çağıran deyiminizde bir değişkende saklamak gibi döndürülen değer, bir eylem gerçekleştirir Aksi takdirde değer kaybolacak emin olun.</span><span class="sxs-lookup"><span data-stu-id="9374c-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9374c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="9374c-120">Example</span></span>  
 <span data-ttu-id="9374c-121">Aşağıdaki `Function` yordamı en uzun taraf veya diğer iki kenara için değerlerine göre bir sağ üçgen hipotenüsü hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9374c-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9374c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9374c-122">See also</span></span>

 [<span data-ttu-id="9374c-123">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9374c-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="9374c-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9374c-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="9374c-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="9374c-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="9374c-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="9374c-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="9374c-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="9374c-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="9374c-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9374c-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9374c-129">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9374c-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="9374c-130">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9374c-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="9374c-131">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="9374c-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="9374c-132">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9374c-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
