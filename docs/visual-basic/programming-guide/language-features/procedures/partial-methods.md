---
title: "Kısmi Yöntemler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ebedd6f8173e3c349240d24ddaf16e4841f67a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="4568d-102">Kısmi Yöntemler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4568d-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="4568d-103">Kısmi yöntemler koda Özel mantık ekleme geliştiricilerin.</span><span class="sxs-lookup"><span data-stu-id="4568d-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="4568d-104">Genellikle, bir tasarımcı tarafından oluşturulan sınıfın parçası kodudur.</span><span class="sxs-lookup"><span data-stu-id="4568d-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="4568d-105">Kısmi yöntemler Kod Oluşturucu tarafından oluşturulan bir parçalı sınıf tanımlanır ve bunlar genellikle bir şey değiştirildiğini bildirim sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4568d-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="4568d-106">Bunlar değişikliğe yanıt özel davranış belirlemek Geliştirici etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4568d-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="4568d-107">Kod oluşturucunun Tasarımcı yalnızca yöntem imzası ve yöntemine yönelik bir veya daha fazla çağrılar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4568d-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="4568d-108">Oluşturulan kod davranışını özelleştirmek istiyorsanız geliştiriciler sonra uygulamaları yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4568d-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="4568d-109">Hiçbir uygulama sağlandığında yöntemine yönelik çağrılar hiçbir ek performans ek yükünün kaynaklanan derleyici tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="4568d-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="4568d-110">Bildirim</span><span class="sxs-lookup"><span data-stu-id="4568d-110">Declaration</span></span>  
 <span data-ttu-id="4568d-111">Oluşturulan kodun anahtar sözcüğünü girerek kısmi bir yöntemin tanımı işaretler `Partial` imza satırın başındaki.</span><span class="sxs-lookup"><span data-stu-id="4568d-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="4568d-112">Tanımı aşağıdaki koşulları karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="4568d-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="4568d-113">Yöntem olmalıdır bir `Sub`değil bir `Function`.</span><span class="sxs-lookup"><span data-stu-id="4568d-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="4568d-114">Yönteminin gövdesi boş bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4568d-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="4568d-115">Erişim değiştiricisi olmalıdır `Private`.</span><span class="sxs-lookup"><span data-stu-id="4568d-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="4568d-116">Uygulama</span><span class="sxs-lookup"><span data-stu-id="4568d-116">Implementation</span></span>  
 <span data-ttu-id="4568d-117">Uygulama, öncelikle kısmi yöntemin gövdesine doldurma oluşur.</span><span class="sxs-lookup"><span data-stu-id="4568d-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="4568d-118">Uygulama tanımından ayrı bir parçalı sınıf genellikle bulunduğu ve oluşturulan kod genişletmek isteyen bir geliştirici tarafından yazılan.</span><span class="sxs-lookup"><span data-stu-id="4568d-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="4568d-119">Önceki örneği bildiriminde imza tam olarak çoğaltır, ancak Çeşitlemeler mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4568d-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="4568d-120">Özellikle, diğer değiştiricileri gibi eklenebilir `Overloads` veya `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="4568d-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="4568d-121">Yalnızca bir `Overrides` değiştiricisi izin verilir.</span><span class="sxs-lookup"><span data-stu-id="4568d-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="4568d-122">Yöntemi değiştirici hakkında daha fazla bilgi için bkz: [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4568d-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="4568d-123">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="4568d-123">Use</span></span>  
 <span data-ttu-id="4568d-124">Diğer çağırırdı gibi kısmi bir yöntem çağrısı `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="4568d-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="4568d-125">Yöntem uygulanmadı, bağımsız olarak değerlendirilir ve yönteminin gövdesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4568d-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="4568d-126">Ancak, kısmi yöntemi uygulama isteğe bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4568d-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="4568d-127">Yöntem uygulanmadı, bir çağrısına hiçbir etkisi olmaz ve yöntemi için bağımsız değişken olarak geçirilen ifade değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="4568d-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4568d-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="4568d-128">Example</span></span>  
 <span data-ttu-id="4568d-129">Product.Designer.vb adındaki bir dosyada tanımlayan bir `Product` olan sınıfı bir `Quantity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4568d-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="4568d-130">Product.vb adındaki bir dosyada için bir uygulama sunmak `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="4568d-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="4568d-131">Son olarak, bir proje ana yönteminde bildirme bir `Product` örneği ve sağlamak için bir başlangıç değeri kendi `Quantity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4568d-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="4568d-132">Bir ileti kutusu bu iletiyi görüntüleyen görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="4568d-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="4568d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4568d-133">See Also</span></span>  
 [<span data-ttu-id="4568d-134">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="4568d-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="4568d-135">Alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="4568d-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="4568d-136">İsteğe bağlı parametreler</span><span class="sxs-lookup"><span data-stu-id="4568d-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="4568d-137">Kısmi</span><span class="sxs-lookup"><span data-stu-id="4568d-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="4568d-138">LINQ-SQL kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="4568d-138">Code Generation in LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb399400)  
 [<span data-ttu-id="4568d-139">Kısmi yöntemler kullanarak iş mantığı ekleme</span><span class="sxs-lookup"><span data-stu-id="4568d-139">Adding Business Logic By Using Partial Methods</span></span>](https://msdn.microsoft.com/library/bb546176)
