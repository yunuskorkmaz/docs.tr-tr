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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825397"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="9383d-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9383d-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="9383d-103">Bir değişken veya özellik okunabildiğini ancak yazılmazsa olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9383d-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9383d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9383d-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9383d-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="9383d-105">Rules</span></span>  
  
-   <span data-ttu-id="9383d-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="9383d-106">**Declaration Context.**</span></span> <span data-ttu-id="9383d-107">Kullanabileceğiniz `ReadOnly` yalnızca Modül düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="9383d-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="9383d-108">Bildirim bağlamı başka bir deyişle bir `ReadOnly` öğesi bir sınıf, yapı veya modül olmalıdır ve bir kaynak dosyası, ad alanı ya da yordamın olamaz.</span><span class="sxs-lookup"><span data-stu-id="9383d-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="9383d-109">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="9383d-109">**Combined Modifiers.**</span></span> <span data-ttu-id="9383d-110">Belirtemezsiniz `ReadOnly` ile birlikte `Static` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="9383d-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="9383d-111">**Bir değer atama.**</span><span class="sxs-lookup"><span data-stu-id="9383d-111">**Assigning a Value.**</span></span> <span data-ttu-id="9383d-112">Kod kullanan bir `ReadOnly` özellik değeri ayarlayamaz.</span><span class="sxs-lookup"><span data-stu-id="9383d-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="9383d-113">Ancak, temel alınan depolama erişimi olan kod atama veya herhangi bir zamanda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9383d-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="9383d-114">Bir değer atamak için bir `ReadOnly` yalnızca bildiriminden veya bir sınıf veya yapı içinde tanımlanmış olduğu oluşturucusunun değişken.</span><span class="sxs-lookup"><span data-stu-id="9383d-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="9383d-115">Salt okunur değişken kullanma zamanı</span><span class="sxs-lookup"><span data-stu-id="9383d-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="9383d-116">Bazı durumlarda, kullanamazsınız bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md) bildirmek ve sabit bir değer atamak için.</span><span class="sxs-lookup"><span data-stu-id="9383d-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="9383d-117">Örneğin, `Const` deyimi atamak istediğiniz veri türü kabul ya da sabit bir ifade ile derleme zamanında değeri hesaplamak mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9383d-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="9383d-118">Hatta derleme zamanında değeri etmeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9383d-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="9383d-119">Bu durumlarda, kullandığınız bir `ReadOnly` sabit değerini tutacak bir değişken.</span><span class="sxs-lookup"><span data-stu-id="9383d-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9383d-120">Değişkenin veri türü bir dizi veya bir sınıf örneği gibi bir başvuru türü ise değişken olsa bile üyelerini değiştirilebilir `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="9383d-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="9383d-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9383d-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="9383d-122">Hazırlarken, dizi tarafından işaret edilen `characterArray()` ayrı tutma "x", "y" ve "z".</span><span class="sxs-lookup"><span data-stu-id="9383d-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="9383d-123">Çünkü değişken `characterArray` olduğu `ReadOnly`; olan başlatıldıktan sonra değerini değiştiremezsiniz, yeni bir dizi atanamaz.</span><span class="sxs-lookup"><span data-stu-id="9383d-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="9383d-124">Ancak, bir veya daha fazla dizi üyeleri değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9383d-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="9383d-125">Bir yordam çağrısından `changeArrayElement`, dizi tarafından işaret edilen `characterArray()` ayrı tutma "x", "M" ve "z".</span><span class="sxs-lookup"><span data-stu-id="9383d-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="9383d-126">Bir yordam parametre bildirmek için benzer olduğuna dikkat edin [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), hangi yordamı çağırma bağımsız değiştirmesini engeller ancak üyelerini değiştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9383d-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9383d-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="9383d-127">Example</span></span>  
 <span data-ttu-id="9383d-128">Aşağıdaki örnekte tanımlayan bir `ReadOnly` özelliği üzerinde bir çalışan işe tarih.</span><span class="sxs-lookup"><span data-stu-id="9383d-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="9383d-129">Bu özellik değerini dahili olarak sınıf deposu bir `Private` sınıf içinde değişken ve yalnızca kod, bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9383d-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="9383d-130">Ancak, özelliğidir `Public`, ve sınıfı erişebilen herhangi bir kod özelliği okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9383d-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9383d-131">`ReadOnly` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9383d-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9383d-132">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9383d-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9383d-133">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9383d-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9383d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9383d-134">See also</span></span>

- [<span data-ttu-id="9383d-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="9383d-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="9383d-136">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9383d-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
