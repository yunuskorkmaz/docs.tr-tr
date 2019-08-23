---
title: ReadOnly (Visual Basic)
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
ms.openlocfilehash: 01c441576cb4247933c053f2043296733f99fdeb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965416"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="d53dc-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d53dc-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="d53dc-103">Bir değişkenin veya özelliğin okunup yazılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d53dc-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d53dc-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d53dc-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="d53dc-105">Rules</span></span>  
  
- <span data-ttu-id="d53dc-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="d53dc-106">**Declaration Context.**</span></span> <span data-ttu-id="d53dc-107">Yalnızca modül düzeyinde `ReadOnly` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="d53dc-108">Diğer bir deyişle, bir `ReadOnly` öğe için bildirim bağlamı bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="d53dc-109">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="d53dc-109">**Combined Modifiers.**</span></span> <span data-ttu-id="d53dc-110">Aynı bildirimde ile `ReadOnly` `Static` birlikte belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="d53dc-111">**Değer atama.**</span><span class="sxs-lookup"><span data-stu-id="d53dc-111">**Assigning a Value.**</span></span> <span data-ttu-id="d53dc-112">Bir `ReadOnly` özelliği kullanan kod, değerini ayarlayamadı.</span><span class="sxs-lookup"><span data-stu-id="d53dc-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="d53dc-113">Ancak, temel alınan depolamaya erişimi olan kod herhangi bir zamanda değeri atayabilir veya değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="d53dc-114">Bir `ReadOnly` değişkene yalnızca bildiriminde veya tanımlandığı bir sınıf veya yapının oluşturucusunda bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="d53dc-115">Salt okunur değişken ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="d53dc-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="d53dc-116">Sabit bir değer bildirmek ve atamak için [const bildirimini](../../../visual-basic/language-reference/statements/const-statement.md) kullanamadığınız durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="d53dc-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="d53dc-117">Örneğin, `Const` deyimi atamak istediğiniz veri türünü kabul etmeyebilir veya bir sabit ifadeyle derleme zamanında değeri hesaplamayabilir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="d53dc-118">Derleme zamanında değeri bile bilmiyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="d53dc-119">Bu durumlarda, sabit bir değeri tutmak için `ReadOnly` bir değişken kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d53dc-120">Değişkenin veri türü bir dizi veya sınıf örneği gibi bir başvuru türü ise, bu değişkenin kendisi `ReadOnly`olsa bile üyeleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="d53dc-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="d53dc-122">Başlatıldığında, tarafından `characterArray()` işaret edilen dizi "x", "y" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="d53dc-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="d53dc-123">`characterArray` Değişken`ReadOnly`olduğundan, değeri başlatıldıktan sonra değiştiremezsiniz; diğer bir deyişle, buna yeni bir dizi atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d53dc-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="d53dc-124">Ancak, bir veya daha fazla dizi üyesinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="d53dc-125">Yordama `changeArrayElement`yapılan bir çağrıdan sonra, işaret eden `characterArray()` dizi "x", "e" ve "z" barındırır.</span><span class="sxs-lookup"><span data-stu-id="d53dc-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="d53dc-126">Bunun, yordamın, çağıran bağımsız değişkenin kendisini değiştirmesini engelleyen bir yordam [](../../../visual-basic/language-reference/modifiers/byval.md)parametresi olarak bildirilmesinin benzer olduğuna, ancak onun üyelerini değiştirmesine izin verdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d53dc-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d53dc-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d53dc-127">Example</span></span>  
 <span data-ttu-id="d53dc-128">Aşağıdaki örnek, bir çalışanın `ReadOnly` işe alındığı tarih için bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d53dc-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="d53dc-129">Sınıfı, özellik değerini dahili olarak bir `Private` değişken olarak depolar ve yalnızca sınıfın içindeki kod bu değeri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="d53dc-130">Ancak, özelliği olur `Public`ve sınıfa erişebilen tüm kodlar özelliği okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="d53dc-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="d53dc-131">`ReadOnly` Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d53dc-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d53dc-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d53dc-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d53dc-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="d53dc-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d53dc-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d53dc-134">See also</span></span>

- [<span data-ttu-id="d53dc-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="d53dc-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="d53dc-136">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d53dc-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
