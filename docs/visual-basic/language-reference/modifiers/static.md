---
title: Statik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f1031fe005a2fc264b50116b8ea3311dc7065dbc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647638"
---
# <a name="static-visual-basic"></a><span data-ttu-id="f5021-102">Statik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5021-102">Static (Visual Basic)</span></span>
<span data-ttu-id="f5021-103">Bir veya daha fazla bildirilmiş yerel değişkenin içinde bildirildikleri yordam sonlandırmasından sonra en son değerlerini korur ve devam etmek için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5021-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5021-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5021-104">Remarks</span></span>  
 <span data-ttu-id="f5021-105">Normalde, bir yerel değişken bir yordamda yordamı durdurur hemen sonra mevcut olmaktan çıkar.</span><span class="sxs-lookup"><span data-stu-id="f5021-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="f5021-106">Bir statik değişken varolmaya devam eder ve en son değerini korur.</span><span class="sxs-lookup"><span data-stu-id="f5021-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="f5021-107">Kodunuzu yordamı çağıran bir sonraki açışınızda değişkeni yeniden ve hala kendisine atanmış en son değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="f5021-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="f5021-108">Statik bir değişken sınıfın veya modül içinde tanımlanan ömrü varolmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="f5021-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f5021-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="f5021-109">Rules</span></span>  
  
- <span data-ttu-id="f5021-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="f5021-110">**Declaration Context.**</span></span> <span data-ttu-id="f5021-111">Kullanabileceğiniz `Static` yalnızca yerel değişkenlerde.</span><span class="sxs-lookup"><span data-stu-id="f5021-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="f5021-112">Bildirim bağlamı başka bir deyişle bir `Static` değişkeni bir yordam ya da bir yordamda bir blok olmalıdır ve kaynak dosyası, ad alanı, sınıf, yapı veya modül olamaz.</span><span class="sxs-lookup"><span data-stu-id="f5021-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="f5021-113">Kullanamazsınız `Static` yapısı yordam içinde.</span><span class="sxs-lookup"><span data-stu-id="f5021-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="f5021-114">Veri türlerini `Static` yerel değişkenler nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="f5021-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="f5021-115">Daha fazla bilgi için [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="f5021-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="f5021-116">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="f5021-116">**Combined Modifiers.**</span></span> <span data-ttu-id="f5021-117">Belirtemezsiniz `Static` ile birlikte `ReadOnly`, `Shadows`, veya `Shared` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="f5021-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f5021-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="f5021-118">Behavior</span></span>  
 <span data-ttu-id="f5021-119">İçinde statik bir değişken bildirdiğinizde bir `Shared` yordamı, yalnızca bir kopyasını statik değişken tüm uygulama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5021-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="f5021-120">Çağrısı bir `Shared` yordamı kullanarak sınıf adı, sınıfın bir örneğine işaret eden bir değişken değil.</span><span class="sxs-lookup"><span data-stu-id="f5021-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="f5021-121">Olmayan bir yordamda bir statik değişken bildirdiğinizde `Shared`, yalnızca bir kopyasını değişkeni, sınıfın her örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5021-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="f5021-122">Paylaşılmayan bir yordam, sınıfın belirli bir örneğine işaret eden bir değişkeni kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="f5021-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5021-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5021-123">Example</span></span>  
 <span data-ttu-id="f5021-124">Aşağıdaki örnek, kullanımını gösterir `Static`.</span><span class="sxs-lookup"><span data-stu-id="f5021-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f5021-125">`Static` Değişkeni `totalSales` yalnızca bir kez 0 olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f5021-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="f5021-126">Girdiğiniz her zaman `updateSales`, `totalSales` yine de hesaplanan en son değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="f5021-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="f5021-127">`Static` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f5021-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="f5021-128">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f5021-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f5021-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5021-129">See also</span></span>

- [<span data-ttu-id="f5021-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="f5021-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="f5021-131">Shared</span><span class="sxs-lookup"><span data-stu-id="f5021-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="f5021-132">Visual Basic'de ömür</span><span class="sxs-lookup"><span data-stu-id="f5021-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="f5021-133">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f5021-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="f5021-134">Yapılar</span><span class="sxs-lookup"><span data-stu-id="f5021-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f5021-135">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="f5021-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f5021-136">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f5021-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
