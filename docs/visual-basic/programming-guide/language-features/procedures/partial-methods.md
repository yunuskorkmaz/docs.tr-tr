---
title: Kısmi Yöntemler (Visual Basic)
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
ms.openlocfilehash: 50d7f24fd9f854d36bb2ed48c2e41a996c29dfe8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638877"
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="a9971-102">Kısmi Yöntemler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9971-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="a9971-103">Kısmi yöntemler, koda Özel mantık eklemek geliştiricilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9971-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="a9971-104">Genellikle, kod tasarımcı tarafından oluşturulan bir sınıf parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a9971-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="a9971-105">Kısmi yöntemler bir kod Oluşturucu tarafından oluşturulan bir kısmi sınıf tanımlanır ve bunlar genellikle bir şey değiştirildiğini bildirim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9971-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="a9971-106">Bunlar Geliştirici değişikliğe yanıt özel davranışını belirtmek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a9971-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="a9971-107">Kod oluşturucunun Tasarımcı yalnızca yöntem imzası ve bir veya daha fazla yöntem çağrısına tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9971-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="a9971-108">Oluşturulan kodun davranışını özelleştirmek istiyorsanız geliştiriciler ardından uygulamaları yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9971-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="a9971-109">Hiçbir uygulama sağlandığında yöntemine yönelik çağrılar hiçbir ek performans yükünden kaynaklanan derleyici tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="a9971-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="a9971-110">Bildirim</span><span class="sxs-lookup"><span data-stu-id="a9971-110">Declaration</span></span>  
 <span data-ttu-id="a9971-111">Oluşturulan kodun anahtar sözcüğünü koyarak kısmi bir yöntemin tanımını işaretler `Partial` imza satırın başlangıcında.</span><span class="sxs-lookup"><span data-stu-id="a9971-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="a9971-112">Tanımı aşağıdaki koşulları karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="a9971-112">The definition must meet the following conditions:</span></span>  
  
- <span data-ttu-id="a9971-113">Yöntem olmalıdır bir `Sub`değil bir `Function`.</span><span class="sxs-lookup"><span data-stu-id="a9971-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
- <span data-ttu-id="a9971-114">Yöntemin gövdesi boş bırakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9971-114">The body of the method must be left empty.</span></span>  
  
- <span data-ttu-id="a9971-115">Erişim değiştiricisi olmalıdır `Private`.</span><span class="sxs-lookup"><span data-stu-id="a9971-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a9971-116">Uygulama</span><span class="sxs-lookup"><span data-stu-id="a9971-116">Implementation</span></span>  
 <span data-ttu-id="a9971-117">Uygulama, kısmi yöntem gövdesinde doldurma öncelikli olarak oluşur.</span><span class="sxs-lookup"><span data-stu-id="a9971-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="a9971-118">Uygulama, genellikle ayrı bir kısmi sınıf tanımından olduğundan ve oluşturulan kodun genişletmek isteyen bir geliştirici tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="a9971-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="a9971-119">Önceki örneği bildiriminde imzası tam olarak çoğaltır, ancak çeşitlemeleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a9971-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="a9971-120">Özellikle, diğer değiştiriciler, gibi eklenebilir `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a9971-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="a9971-121">Yalnızca bir `Overrides` değiştiricisi izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a9971-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="a9971-122">Yöntemi değiştirici hakkında daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a9971-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="a9971-123">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="a9971-123">Use</span></span>  
 <span data-ttu-id="a9971-124">Diğer çağıracak şekilde kısmi bir yöntemin çağrı `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="a9971-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="a9971-125">Yöntem uygulanmadı, bağımsız değişkenleri değerlendirilir ve yöntemin gövdesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a9971-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="a9971-126">Ancak, kısmi bir yöntemin uygulama isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a9971-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="a9971-127">Yöntem uygulanmadı, bir çağrı etkiye sahip değildir ve yönteme bağımsız değişken olarak geçirilen ifade değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="a9971-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9971-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9971-128">Example</span></span>  
 <span data-ttu-id="a9971-129">Product.Designer.vb adlı bir dosyada tanımlayan bir `Product` sahip sınıf bir `Quantity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a9971-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 <span data-ttu-id="a9971-130">Product.vb adlı bir dosyada sağlamak için bir uygulama `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="a9971-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a9971-131">Son olarak, bir projenin ana yöntemi bildirmek bir `Product` örneği ve sağlamak için bir başlangıç değeri kendi `Quantity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a9971-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 <span data-ttu-id="a9971-132">Bir ileti kutusunda Bu ileti görüntüleyen görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="a9971-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="a9971-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9971-133">See also</span></span>

- [<span data-ttu-id="a9971-134">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a9971-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a9971-135">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a9971-135">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a9971-136">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9971-136">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="a9971-137">Partial</span><span class="sxs-lookup"><span data-stu-id="a9971-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="a9971-138">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9971-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="a9971-139">Kısmi Yöntemler Kullanarak İş Mantığı Ekleme</span><span class="sxs-lookup"><span data-stu-id="a9971-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
