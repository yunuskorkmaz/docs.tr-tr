---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: yordam oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: bca5ad24e845600642429273f6053787dd290b88
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472546"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="a390d-103">Nasıl yapılır: Yordam Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a390d-103">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="a390d-104">Bir yöntemi başlangıç bildirimi ifadesiyle ( `Sub` veya `Function` ) ve bir bitiş bildirimi ifadesiyle ( `End Sub` veya) çevreedersiniz `End Function` .</span><span class="sxs-lookup"><span data-stu-id="a390d-104">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="a390d-105">Tüm yordamın kodu bu deyimler arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="a390d-105">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="a390d-106">Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a390d-106">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="a390d-107">Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a390d-107">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="a390d-108">Değer döndürmeyen bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a390d-108">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="a390d-109">Diğer herhangi bir yordamın dışında, bir ifadesini ve `Sub` ardından bir `End Sub` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a390d-109">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="a390d-110">İfadesinde, `Sub` `Sub` yordam adı ile anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="a390d-110">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="a390d-111">Yordamın kod deyimlerini `Sub` ve deyimlerini arasına yerleştirin `End Sub` .</span><span class="sxs-lookup"><span data-stu-id="a390d-111">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="a390d-112">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a390d-112">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="a390d-113">Diğer herhangi bir yordamın dışında, bir ifadesini ve `Function` ardından bir `End Function` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a390d-113">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="a390d-114">İfadesinde, `Function` `Function` yordamın adı, sonra parantez içindeki parametre listesi ve `As` dönüş değerinin veri türünü belirten yan tümce ile anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="a390d-114">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="a390d-115">Yordamın kod deyimlerini `Function` ve deyimlerini arasına yerleştirin `End Function` .</span><span class="sxs-lookup"><span data-stu-id="a390d-115">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="a390d-116">`Return`Çağırma koduna değeri döndürmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="a390d-116">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="a390d-117">Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="a390d-117">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="a390d-118">Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a390d-118">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="a390d-119">Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri veya yordamı çağıran tek bir deyim ile değiştirin `Sub` `Function` .</span><span class="sxs-lookup"><span data-stu-id="a390d-119">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="a390d-120">Yordamınız bir değer döndürürse bir ise, `Function` çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden, örneğin bir değişkende depolanması, aksi takdirde değerin kaybedildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a390d-120">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="a390d-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a390d-121">Example</span></span>

 <span data-ttu-id="a390d-122">Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="a390d-122">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="a390d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a390d-123">See also</span></span>

- [<span data-ttu-id="a390d-124">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a390d-124">Procedures</span></span>](index.md)
- [<span data-ttu-id="a390d-125">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a390d-125">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="a390d-126">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="a390d-126">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="a390d-127">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="a390d-127">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="a390d-128">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="a390d-128">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="a390d-129">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a390d-129">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a390d-130">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a390d-130">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="a390d-131">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a390d-131">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="a390d-132">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="a390d-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="a390d-133">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a390d-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
