---
description: 'Daha fazla bilgi edinin: static (Visual Basic)'
title: Statik
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 03c2e3f64ac9052a0c604b8bc34782af16edbf34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700747"
---
# <a name="static-visual-basic"></a><span data-ttu-id="e4d92-103">Statik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4d92-103">Static (Visual Basic)</span></span>

<span data-ttu-id="e4d92-104">Bir veya daha fazla tanımlanmış yerel değişkenin mevcut olmaya devam etmesi ve bildirildiği yordamın sonlandırmasından sonra en son değerlerini korumasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4d92-104">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d92-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4d92-105">Remarks</span></span>  

 <span data-ttu-id="e4d92-106">Normalde, yordamda bir yerel değişken, yordam durdurulduğunda hemen sona erer.</span><span class="sxs-lookup"><span data-stu-id="e4d92-106">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="e4d92-107">Statik bir değişken var olmaya devam eder ve en son değerini korur.</span><span class="sxs-lookup"><span data-stu-id="e4d92-107">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="e4d92-108">Kodunuzun yordamı çağırması bir sonraki sefer, değişken yeniden başlatılır ve kendisine atadığınız en son değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="e4d92-108">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="e4d92-109">Statik bir değişken, içinde tanımlanan sınıf veya modülün kullanım ömrü için mevcut olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e4d92-109">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e4d92-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e4d92-110">Rules</span></span>  
  
- <span data-ttu-id="e4d92-111">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="e4d92-111">**Declaration Context.**</span></span> <span data-ttu-id="e4d92-112">`Static`Yalnızca yerel değişkenler üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4d92-112">You can use `Static` only on local variables.</span></span> <span data-ttu-id="e4d92-113">Bu, bir değişken için bildirim bağlamının bir yordam `Static` veya bir yordamda bir blok olması veya bir kaynak dosya, ad alanı, sınıf, yapı veya modül olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e4d92-113">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="e4d92-114">`Static`Yapı yordamının içinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e4d92-114">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="e4d92-115">Yerel değişkenlerin veri türleri `Static` çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="e4d92-115">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="e4d92-116">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e4d92-116">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="e4d92-117">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="e4d92-117">**Combined Modifiers.**</span></span> <span data-ttu-id="e4d92-118">`Static` `ReadOnly` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Shadows` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="e4d92-118">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="e4d92-119">Davranış</span><span class="sxs-lookup"><span data-stu-id="e4d92-119">Behavior</span></span>  

 <span data-ttu-id="e4d92-120">Bir yordamda statik bir değişken bildirdiğinizde `Shared` , tüm uygulama için statik değişkenin yalnızca bir kopyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4d92-120">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="e4d92-121">Sınıf `Shared` adını kullanarak bir yordamı çağırın, sınıfın bir örneğine işaret eden bir değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="e4d92-121">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="e4d92-122">Olmayan bir yordamda statik bir değişken bildirdiğinizde `Shared` , sınıfın her örneği için değişkenin yalnızca bir kopyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4d92-122">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="e4d92-123">Sınıfın belirli bir örneğine işaret eden bir değişken kullanarak paylaşılmayan bir yordam çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4d92-123">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d92-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4d92-124">Example</span></span>  

 <span data-ttu-id="e4d92-125">Aşağıdaki örnek öğesinin kullanımını gösterir `Static` .</span><span class="sxs-lookup"><span data-stu-id="e4d92-125">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="e4d92-126">`Static`Değişken `totalSales` yalnızca bir kez 0 olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e4d92-126">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="e4d92-127">Girdiğiniz her seferinde `updateSales` , `totalSales` hala sizin için hesapladığınız en son değere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="e4d92-127">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="e4d92-128">`Static`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e4d92-128">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="e4d92-129">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="e4d92-129">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e4d92-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4d92-130">See also</span></span>

- [<span data-ttu-id="e4d92-131">Shadows</span><span class="sxs-lookup"><span data-stu-id="e4d92-131">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="e4d92-132">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="e4d92-132">Shared</span></span>](shared.md)
- [<span data-ttu-id="e4d92-133">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="e4d92-133">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="e4d92-134">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="e4d92-134">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="e4d92-135">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e4d92-135">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e4d92-136">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4d92-136">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="e4d92-137">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="e4d92-137">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
