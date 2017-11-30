---
title: "Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c818765cbeac7a3080ee666d464052493e5bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="1014b-102">Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1014b-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="1014b-103">Nesne başlatıcıları bildirme ve tek bir deyimde sınıfının bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1014b-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="1014b-104">Ayrıca, parametreli bir oluşturucu çağırmadan aynı anda bir veya daha fazla üye örneğinin başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1014b-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="1014b-105">Adlandırılmış bir türün bir örneği oluşturmak için nesne Başlatıcı kullandığınızda, belirttiğiniz sırayla belirlenen üyelerinin başlatma arkasından sınıfı için varsayılan oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1014b-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="1014b-106">Aşağıdaki yordamda bir örneğini oluşturmak gösterilmiştir bir `Student` üç farklı yolla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1014b-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="1014b-107">Sınıfı, ad, Soyadı ve diğerlerinin yanı sıra sınıfı yıl özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1014b-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="1014b-108">Her üç bildirimlerinin yeni bir örneğini oluşturur `Student`, özelliğiyle `First` "Michael için", özellik kümesi `Last` "Tucker" ve diğer tüm üyeleri varsayılan değerlerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1014b-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="1014b-109">Nesne Başlatıcı kullanmayan bir aşağıdaki örnek yordamı her bildirim sonucunu eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1014b-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 <span data-ttu-id="1014b-110">Bir uygulama için `Student` sınıfı için bkz: [nasıl yapılır: öğelerinin listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="1014b-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="1014b-111">Set sınıfı ve listesini oluşturmak için bu konudan kodu kopyalayabilirsiniz `Student` çalışmak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1014b-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="1014b-112">Nesne Başlatıcı kullanarak adlandırılmış bir sınıfın bir nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1014b-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="1014b-113">Bir oluşturucu kullanmak planlı olarak bildirimi başlar.</span><span class="sxs-lookup"><span data-stu-id="1014b-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="1014b-114">Anahtar sözcüğünü yazmanız `With`, küme ayraçları başlatma listesinde ardından.</span><span class="sxs-lookup"><span data-stu-id="1014b-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="1014b-115">Başlatma listesinde başlatmak ve ilk değer atamak için istediğiniz her bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="1014b-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="1014b-116">Özelliğin adını öncesinde nokta.</span><span class="sxs-lookup"><span data-stu-id="1014b-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     <span data-ttu-id="1014b-117">Bir veya daha fazla üye sınıfının başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1014b-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="1014b-118">Alternatif olarak, sınıfının yeni bir örneğini bildirme ve bir değere atayın.</span><span class="sxs-lookup"><span data-stu-id="1014b-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="1014b-119">Öncelikle, örneği bildirin `Student`:</span><span class="sxs-lookup"><span data-stu-id="1014b-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="1014b-120">Örneği oluşturmayı Başlat `Student` normal şekilde.</span><span class="sxs-lookup"><span data-stu-id="1014b-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="1014b-121">Tür `With` ve ardından yeni örnek bir veya daha fazla üyesi başlatmak için nesne Başlatıcı.</span><span class="sxs-lookup"><span data-stu-id="1014b-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  <span data-ttu-id="1014b-122">Kaldırarak tanımı önceki adımda basitleştirebilir `As Student`.</span><span class="sxs-lookup"><span data-stu-id="1014b-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="1014b-123">Bunu yaparsanız, belirleyen derleyici `student3` örneği `Student` yerel türü çıkarımı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1014b-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     <span data-ttu-id="1014b-124">Daha fazla bilgi için bkz: [yerel türü çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="1014b-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1014b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1014b-125">See Also</span></span>  
 [<span data-ttu-id="1014b-126">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="1014b-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="1014b-127">Nasıl yapılır: öğe listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1014b-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [<span data-ttu-id="1014b-128">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="1014b-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="1014b-129">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="1014b-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
