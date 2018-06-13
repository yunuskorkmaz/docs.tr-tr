---
title: Statik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602060"
---
# <a name="static-visual-basic"></a><span data-ttu-id="86374-102">Statik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86374-102">Static (Visual Basic)</span></span>
<span data-ttu-id="86374-103">Bir veya daha fazla bildirilen yerel değişkenler var ve bunlar bildirilir yordamı sonlandırma sonra en son değerleri korumak devam etmek için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86374-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86374-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86374-104">Remarks</span></span>  
 <span data-ttu-id="86374-105">Normalde, bir yordam yerel bir değişkende yordamı durdurur hemen yok olur.</span><span class="sxs-lookup"><span data-stu-id="86374-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="86374-106">Statik bir değişken var olmaya devam eder ve en son değerini korur.</span><span class="sxs-lookup"><span data-stu-id="86374-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="86374-107">Yordamı, kodunuzu çağırması sonraki saat değişkeni değil yeniden ve hala kendisine atanmış en son değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="86374-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="86374-108">Statik bir değişken içinde tanımlanan sınıfı veya modülü ömrü için var olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="86374-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="86374-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="86374-109">Rules</span></span>  
  
-   <span data-ttu-id="86374-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="86374-110">**Declaration Context.**</span></span> <span data-ttu-id="86374-111">Kullanabileceğiniz `Static` yalnızca yerel değişkenler üzerinde.</span><span class="sxs-lookup"><span data-stu-id="86374-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="86374-112">Bu bildirimi bağlamının anlamına gelir bir `Static` değişkeni bir yordam veya bir yordam bloğunda olmalıdır ve kaynak dosyası, ad alanı, sınıf, yapı veya modülü olamaz.</span><span class="sxs-lookup"><span data-stu-id="86374-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="86374-113">Kullanamazsınız `Static` yapısı yordam içindeki.</span><span class="sxs-lookup"><span data-stu-id="86374-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="86374-114">Veri türlerini `Static` yerel değişkenler olamaz sonuçlandı.</span><span class="sxs-lookup"><span data-stu-id="86374-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="86374-115">Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="86374-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="86374-116">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="86374-116">**Combined Modifiers.**</span></span> <span data-ttu-id="86374-117">Belirtemeyeceğiniz `Static` ile birlikte `ReadOnly`, `Shadows`, veya `Shared` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="86374-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="86374-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="86374-118">Behavior</span></span>  
 <span data-ttu-id="86374-119">Statik bir değişkende bildirme ne zaman bir `Shared` yordamı, statik değişken yalnızca bir kopyası olan tüm uygulama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86374-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="86374-120">Çağırmanız bir `Shared` sınıfı kullanarak yordamı adı, sınıfının bir örneğini gösteren bir değişken değil.</span><span class="sxs-lookup"><span data-stu-id="86374-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="86374-121">Bildirme zaman değil bir yordam statik bir değişkende `Shared`, yalnızca bir kopya değişkenin sınıfın her örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86374-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="86374-122">Sınıfın belirli bir örneğine işaret eden bir değişkeni kullanarak bir paylaşılmayan yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="86374-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86374-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="86374-123">Example</span></span>  
 <span data-ttu-id="86374-124">Aşağıdaki örnek kullanımını gösteren `Static`.</span><span class="sxs-lookup"><span data-stu-id="86374-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="86374-125">`Static` Değişken `totalSales` 0 olarak yalnızca bir kez başlatılır.</span><span class="sxs-lookup"><span data-stu-id="86374-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="86374-126">Girdiğiniz her zaman `updateSales`, `totalSales` hala için hesaplanan en son değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="86374-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="86374-127">`Static` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="86374-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="86374-128">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="86374-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="86374-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86374-129">See Also</span></span>  
 [<span data-ttu-id="86374-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="86374-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="86374-131">Shared</span><span class="sxs-lookup"><span data-stu-id="86374-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="86374-132">Visual Basic'de ömür</span><span class="sxs-lookup"><span data-stu-id="86374-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="86374-133">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="86374-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="86374-134">Yapılar</span><span class="sxs-lookup"><span data-stu-id="86374-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="86374-135">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="86374-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="86374-136">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="86374-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
