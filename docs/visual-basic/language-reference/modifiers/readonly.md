---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="c8857-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8857-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="c8857-103">Bir değişkenin veya özelliğin okuma ancak yazılmadı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8857-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8857-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8857-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c8857-105">Kurallar</span><span class="sxs-lookup"><span data-stu-id="c8857-105">Rules</span></span>  
  
-   <span data-ttu-id="c8857-106">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="c8857-106">**Declaration Context.**</span></span> <span data-ttu-id="c8857-107">Kullanabileceğiniz `ReadOnly` yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="c8857-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="c8857-108">Bu bildirimi bağlamının anlamına gelir bir `ReadOnly` öğesi bir sınıf, yapı veya modülü olması ve kaynak dosyasını, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="c8857-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="c8857-109">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="c8857-109">**Combined Modifiers.**</span></span> <span data-ttu-id="c8857-110">Belirtemeyeceğiniz `ReadOnly` ile birlikte `Static` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="c8857-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="c8857-111">**Bir değer atama.**</span><span class="sxs-lookup"><span data-stu-id="c8857-111">**Assigning a Value.**</span></span> <span data-ttu-id="c8857-112">Kod kullanan bir `ReadOnly` özellik değeri ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c8857-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="c8857-113">Ancak temel alınan depolama erişimi kod atayabilir veya herhangi bir zamanda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c8857-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="c8857-114">Bir değere atayabileceğiniz bir `ReadOnly` yalnızca bildiriminden veya bir sınıf veya yapı tanımlanmış oluşturucusunun değişken.</span><span class="sxs-lookup"><span data-stu-id="c8857-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="c8857-115">Bir salt okunur değişken kullanmak ne zaman</span><span class="sxs-lookup"><span data-stu-id="c8857-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="c8857-116">İçinde kullanamazsınız durumlar vardır bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md) bildirme ve sabit bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8857-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="c8857-117">Örneğin, `Const` deyimi atamak istediğiniz veri türü kabul veya sabit bir ifade ile derleme zamanında değeri işlem mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c8857-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="c8857-118">Hatta derleme zamanında değeri anlamayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8857-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="c8857-119">Bu durumlarda, kullanabileceğiniz bir `ReadOnly` değişkeni sabit bir değer tutun.</span><span class="sxs-lookup"><span data-stu-id="c8857-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8857-120">Değişken olsa bile değişkenin veri türü bir dizi ya da bir sınıf örneği gibi bir başvuru türü ise üyeleri değiştirilebilir `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="c8857-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="c8857-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c8857-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="c8857-122">Hazırlarken, dizi işaret için tarafından `characterArray()` ayrı tutma "x", "y" ve "z".</span><span class="sxs-lookup"><span data-stu-id="c8857-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="c8857-123">Çünkü değişkeni `characterArray` olan `ReadOnly`; olan başlatıldıktan sonra değeri değiştirilemiyor, yeni bir dizi atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c8857-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="c8857-124">Ancak, bir veya daha fazla dizi üyeleri değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8857-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="c8857-125">Aşağıdaki yordam çağrısına `changeArrayElement`, tarafından diziyi işaret için `characterArray()` ayrı tutma "x", "M" ve "z".</span><span class="sxs-lookup"><span data-stu-id="c8857-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="c8857-126">Bunun bir yordam parametresini olacak şekilde bildirmek için benzer olduğunu unutmayın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), yordamı çağıran bağımsız değişkenin kendisine değiştirmelerini ancak üyelerini değiştirmek izin verir.</span><span class="sxs-lookup"><span data-stu-id="c8857-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8857-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8857-127">Example</span></span>  
 <span data-ttu-id="c8857-128">Aşağıdaki örnek tanımlayan bir `ReadOnly` özelliği bir çalışan üzerinde işe tarihi için.</span><span class="sxs-lookup"><span data-stu-id="c8857-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="c8857-129">Bu özellik değerini dahili olarak sınıf deposu bir `Private` sınıfı içinde değişken ve yalnızca kod, bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8857-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="c8857-130">Ancak, özelliktir `Public`, ve sınıf erişebilmeniz için herhangi bir kod özelliği okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8857-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="c8857-131">`ReadOnly` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c8857-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c8857-132">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="c8857-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c8857-133">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="c8857-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8857-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8857-134">See Also</span></span>  
 [<span data-ttu-id="c8857-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c8857-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="c8857-136">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c8857-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
