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
ms.openlocfilehash: 405297a25d4b948a6920bd989c7826e8b6f66bb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398213"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="587b8-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="587b8-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="587b8-103">Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="587b8-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="587b8-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="587b8-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="587b8-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="587b8-105">Rules</span></span>

- <span data-ttu-id="587b8-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="587b8-106">**Declaration Context.**</span></span> <span data-ttu-id="587b8-107">`ReadOnly`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="587b8-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="587b8-108">Diğer bir deyişle, bir öğe için bildirim bağlamı `ReadOnly` bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="587b8-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="587b8-109">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="587b8-109">**Combined Modifiers.**</span></span> <span data-ttu-id="587b8-110">`ReadOnly`Aynı bildirimde ile birlikte belirtemezsiniz `Static` .</span><span class="sxs-lookup"><span data-stu-id="587b8-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="587b8-111">**Değer atama.**</span><span class="sxs-lookup"><span data-stu-id="587b8-111">**Assigning a Value.**</span></span> <span data-ttu-id="587b8-112">Bir özelliği kullanan kod `ReadOnly` , değerini ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="587b8-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="587b8-113">Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="587b8-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="587b8-114">Bir `ReadOnly` değişkene yalnızca bildiriminde veya tanımlandığı bir sınıf veya yapının oluşturucusunda bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="587b8-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="587b8-115">Salt okunur değişken ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="587b8-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="587b8-116">Sabit bir değer bildirmek ve atamak için [const bildirimini](../statements/const-statement.md) kullanamadığınız durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="587b8-116">There are situations in which you cannot use a [Const Statement](../statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="587b8-117">Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir.</span><span class="sxs-lookup"><span data-stu-id="587b8-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="587b8-118">Derleme zamanında değeri bile bilmiyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="587b8-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="587b8-119">Bu durumlarda, `ReadOnly` sabit bir değeri tutmak için bir değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="587b8-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="587b8-120">Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, bu değişkenin kendisi olsa bile üyeleri değiştirilebilir `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="587b8-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="587b8-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="587b8-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="587b8-122">Başlatıldığında, tarafından işaret edilen dizi `characterArray()` "x", "y" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="587b8-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="587b8-123">Değişken olduğundan `characterArray` `ReadOnly` , değeri başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="587b8-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="587b8-124">Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="587b8-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="587b8-125">Yordama yapılan bir çağrıdan `ChangeArrayElement` sonra, işaret eden dizi `characterArray()` "x", "e" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="587b8-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="587b8-126">Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden [emin olun.](byval.md)</span><span class="sxs-lookup"><span data-stu-id="587b8-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="587b8-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="587b8-127">Example</span></span>

<span data-ttu-id="587b8-128">Aşağıdaki örnek, bir `ReadOnly` çalışanın işe alındığı tarih için bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="587b8-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="587b8-129">Sınıfı, özellik değerini dahili olarak bir değişken olarak depolar `Private` ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="587b8-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="587b8-130">Ancak, özelliği olur `Public` ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="587b8-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="587b8-131">`ReadOnly`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="587b8-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="587b8-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="587b8-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="587b8-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="587b8-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="587b8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="587b8-134">See also</span></span>

- [<span data-ttu-id="587b8-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="587b8-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="587b8-136">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="587b8-136">Keywords</span></span>](../keywords/index.md)
