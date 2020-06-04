---
title: 'Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404881"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="276ba-102">Nasıl yapılır: Nesne Başlatıcı Kullanarak Bir Nesne Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="276ba-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="276ba-103">Nesne başlatıcıları, tek bir ifadede bir sınıfın örneğini bildirmenize ve örneklendirimenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="276ba-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="276ba-104">Ayrıca, parametreli bir Oluşturucu çağırmadan, örneğin bir veya daha fazla üyesini aynı zamanda başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="276ba-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="276ba-105">Adlandırılmış bir türün örneğini oluşturmak için bir nesne Başlatıcısı kullandığınızda, sınıfının parametresiz oluşturucusu çağrılır, ardından belirttiğiniz sırada belirtilen üyelerin başlatılması gelir.</span><span class="sxs-lookup"><span data-stu-id="276ba-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="276ba-106">Aşağıdaki yordamda üç farklı şekilde bir sınıf örneğinin nasıl oluşturulacağı gösterilmektedir `Student` .</span><span class="sxs-lookup"><span data-stu-id="276ba-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="276ba-107">Sınıfın adı, soyadı ve sınıf yılı özellikleri diğerleri arasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="276ba-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="276ba-108">Üç bildirime her biri `Student` , özelliği `First` "Michael", özelliği `Last` "Tucker" olarak ayarlanmış ve diğer tüm Üyeler varsayılan değerlerine ayarlanmış olan yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="276ba-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="276ba-109">Yordamdaki her bir bildirimin sonucu, nesne Başlatıcısı kullanmayan aşağıdaki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="276ba-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="276ba-110">Sınıfının uygulanması için `Student` bkz. [nasıl yapılır: öğe listesi oluşturma](../../concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="276ba-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="276ba-111">Sınıfı ayarlamak ve birlikte çalışmak üzere bir nesne listesi oluşturmak için bu konudaki kodu kopyalayabilirsiniz `Student` .</span><span class="sxs-lookup"><span data-stu-id="276ba-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="276ba-112">Bir nesne Başlatıcısı kullanarak adlandırılmış bir sınıfın nesnesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="276ba-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="276ba-113">Oluşturucuyu kullanmayı planladıysanız bildirimi başlatın.</span><span class="sxs-lookup"><span data-stu-id="276ba-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="276ba-114">Anahtar sözcüğünü ve `With` ardından Küme ayraçları içinde bir başlatma listesini yazın.</span><span class="sxs-lookup"><span data-stu-id="276ba-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="276ba-115">Başlatma listesinde, başlatmak istediğiniz her bir özelliği ekleyin ve buna bir başlangıç değeri atayın.</span><span class="sxs-lookup"><span data-stu-id="276ba-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="276ba-116">Özelliğin adı önünde bir nokta gelir.</span><span class="sxs-lookup"><span data-stu-id="276ba-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="276ba-117">Sınıfının bir veya daha fazla üyesini başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="276ba-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="276ba-118">Alternatif olarak, sınıfının yeni bir örneğini bildirebilir ve sonra bir değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="276ba-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="276ba-119">İlk olarak, bir örneği bildirin `Student` :</span><span class="sxs-lookup"><span data-stu-id="276ba-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="276ba-120">Bir örneğinin oluşturulmasını `Student` normal şekilde başlatın.</span><span class="sxs-lookup"><span data-stu-id="276ba-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="276ba-121">`With`Yeni örneğin bir veya daha fazla üyesini başlatmak için bir nesne Başlatıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="276ba-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="276ba-122">Önceki adımda, öğesini atlayarak tanımlamayı kolaylaştırabilirsiniz `As Student` .</span><span class="sxs-lookup"><span data-stu-id="276ba-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="276ba-123">Bunu yaparsanız, derleyici `student3` `Student` Yerel tür çıkarımı kullanarak bir örneği olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="276ba-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="276ba-124">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="276ba-124">For more information, see [Local Type Inference](../variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276ba-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="276ba-125">See also</span></span>

- [<span data-ttu-id="276ba-126">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="276ba-126">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="276ba-127">Nasıl yapılır: Öğe Listesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="276ba-127">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="276ba-128">Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="276ba-128">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="276ba-129">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="276ba-129">Anonymous Types</span></span>](anonymous-types.md)
