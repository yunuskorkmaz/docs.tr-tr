---
title: Genel Yordamlar
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 558601f038fccdcb9b94acb7c796e2b49fb6e6f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059203"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="0d85b-102">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0d85b-102">Generic Procedures in Visual Basic</span></span>

<span data-ttu-id="0d85b-103">*Genel yöntem*olarak da adlandırılan *genel yordam*, en az bir tür parametresiyle tanımlanmış bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="0d85b-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="0d85b-104">Bu, çağıran kodun, yordamı her çağırdığında veri türlerini gereksinimlerine uyarlayabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d85b-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="0d85b-105">Bir yordam, genel bir sınıf veya genel bir yapı içinde tanımlanmakta olan virtuale tarafından genel değildir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="0d85b-106">Genel olması için, yordamın, gerçekleştirebileceğiniz normal parametrelere ek olarak en az bir tür parametresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="0d85b-107">Genel bir sınıf veya yapı genel olmayan yordamlar içerebilir ve genel olmayan bir sınıf, yapı veya modül genel yordamlar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="0d85b-108">Genel yordam, kendi tür parametrelerini normal parametre listesinde, bir tane varsa dönüş türünde ve yordam kodunda kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="0d85b-109">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="0d85b-109">Type Inference</span></span>  

 <span data-ttu-id="0d85b-110">Herhangi bir tür bağımsız değişkeni sağlamadan, genel bir yordamı çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d85b-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="0d85b-111">Bu şekilde çağırırsanız, derleyici yordamın tür bağımsız değişkenlerine geçirilecek uygun veri türlerini saptamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="0d85b-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="0d85b-112">Buna *tür çıkarımı*denir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-112">This is called *type inference*.</span></span> <span data-ttu-id="0d85b-113">Aşağıdaki kod, derleyicinin türü tür parametresine geçmesi gereken bir çağrıyı gösterir `String` `t` .</span><span class="sxs-lookup"><span data-stu-id="0d85b-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 <span data-ttu-id="0d85b-114">Derleyici, tür bağımsız değişkenlerini çağrınızın bağlamından çıkarsanamıyor bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="0d85b-115">Bu tür bir hatanın olası nedeni bir dizi sırası uyumsuzluğu.</span><span class="sxs-lookup"><span data-stu-id="0d85b-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="0d85b-116">Örneğin, bir tür parametresinin dizisi olarak normal bir parametre tanımladığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="0d85b-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="0d85b-117">Farklı bir derece (boyut sayısı) dizisi sağlayan genel yordamı çağırırsanız, uyuşmazlık tür çıkarımını başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0d85b-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="0d85b-118">Aşağıdaki kod, tek boyutlu bir dizi bekleyen bir yordama iki boyutlu bir dizinin geçirildiği bir çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="0d85b-119">Tür çıkarımı yalnızca tüm tür bağımsız değişkenlerini atlayarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d85b-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="0d85b-120">Bir tür bağımsız değişkeni sağlarsanız, bunları sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="0d85b-121">Tür çıkarımı yalnızca genel yordamlar için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0d85b-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="0d85b-122">Genel sınıflarda, yapılarda, arabirimlerde veya Temsilcilerde tür çıkarımı çağıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="0d85b-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d85b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d85b-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0d85b-124">Description</span><span class="sxs-lookup"><span data-stu-id="0d85b-124">Description</span></span>  

 <span data-ttu-id="0d85b-125">Aşağıdaki örnek, `Function` bir dizide belirli bir öğeyi bulmak için genel bir yordam tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0d85b-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="0d85b-126">Bir tür parametresini tanımlar ve parametre listesinde iki parametreyi oluşturmak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d85b-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0d85b-127">Kod</span><span class="sxs-lookup"><span data-stu-id="0d85b-127">Code</span></span>  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a><span data-ttu-id="0d85b-128">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="0d85b-128">Comments</span></span>  

 <span data-ttu-id="0d85b-129">Yukarıdaki örnek, öğesinin `searchValue` her öğesine karşı karşılaştırma yeteneği gerektirir `searchArray` .</span><span class="sxs-lookup"><span data-stu-id="0d85b-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="0d85b-130">Bu özelliği garantilemek için, `T` arabirimi uygulamak üzere tür parametresini kısıtlar <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="0d85b-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="0d85b-131">Kodu, <xref:System.IComparable%601.CompareTo%2A> `=` için sağlanan bir tür bağımsız değişkeninin işleci desteklediği garantisi olmadığından, işleci yerine yöntemini kullanır `T` `=` .</span><span class="sxs-lookup"><span data-stu-id="0d85b-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="0d85b-132">`findElement`Yordamı aşağıdaki kodla test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d85b-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 <span data-ttu-id="0d85b-133">Yukarıdaki `MsgBox` "0", "1" ve "-1" sırasıyla görüntülenecek çağrılar.</span><span class="sxs-lookup"><span data-stu-id="0d85b-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d85b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d85b-134">See also</span></span>

- [<span data-ttu-id="0d85b-135">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="0d85b-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="0d85b-136">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0d85b-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="0d85b-137">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="0d85b-137">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="0d85b-138">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0d85b-138">Procedures</span></span>](../procedures/index.md)
- [<span data-ttu-id="0d85b-139">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0d85b-139">Procedure Parameters and Arguments</span></span>](../procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0d85b-140">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="0d85b-140">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="0d85b-141">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="0d85b-141">Parameter List</span></span>](../../../language-reference/statements/parameter-list.md)
