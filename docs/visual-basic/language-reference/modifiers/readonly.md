---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351273"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="e39f6-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e39f6-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="e39f6-103">Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="e39f6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e39f6-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="e39f6-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e39f6-105">Rules</span></span>

- <span data-ttu-id="e39f6-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="e39f6-106">**Declaration Context.**</span></span> <span data-ttu-id="e39f6-107">Yalnızca modül düzeyinde `ReadOnly` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="e39f6-108">Bu, bir `ReadOnly` öğesi için bildirim bağlamının bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı veya yordam olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="e39f6-109">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="e39f6-109">**Combined Modifiers.**</span></span> <span data-ttu-id="e39f6-110">Aynı bildirimde `Static` birlikte `ReadOnly` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="e39f6-111">**Değer atama.**</span><span class="sxs-lookup"><span data-stu-id="e39f6-111">**Assigning a Value.**</span></span> <span data-ttu-id="e39f6-112">`ReadOnly` bir özelliği kullanan kod, değerini ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="e39f6-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="e39f6-113">Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="e39f6-114">Bir `ReadOnly` değişkenine bir değeri yalnızca bildiriminde veya tanımlandığı bir sınıfın veya yapının oluşturucusunda atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="e39f6-115">Salt okunur değişken ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="e39f6-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="e39f6-116">Sabit bir değer bildirmek ve atamak için [const bildirimini](../../../visual-basic/language-reference/statements/const-statement.md) kullanamadığınız durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="e39f6-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="e39f6-117">Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="e39f6-118">Derleme zamanında değeri bile bilmiyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="e39f6-119">Bu durumlarda, sabit bir değeri tutmak için bir `ReadOnly` değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e39f6-120">Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, değişkenin kendisi `ReadOnly`olsa bile üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="e39f6-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="e39f6-122">Başlatıldığında, `characterArray()` tarafından işaret edilen dizi "x", "y" ve "z" ' i barındırır.</span><span class="sxs-lookup"><span data-stu-id="e39f6-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="e39f6-123">`characterArray` değişken `ReadOnly`olduğundan, değerini başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e39f6-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="e39f6-124">Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="e39f6-125">Yordam `ChangeArrayElement`çağrısı sonrasında, `characterArray()` tarafından işaret edilen dizi "x", "e" ve "z" karakterlerini tutar.</span><span class="sxs-lookup"><span data-stu-id="e39f6-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="e39f6-126">Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden [emin olun.](byval.md)</span><span class="sxs-lookup"><span data-stu-id="e39f6-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="e39f6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e39f6-127">Example</span></span>

<span data-ttu-id="e39f6-128">Aşağıdaki örnek, bir çalışanın işe alındığı tarih için bir `ReadOnly` özelliğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e39f6-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="e39f6-129">Sınıfı, özellik değerini dahili olarak bir `Private` değişkeni olarak depolar ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="e39f6-130">Ancak, özelliği `Public`ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="e39f6-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="e39f6-131">`ReadOnly` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e39f6-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="e39f6-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="e39f6-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="e39f6-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="e39f6-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="e39f6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e39f6-134">See also</span></span>

- [<span data-ttu-id="e39f6-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="e39f6-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="e39f6-136">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e39f6-136">Keywords</span></span>](../keywords/index.md)
