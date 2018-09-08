---
title: Visual Basic'de Genel Yordamlar
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
ms.openlocfilehash: 9a88a979a6b46f897e5f04f4481d4a23e245b165
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195026"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="3754a-102">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3754a-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="3754a-103">A *genel yordam*ayrıca adlı bir *genel yöntem*, en az bir tür parametreyle tanımlanan bir yordam olduğunu.</span><span class="sxs-lookup"><span data-stu-id="3754a-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="3754a-104">Bu, çağıran kodu yordam çağrıları her zaman veri türleri, gereksinimleri ile uyumlu hale getirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3754a-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="3754a-105">Bir yordam, yalnızca genel bir sınıf veya yapının genel bir yapı içinde tanımlanan da genel değil.</span><span class="sxs-lookup"><span data-stu-id="3754a-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="3754a-106">Yordamı, genel olması için ek normal işlem sürebilir herhangi bir parametre olarak en az bir tür parametresi atmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3754a-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="3754a-107">Bir genel sınıf veya yapı jenerik olmayan yordamları ve jenerik olmayan bir sınıf, yapı, içerebilir veya modülü genel yordamlar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3754a-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="3754a-108">Genel bir yordam, normal parametre listesinde bir ve onun yordamdaki kodu varsa, dönüş türü, tür parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3754a-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="3754a-109">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="3754a-109">Type Inference</span></span>  
 <span data-ttu-id="3754a-110">Herhangi bir tür bağımsız değişkeni sağlamadan genel bir yordam çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3754a-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="3754a-111">Bu şekilde çağırırsanız derleyici yordamın türü bağımsız değişkenler için uygun veri türlerini belirlemek çalışır.</span><span class="sxs-lookup"><span data-stu-id="3754a-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="3754a-112">Bu adlandırılır *anlam çıkarma*.</span><span class="sxs-lookup"><span data-stu-id="3754a-112">This is called *type inference*.</span></span> <span data-ttu-id="3754a-113">Aşağıdaki kod bir çağrı gösterir, derleyicinin tür geçmelidir algılar `String` tür parametresi için `t`.</span><span class="sxs-lookup"><span data-stu-id="3754a-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="3754a-114">Derleyici, tür bağımsız değişkenlerini çağrınızın bağlamından çıkarsanamaz. bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="3754a-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="3754a-115">Bu tür bir hataya olası nedenlerinden biri, bir dizi derece uyuşmazlığı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3754a-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="3754a-116">Örneğin, bir tür parametresi bir dizi olarak normal parametresini tanımlama varsayalım.</span><span class="sxs-lookup"><span data-stu-id="3754a-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="3754a-117">Genel bir yordamı çağırma sağlayan bir dizi farklı boyut sayısına (sayı) boyut uyuşmazlığı tür çıkarımı başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3754a-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="3754a-118">Aşağıdaki kod bir çağrı gösterir, tek boyutlu dizi bekliyor bir yordam için iki boyutlu bir dizi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3754a-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="3754a-119">Tür çıkarımı, yalnızca tüm tür bağımsız değişkenlerini gt;(yok) çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3754a-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="3754a-120">Bir tür bağımsız değişkeni sağlarsanız, tüm bunları sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3754a-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="3754a-121">Tür çıkarımı, yalnızca genel yordamlar için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3754a-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="3754a-122">Genel sınıflar, yapılar, arabirimler veya temsilciler tür çıkarımı çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="3754a-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3754a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="3754a-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3754a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3754a-124">Description</span></span>  
 <span data-ttu-id="3754a-125">Aşağıdaki örnek, genel tanımlar `Function` yordamı belirli bir öğenin bir dizide bulunacak.</span><span class="sxs-lookup"><span data-stu-id="3754a-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="3754a-126">Bu, bir tür parametresi tanımlar ve parametre listesinde iki parametre oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3754a-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3754a-127">Kod</span><span class="sxs-lookup"><span data-stu-id="3754a-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="3754a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3754a-128">Comments</span></span>  
 <span data-ttu-id="3754a-129">Yukarıdaki örnekte karşılaştırma gerektirir `searchValue` her öğeye karşı `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="3754a-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="3754a-130">Bu yeteneği sağlamak için bu tür parametresi kısıtlaması uygular `T` uygulamak için <xref:System.IComparable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3754a-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="3754a-131">Kod <xref:System.IComparable%601.CompareTo%2A> yöntemi yerine `=` işleci, bir tür bağımsız değişkeni için sağlanan garanti olduğundan `T` destekler `=` işleci.</span><span class="sxs-lookup"><span data-stu-id="3754a-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="3754a-132">Test edebilirsiniz `findElement` aşağıdaki kodla yordamı.</span><span class="sxs-lookup"><span data-stu-id="3754a-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="3754a-133">Önceki çağrılar `MsgBox` sırasıyla "0", "1" ve "-1" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3754a-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3754a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3754a-134">See Also</span></span>  
 [<span data-ttu-id="3754a-135">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="3754a-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="3754a-136">Nasıl yapılır: Farklı Veri Türlerinde Aynı İşlevselliği Sağlayabilen Bir Sınıf Tanımlama</span><span class="sxs-lookup"><span data-stu-id="3754a-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="3754a-137">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="3754a-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="3754a-138">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="3754a-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="3754a-139">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="3754a-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3754a-140">Tür Listesi</span><span class="sxs-lookup"><span data-stu-id="3754a-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="3754a-141">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="3754a-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
