---
title: 'Nasıl yapılır: Yordam oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216726"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="136aa-102">Nasıl yapılır: Yordam oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136aa-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="136aa-103">Bir yöntemi başlangıç bildirimi ifadesiyle`Sub` (veya `Function`) ve bir bitiş bildirimi ifadesiyle (`End Sub` veya `End Function`) çevreedersiniz.</span><span class="sxs-lookup"><span data-stu-id="136aa-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="136aa-104">Tüm yordamın kodu bu deyimler arasında yer alır.</span><span class="sxs-lookup"><span data-stu-id="136aa-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="136aa-105">Yordam başka bir yordam içeremez, bu nedenle başlangıç ve bitiş deyimleri başka bir yordamın dışında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="136aa-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="136aa-106">Farklı yerlerde aynı görevi gerçekleştiren bir kodunuz varsa, görevi bir kez yordam olarak yazabilir ve ardından kodunuzda farklı yerlerden çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="136aa-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="136aa-107">Değer döndürmeyen bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="136aa-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="136aa-108">Diğer herhangi bir yordamın dışında, bir `Sub` ifadesini ve ardından `End Sub` bir ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="136aa-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="136aa-109">İfadesinde, yordam adı ile `Sub` anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin. `Sub`</span><span class="sxs-lookup"><span data-stu-id="136aa-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="136aa-110">Yordamın kod deyimlerini `Sub` ve `End Sub` deyimlerini arasına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="136aa-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="136aa-111">Bir değer döndüren bir yordam oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="136aa-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="136aa-112">Diğer herhangi bir yordamın dışında, bir `Function` ifadesini ve ardından `End Function` bir ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="136aa-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="136aa-113">İfadesinde, yordamın adı, sonra `Function` `As` parantez içindeki parametre listesi ve dönüş değerinin veri türünü belirten yan tümce ile anahtar sözcüğünü izleyin. `Function`</span><span class="sxs-lookup"><span data-stu-id="136aa-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="136aa-114">Yordamın kod deyimlerini `Function` ve `End Function` deyimlerini arasına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="136aa-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="136aa-115">Çağırma koduna `Return` değeri döndürmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="136aa-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="136aa-116">Yeni yordamınıza eski ve yinelenen kod bloklarıyla bağlanmak için</span><span class="sxs-lookup"><span data-stu-id="136aa-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="136aa-117">Yeni yordamı, eski kodun ona erişimi olan bir yerde tanımladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="136aa-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="136aa-118">Eski, yinelenen kod bloğunda, yinelenen görevi gerçekleştiren deyimleri `Sub` veya `Function` yordamı çağıran tek bir deyim ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="136aa-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="136aa-119">Yordamınız bir değer döndürürse `Function` bir ise, çağırma deyiminizin döndürülen değeri olan bir eylem gerçekleştirdiğinden, örneğin bir değişkende depolanması, aksi takdirde değerin kaybedildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="136aa-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="136aa-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="136aa-120">Example</span></span>

 <span data-ttu-id="136aa-121">Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar:</span><span class="sxs-lookup"><span data-stu-id="136aa-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="136aa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="136aa-122">See also</span></span>

- [<span data-ttu-id="136aa-123">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="136aa-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="136aa-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="136aa-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="136aa-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="136aa-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="136aa-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="136aa-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="136aa-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="136aa-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="136aa-128">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="136aa-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="136aa-129">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="136aa-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="136aa-130">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="136aa-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="136aa-131">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="136aa-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="136aa-132">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136aa-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
