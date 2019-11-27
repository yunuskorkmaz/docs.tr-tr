---
title: 'Nasıl yapılır: Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344904"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="ffcea-102">Nasıl yapılır: Yordam Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffcea-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="ffcea-103">Bir başlangıç bildirimi bildirimi (`Sub` veya `Function`) ve bir bitiş bildirimi bildirimi (`End Sub` ya da `End Function`) arasında bir yordam alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ffcea-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="ffcea-104">Tüm yordamın kodu bu deyimler arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="ffcea-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="ffcea-105">Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffcea-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="ffcea-106">Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffcea-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="ffcea-107">Değer döndürmeyen bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ffcea-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="ffcea-108">Diğer herhangi bir yordamın dışında, bir `Sub` ifadesini ve ardından bir `End Sub` bildirisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffcea-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="ffcea-109">`Sub` bildiriminde, yordamın adı ile `Sub` anahtar sözcüğünü, sonra da parantez içindeki parametre listesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="ffcea-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="ffcea-110">Yordamın kod deyimlerini `Sub` ve `End Sub` deyimleri arasına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ffcea-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="ffcea-111">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ffcea-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="ffcea-112">Diğer herhangi bir yordamın dışında, bir `Function` ifadesini ve ardından bir `End Function` bildirisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffcea-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="ffcea-113">`Function` bildiriminde, yordamın adı, sonra parantez içindeki parametre listesi ve dönüş değerinin veri türünü belirten bir `As` yan tümcesi ile `Function` anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="ffcea-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="ffcea-114">Yordamın kod deyimlerini `Function` ve `End Function` deyimleri arasına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ffcea-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="ffcea-115">Değeri çağırma koduna döndürmek için bir `Return` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffcea-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="ffcea-116">Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="ffcea-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="ffcea-117">Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ffcea-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="ffcea-118">Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri `Sub` veya `Function` yordamını çağıran tek bir deyim ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ffcea-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="ffcea-119">Yordamınız bir değer döndüren bir `Function` ise, çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden emin olun (örneğin, bir değişkende depolanması) veya aksi takdirde değer kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="ffcea-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="ffcea-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffcea-120">Example</span></span>

 <span data-ttu-id="ffcea-121">Aşağıdaki `Function` yordam, iki tarafa ait değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="ffcea-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ffcea-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcea-122">See also</span></span>

- [<span data-ttu-id="ffcea-123">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ffcea-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="ffcea-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ffcea-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="ffcea-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="ffcea-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="ffcea-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="ffcea-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="ffcea-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="ffcea-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="ffcea-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ffcea-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ffcea-129">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ffcea-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="ffcea-130">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ffcea-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="ffcea-131">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="ffcea-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="ffcea-132">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffcea-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
