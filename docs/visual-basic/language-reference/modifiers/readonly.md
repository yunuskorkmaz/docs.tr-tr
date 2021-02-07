---
description: 'Daha fazla bilgi edinin: ReadOnly (Visual Basic)'
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
ms.openlocfilehash: f510271531f6e6604f2b542d8331d1a1d7f64d58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700916"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="01d64-103">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d64-103">ReadOnly (Visual Basic)</span></span>

<span data-ttu-id="01d64-104">Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="01d64-104">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="01d64-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01d64-105">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="01d64-106">Kurallar</span><span class="sxs-lookup"><span data-stu-id="01d64-106">Rules</span></span>

- <span data-ttu-id="01d64-107">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="01d64-107">**Declaration Context.**</span></span> <span data-ttu-id="01d64-108">`ReadOnly`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d64-108">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="01d64-109">Diğer bir deyişle, bir öğe için bildirim bağlamı `ReadOnly` bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="01d64-109">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="01d64-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="01d64-110">**Combined Modifiers.**</span></span> <span data-ttu-id="01d64-111">`ReadOnly`Aynı bildirimde ile birlikte belirtemezsiniz `Static` .</span><span class="sxs-lookup"><span data-stu-id="01d64-111">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="01d64-112">**Değer atama.**</span><span class="sxs-lookup"><span data-stu-id="01d64-112">**Assigning a Value.**</span></span> <span data-ttu-id="01d64-113">Bir özelliği kullanan kod `ReadOnly` , değerini ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="01d64-113">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="01d64-114">Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="01d64-114">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="01d64-115">Bir `ReadOnly` değişkene yalnızca bildiriminde veya tanımlandığı bir sınıf veya yapının oluşturucusunda bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d64-115">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="01d64-116">Salt okunur değişken ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="01d64-116">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="01d64-117">Sabit bir değer bildirmek ve atamak için [const bildirimini](../statements/const-statement.md) kullanamadığınız durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="01d64-117">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="01d64-118">Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir.</span><span class="sxs-lookup"><span data-stu-id="01d64-118">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="01d64-119">Derleme zamanında değeri bile bilmiyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d64-119">You might not even know the value at compile time.</span></span> <span data-ttu-id="01d64-120">Bu durumlarda, `ReadOnly` sabit bir değeri tutmak için bir değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d64-120">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01d64-121">Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, bu değişkenin kendisi olsa bile üyeleri değiştirilebilir `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="01d64-121">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="01d64-122">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="01d64-122">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="01d64-123">Başlatıldığında, tarafından işaret edilen dizi `characterArray()` "x", "y" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="01d64-123">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="01d64-124">Değişken olduğundan `characterArray` `ReadOnly` , değeri başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="01d64-124">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="01d64-125">Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01d64-125">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="01d64-126">Yordama yapılan bir çağrıdan `ChangeArrayElement` sonra, işaret eden dizi `characterArray()` "x", "e" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="01d64-126">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="01d64-127">Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden [emin olun.](byval.md)</span><span class="sxs-lookup"><span data-stu-id="01d64-127">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="01d64-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="01d64-128">Example</span></span>

<span data-ttu-id="01d64-129">Aşağıdaki örnek, bir `ReadOnly` çalışanın işe alındığı tarih için bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01d64-129">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="01d64-130">Sınıfı, özellik değerini dahili olarak bir değişken olarak depolar `Private` ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="01d64-130">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="01d64-131">Ancak, özelliği olur `Public` ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="01d64-131">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="01d64-132">`ReadOnly`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="01d64-132">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="01d64-133">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="01d64-133">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="01d64-134">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="01d64-134">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="01d64-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01d64-135">See also</span></span>

- [<span data-ttu-id="01d64-136">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="01d64-136">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="01d64-137">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="01d64-137">Keywords</span></span>](../keywords/index.md)
