---
title: 'Nasıl yapılır: (Visual Basic) nesne Başlatıcı kullanarak nesne bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: e0673c9faceb3bd9fc71123a2ae22abbc7061c04
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970213"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="0ec10-102">Nasıl yapılır: (Visual Basic) nesne Başlatıcı kullanarak nesne bildirme</span><span class="sxs-lookup"><span data-stu-id="0ec10-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="0ec10-103">Nesne başlatıcıları bildirme ve tek bir deyimde bir sınıfın bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ec10-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="0ec10-104">Ayrıca, parametreli bir kurucu çağırmadan aynı anda bir veya daha fazla üye örneğinin başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ec10-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="0ec10-105">Adlandırılmış bir türün bir örneğini oluşturmak için bir nesne Başlatıcısı kullandığınızda, belirttiğiniz sırada belirtilen üyeleri başlatma sonrasında sınıfı için varsayılan oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0ec10-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="0ec10-106">Aşağıdaki yordam bir örneğini oluşturmak nasıl gösterir bir `Student` üç farklı yolla sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ec10-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="0ec10-107">Sınıfı, ad, Soyadı ve diğerlerinin yanı sıra sınıf yıl özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0ec10-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="0ec10-108">Her üç bildirimlerinin yeni bir örneğini oluşturur `Student`, özelliğiyle `First` "Michael için", özellik kümesi `Last` "Tucker için" ve diğer tüm üyeleri varsayılan değerlerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ec10-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="0ec10-109">Yordamdaki her bildirimin sonucu nesne Başlatıcı kullanmaz aşağıdaki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0ec10-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="0ec10-110">Bir uygulama için `Student` sınıfı [nasıl yapılır: Öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="0ec10-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="0ec10-111">Sınıfı oluşturan ve listesini oluşturmak için bu konudan kod kopyalayabilirsiniz `Student` çalışmak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0ec10-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="0ec10-112">Bir nesne Başlatıcı kullanarak adlandırılmış bir sınıfın bir nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0ec10-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="0ec10-113">Bir oluşturucu kullanmayı planladığınız gibi bildirimi başlar.</span><span class="sxs-lookup"><span data-stu-id="0ec10-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="0ec10-114">Anahtar sözcüğü yazın `With`, küme ayraçları içinde bir başlatma listesi tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="0ec10-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="0ec10-115">Başlatma listesinde başlatın ve bir başlangıç değeri için atamak istediğiniz her bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="0ec10-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="0ec10-116">Özelliğin adı öncesinde bir nokta.</span><span class="sxs-lookup"><span data-stu-id="0ec10-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="0ec10-117">Bir veya daha fazla sınıf üyelerini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ec10-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="0ec10-118">Alternatif olarak, yeni bir sınıf örneği bildirebilir ve bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="0ec10-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="0ec10-119">İlk olarak, bir örneğini bildirmeniz `Student`:</span><span class="sxs-lookup"><span data-stu-id="0ec10-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="0ec10-120">Bir örneğinin oluşturulmasını başlatmak `Student` normal şekilde.</span><span class="sxs-lookup"><span data-stu-id="0ec10-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="0ec10-121">Tür `With` ve ardından bir veya daha fazla üyesi yeni örneği başlatmak için nesne Başlatıcı.</span><span class="sxs-lookup"><span data-stu-id="0ec10-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  <span data-ttu-id="0ec10-122">Tanım önceki adımda gt;(yok) basitleştirebilirsiniz `As Student`.</span><span class="sxs-lookup"><span data-stu-id="0ec10-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="0ec10-123">Bunu yaparsanız, derleyici belirleyen `student3` örneğidir `Student` yerel tür çıkarımı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0ec10-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="0ec10-124">Daha fazla bilgi için [yerel tür çıkarımı](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="0ec10-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec10-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ec10-125">See also</span></span>
- [<span data-ttu-id="0ec10-126">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="0ec10-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="0ec10-127">Nasıl yapılır: Öğe listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0ec10-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="0ec10-128">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="0ec10-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="0ec10-129">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="0ec10-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
