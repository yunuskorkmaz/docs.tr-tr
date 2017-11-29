---
title: "Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="6be50-102">Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6be50-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="6be50-103">Dizileri bağımsız değişkenler olarak yöntemi parametrelerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6be50-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="6be50-104">Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be50-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="6be50-105">Tek boyutlu diziler bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="6be50-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="6be50-106">Başlatılmış bir tek boyutlu dizi yönteme geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6be50-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="6be50-107">Örneğin, aşağıdaki deyim yazdırma yöntemi için bir dizi gönderir.</span><span class="sxs-lookup"><span data-stu-id="6be50-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="6be50-108">Aşağıdaki kod bir kısmi yazdırma yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6be50-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="6be50-109">Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="6be50-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="6be50-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6be50-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6be50-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be50-111">Description</span></span>  
 <span data-ttu-id="6be50-112">Aşağıdaki örnekte, bir dizeler dizisi başlatılır ve bağımsız değişken olarak geçirilen bir `PrintArray` dizeleri yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6be50-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="6be50-113">Yöntem dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6be50-113">The method displays the elements of the array.</span></span> <span data-ttu-id="6be50-114">Ardından, yöntemleri `ChangeArray` ve `ChangeArrayElement` bir dizi bağımsız değişkeni değere göre gönderme değişiklikleri dizi öğelerine engellemez olduğunu göstermek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6be50-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6be50-115">Kod</span><span class="sxs-lookup"><span data-stu-id="6be50-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="6be50-116">Çok boyutlu diziler bağımsız değişkenler olarak geçirme</span><span class="sxs-lookup"><span data-stu-id="6be50-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="6be50-117">Tek boyutlu dizi geçirdiğiniz aynı şekilde başlatılmış boyutlu bir diziye bir yönteme geçirin.</span><span class="sxs-lookup"><span data-stu-id="6be50-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="6be50-118">Aşağıdaki kod, iki boyutlu bir dizi bağımsız değişkeni olarak kabul eden bir yazdırma yöntemini kısmi bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6be50-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="6be50-119">Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.</span><span class="sxs-lookup"><span data-stu-id="6be50-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="6be50-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6be50-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6be50-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be50-121">Description</span></span>  
 <span data-ttu-id="6be50-122">Aşağıdaki örnekte, iki boyutlu dizisi başlatılır ve geçirilen `Print2DArray` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6be50-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="6be50-123">Yöntem dizinin öğelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6be50-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6be50-124">Kod</span><span class="sxs-lookup"><span data-stu-id="6be50-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6be50-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6be50-125">See Also</span></span>  
 [<span data-ttu-id="6be50-126">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6be50-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6be50-127">Diziler</span><span class="sxs-lookup"><span data-stu-id="6be50-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="6be50-128">Tek boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="6be50-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="6be50-129">Çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="6be50-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="6be50-130">Basit diziler</span><span class="sxs-lookup"><span data-stu-id="6be50-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
