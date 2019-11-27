---
title: Kısmi Yöntemler
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352630"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="62b87-102">Kısmi Yöntemler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62b87-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="62b87-103">Kısmi Yöntemler, geliştiricilerin koda özel mantık eklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="62b87-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="62b87-104">Genellikle kod, tasarımcı tarafından üretilen sınıfın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="62b87-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="62b87-105">Kısmi Yöntemler, bir kod üreticisi tarafından oluşturulan kısmi bir sınıfta tanımlanmıştır ve genellikle bir şeyin değiştirildiğini belirten bildirim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62b87-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="62b87-106">Bu, geliştiricinin değişikliğe yanıt olarak özel davranış belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="62b87-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="62b87-107">Kod oluşturucunun Tasarımcısı yalnızca yöntem imzasını ve metoda bir veya daha fazla çağrı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62b87-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="62b87-108">Geliştiriciler daha sonra oluşturulan kodun davranışını özelleştirmek istiyorlarsa yöntemi için uygulamalar sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="62b87-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="62b87-109">Hiçbir uygulama sağlanmazsa, metoda yapılan çağrılar derleyici tarafından kaldırılır ve ek performans yükü yoktur.</span><span class="sxs-lookup"><span data-stu-id="62b87-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="62b87-110">Bildirim</span><span class="sxs-lookup"><span data-stu-id="62b87-110">Declaration</span></span>  
 <span data-ttu-id="62b87-111">Oluşturulan kod, imza satırının başına `Partial` anahtar sözcüğünü yerleştirerek kısmi bir yöntemin tanımını işaretler.</span><span class="sxs-lookup"><span data-stu-id="62b87-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="62b87-112">Tanımın aşağıdaki koşullara uyması gerekir:</span><span class="sxs-lookup"><span data-stu-id="62b87-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="62b87-113">Yöntem bir `Function`değil `Sub`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62b87-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="62b87-114">Metodun gövdesi boş bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62b87-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="62b87-115">Erişim değiştiricisi `Private`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62b87-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="62b87-116">Uygulama</span><span class="sxs-lookup"><span data-stu-id="62b87-116">Implementation</span></span>  
 <span data-ttu-id="62b87-117">Uygulama, birincil olarak kısmi yöntemin gövdesini doldurmayla oluşur.</span><span class="sxs-lookup"><span data-stu-id="62b87-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="62b87-118">Uygulama genellikle tanımdan ayrı bir kısmi sınıfta bulunur ve oluşturulan kodu genişletmek isteyen bir geliştirici tarafından yazılır.</span><span class="sxs-lookup"><span data-stu-id="62b87-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="62b87-119">Önceki örnek, bildirimin imzasını tam olarak yinelemediğinde, ancak Çeşitlemeler olasıdır.</span><span class="sxs-lookup"><span data-stu-id="62b87-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="62b87-120">Özellikle, `Overloads` veya `Overrides`gibi diğer değiştiriciler eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="62b87-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="62b87-121">Yalnızca bir `Overrides` değiştiricisine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="62b87-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="62b87-122">Yöntem değiştiriciler hakkında daha fazla bilgi için bkz. [Sub deyimin](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62b87-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="62b87-123">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="62b87-123">Use</span></span>  
 <span data-ttu-id="62b87-124">Başka bir `Sub` yordamını çağırırınız gibi kısmi bir yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62b87-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="62b87-125">Yöntem uygulanmışsa, bağımsız değişkenler değerlendirilir ve yöntemin gövdesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="62b87-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="62b87-126">Ancak, kısmi bir yöntemi uygulama yönteminin isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62b87-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="62b87-127">Yöntem uygulanmemişse, bir çağrısının bir etkisi olmaz ve yöntemine bağımsız değişken olarak geçirilen ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="62b87-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b87-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b87-128">Example</span></span>  
 <span data-ttu-id="62b87-129">Product. Designer. vb adlı bir dosyada, `Quantity` özelliğine sahip bir `Product` sınıfı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="62b87-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="62b87-130">Product. vb adlı bir dosyada `QuantityChanged`için bir uygulama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="62b87-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="62b87-131">Son olarak, bir projenin ana yönteminde, bir `Product` örneği bildirin ve `Quantity` özelliği için bir başlangıç değeri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="62b87-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="62b87-132">Şu iletiyi görüntüleyen bir ileti kutusu görünür:</span><span class="sxs-lookup"><span data-stu-id="62b87-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="62b87-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62b87-133">See also</span></span>

- [<span data-ttu-id="62b87-134">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b87-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="62b87-135">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="62b87-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="62b87-136">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="62b87-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="62b87-137">Partial</span><span class="sxs-lookup"><span data-stu-id="62b87-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="62b87-138">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62b87-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="62b87-139">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="62b87-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
