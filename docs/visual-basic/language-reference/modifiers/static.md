---
title: Statik
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 3b323d5fb1c4f1357b9f476213793c69d29b7208
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402700"
---
# <a name="static-visual-basic"></a><span data-ttu-id="dc5e9-102">Statik (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc5e9-102">Static (Visual Basic)</span></span>
<span data-ttu-id="dc5e9-103">Bir veya daha fazla tanımlanmış yerel değişkenin mevcut olmaya devam etmesi ve bildirildiği yordamın sonlandırmasından sonra en son değerlerini korumasının gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc5e9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc5e9-104">Remarks</span></span>  
 <span data-ttu-id="dc5e9-105">Normalde, yordamda bir yerel değişken, yordam durdurulduğunda hemen sona erer.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="dc5e9-106">Statik bir değişken var olmaya devam eder ve en son değerini korur.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="dc5e9-107">Kodunuzun yordamı çağırması bir sonraki sefer, değişken yeniden başlatılır ve kendisine atadığınız en son değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="dc5e9-108">Statik bir değişken, içinde tanımlanan sınıf veya modülün kullanım ömrü için mevcut olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dc5e9-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="dc5e9-109">Rules</span></span>  
  
- <span data-ttu-id="dc5e9-110">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="dc5e9-110">**Declaration Context.**</span></span> <span data-ttu-id="dc5e9-111">`Static`Yalnızca yerel değişkenler üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="dc5e9-112">Bu, bir değişken için bildirim bağlamının bir yordam `Static` veya bir yordamda bir blok olması veya bir kaynak dosya, ad alanı, sınıf, yapı veya modül olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="dc5e9-113">`Static`Yapı yordamının içinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="dc5e9-114">Yerel değişkenlerin veri türleri `Static` çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="dc5e9-115">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="dc5e9-115">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="dc5e9-116">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="dc5e9-116">**Combined Modifiers.**</span></span> <span data-ttu-id="dc5e9-117">`Static` `ReadOnly` Aynı bildirimde, veya ile birlikte belirtemezsiniz `Shadows` `Shared` .</span><span class="sxs-lookup"><span data-stu-id="dc5e9-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="dc5e9-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="dc5e9-118">Behavior</span></span>  
 <span data-ttu-id="dc5e9-119">Bir yordamda statik bir değişken bildirdiğinizde `Shared` , tüm uygulama için statik değişkenin yalnızca bir kopyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="dc5e9-120">Sınıf `Shared` adını kullanarak bir yordamı çağırın, sınıfın bir örneğine işaret eden bir değişken değildir.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="dc5e9-121">Olmayan bir yordamda statik bir değişken bildirdiğinizde `Shared` , sınıfın her örneği için değişkenin yalnızca bir kopyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="dc5e9-122">Sınıfın belirli bir örneğine işaret eden bir değişken kullanarak paylaşılmayan bir yordam çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc5e9-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc5e9-123">Example</span></span>  
 <span data-ttu-id="dc5e9-124">Aşağıdaki örnek öğesinin kullanımını gösterir `Static` .</span><span class="sxs-lookup"><span data-stu-id="dc5e9-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="dc5e9-125">`Static`Değişken `totalSales` yalnızca bir kez 0 olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="dc5e9-126">Girdiğiniz her seferinde `updateSales` , `totalSales` hala sizin için hesapladığınız en son değere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="dc5e9-127">`Static`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="dc5e9-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="dc5e9-128">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc5e9-128">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="dc5e9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5e9-129">See also</span></span>

- [<span data-ttu-id="dc5e9-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="dc5e9-130">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="dc5e9-131">Shared</span><span class="sxs-lookup"><span data-stu-id="dc5e9-131">Shared</span></span>](shared.md)
- [<span data-ttu-id="dc5e9-132">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="dc5e9-132">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="dc5e9-133">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="dc5e9-133">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="dc5e9-134">Yapılar</span><span class="sxs-lookup"><span data-stu-id="dc5e9-134">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="dc5e9-135">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc5e9-135">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="dc5e9-136">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="dc5e9-136">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
