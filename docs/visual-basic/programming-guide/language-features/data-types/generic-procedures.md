---
title: Visual Basic'de Genel Yordamlar
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e019ca32277f93f798e99e996a3670c8302ba9b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="62d23-102">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="62d23-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="62d23-103">A *genel yordam*, olarak da bilinir bir *genel yöntem*, bir yordamı ile en az bir tür parametresi tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="62d23-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="62d23-104">Bu yordam çağrıları her saat veri türleri için kendi gereksinimlerine uyarlamak çağıran kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="62d23-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="62d23-105">Bir yordam yalnızca genel bir sınıf veya genel yapısı içinde tanımlanan genel değil.</span><span class="sxs-lookup"><span data-stu-id="62d23-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="62d23-106">Genel olması için yordam bunun sürebilir normal parametreleri yanı sıra en az bir tür parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="62d23-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="62d23-107">Genel sınıf veya yapı nongeneric yordamları ve nongeneric bir sınıf, yapı, içerebilir veya modülü genel yordamlar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="62d23-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="62d23-108">Genel bir yordam, normal parametre listesinde bir ve kendi yordamdaki kodu varsa, dönüş türü türü parametrelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d23-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="62d23-109">Tür Çıkarma</span><span class="sxs-lookup"><span data-stu-id="62d23-109">Type Inference</span></span>  
 <span data-ttu-id="62d23-110">Herhangi bir tür bağımsız değişkeni girmeden genel yordam çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d23-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="62d23-111">Bu şekilde çağırmak için yordam tür bağımsız değişkeni geçirmek için uygun veri türlerini belirlemek derleyici çalışır.</span><span class="sxs-lookup"><span data-stu-id="62d23-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="62d23-112">Bu adlı *türü çıkarımı*.</span><span class="sxs-lookup"><span data-stu-id="62d23-112">This is called *type inference*.</span></span> <span data-ttu-id="62d23-113">Aşağıdaki kod bir çağrı gösterir derleyici türü geçirmelisiniz oluşturur, `String` tür parametresi için `t`.</span><span class="sxs-lookup"><span data-stu-id="62d23-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="62d23-114">Tür bağımsız değişkenleri aramanız bağlamından derleyici gösterilemez bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="62d23-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="62d23-115">Böyle bir hata bir olası nedeni bir dizi derece eşleşmemesidir.</span><span class="sxs-lookup"><span data-stu-id="62d23-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="62d23-116">Örneğin, bir tür parametresi bir dizi normal parametresini tanımlama varsayalım.</span><span class="sxs-lookup"><span data-stu-id="62d23-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="62d23-117">Genel yordam çağrısı, farklı bir derece (boyutları sayısı), bir dizi sağladığını uyuşmazlığı tür çıkarımı başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="62d23-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="62d23-118">Aşağıdaki kod bir çağrı gösterir, iki boyutlu bir dizi tek boyutlu dizi bekliyor yordamına geçirilen içinde.</span><span class="sxs-lookup"><span data-stu-id="62d23-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 <span data-ttu-id="62d23-119">Tür çıkarımı yalnızca tüm tür bağımsız değişkenleri kaldırarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62d23-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="62d23-120">Bir tür bağımsız değişkeni sağlarsanız, tümünü sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62d23-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="62d23-121">Tür çıkarımı yalnızca genel yordamlar için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="62d23-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="62d23-122">Tür çıkarımı Genel sınıflar, yapılar, arabirimleri veya temsilciler üzerinde çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="62d23-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62d23-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="62d23-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="62d23-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62d23-124">Description</span></span>  
 <span data-ttu-id="62d23-125">Aşağıdaki örnek, genel tanımlar `Function` bir dizide belirli bir öğeyi bulmak için yordamı.</span><span class="sxs-lookup"><span data-stu-id="62d23-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="62d23-126">Bir tür parametresi tanımlar ve parametre listesinde iki parametre oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62d23-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="62d23-127">Kod</span><span class="sxs-lookup"><span data-stu-id="62d23-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="62d23-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62d23-128">Comments</span></span>  
 <span data-ttu-id="62d23-129">Önceki örnekte karşılaştırmak olanağı gerektirir `searchValue` her öğeye karşı `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="62d23-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="62d23-130">Bu yeteneği sağlamak amacıyla, tür parametresi kısıtlar `T` uygulamak için <xref:System.IComparable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="62d23-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="62d23-131">Kod kullanan <xref:System.IComparable%601.CompareTo%2A> yöntemi yerine `=` işleci, tür bağımsız değişkeni için sağlanan garanti olduğundan `T` destekler `=` işleci.</span><span class="sxs-lookup"><span data-stu-id="62d23-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="62d23-132">Test edebilirsiniz `findElement` aşağıdaki kodla yordamı.</span><span class="sxs-lookup"><span data-stu-id="62d23-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="62d23-133">Yukarıdaki çağrılar `MsgBox` sırasıyla görüntü "0", "1" ve "-1".</span><span class="sxs-lookup"><span data-stu-id="62d23-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d23-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62d23-134">See Also</span></span>  
 [<span data-ttu-id="62d23-135">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="62d23-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="62d23-136">Nasıl yapılır: farklı veri türlerinde aynı işlevselliği sağlayabilen bir sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="62d23-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="62d23-137">Nasıl yapılır: genel bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="62d23-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="62d23-138">Yordamları</span><span class="sxs-lookup"><span data-stu-id="62d23-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="62d23-139">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="62d23-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="62d23-140">Tür listesi</span><span class="sxs-lookup"><span data-stu-id="62d23-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="62d23-141">Parametre listesi</span><span class="sxs-lookup"><span data-stu-id="62d23-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
