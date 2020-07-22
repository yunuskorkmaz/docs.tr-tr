---
title: 'Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma'
description: Bkz. yansıma ile genel türleri İnceleme ve örnek oluşturma. IsGenericType, IsGenericParameter ve GenericParameterPosition özelliklerini kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: b57a0ed0c809da442dc9fcf202ad364060971f80
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865105"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="ccbaa-104">Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ccbaa-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="ccbaa-105">Genel türler hakkında bilgi, <xref:System.Type> genel türü temsil eden bir nesneyi inceleyerek, diğer türlerle ilgili bilgilerle aynı şekilde alınır:</span><span class="sxs-lookup"><span data-stu-id="ccbaa-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="ccbaa-106">Prensibi, genel bir türün <xref:System.Type> genel tür parametrelerini temsil eden bir nesne listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="ccbaa-107">Bu bölümdeki ilk yordam genel türleri inceler.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="ccbaa-108"><xref:System.Type>Tür bağımsız değişkenlerini genel tür tanımının tür parametrelerine bağlayarak, oluşturulmuş bir türü temsil eden bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="ccbaa-109">İkinci yordam bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="ccbaa-110">Genel bir tür ve tür parametrelerini incelemek için</span><span class="sxs-lookup"><span data-stu-id="ccbaa-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="ccbaa-111"><xref:System.Type>Genel türü temsil eden bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="ccbaa-112">Aşağıdaki kodda, türü C# işleci kullanılarak elde edilir `typeof` ( `GetType` Visual Basic `typeid` Visual C++).</span><span class="sxs-lookup"><span data-stu-id="ccbaa-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="ccbaa-113"><xref:System.Type>Nesne almanın diğer yolları için bkz. sınıf konusu <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="ccbaa-114">Bu yordamın geri kalanında, türünün adlı bir yöntem parametresinde yer aldığı unutulmamalıdır `t` .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="ccbaa-115"><xref:System.Type.IsGenericType%2A>Türün genel olup olmadığını anlamak için özelliğini kullanın ve <xref:System.Type.IsGenericTypeDefinition%2A> türün genel tür tanımı olup olmadığını anlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="ccbaa-116">Yöntemini kullanarak genel tür bağımsız değişkenlerini içeren bir dizi alın <xref:System.Type.GetGenericArguments%2A> .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="ccbaa-117">Her tür bağımsız değişkeni için, bir tür parametresi (örneğin, genel tür tanımında) veya tür parametresi için belirtilmiş bir tür (örneğin, oluşturulmuş bir tür için), <xref:System.Type.IsGenericParameter%2A> özelliğini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="ccbaa-118">Tür sisteminde, genel tür parametresi <xref:System.Type> , normal türler gibi bir örneği tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="ccbaa-119">Aşağıdaki kod, <xref:System.Type> genel bir tür parametresini temsil eden bir nesnenin adını ve parametre konumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="ccbaa-120">Burada parametre konumu önemsiz bir bilgi; başka bir genel türün tür bağımsız değişkeni olarak kullanılmış bir tür parametresi incelerken daha fazla ilgi çekici olur.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="ccbaa-121"><xref:System.Type.GetGenericParameterConstraints%2A>Tüm kısıtlamaları tek bir dizide elde etmek için yöntemini kullanarak bir genel tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını saptayın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="ccbaa-122">Kısıtlamaların belirli bir sırada olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="ccbaa-123">Bir <xref:System.Type.GenericParameterAttributes%2A> tür parametresindeki özel kısıtlamaları (örneğin, bir başvuru türü olması gerekir) bulmaya yönelik özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="ccbaa-124">Özelliği, aşağıdaki kodda gösterildiği gibi, bir varyansı temsil eden değerleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="ccbaa-125">Özel kısıtlama öznitelikleri bayraklardır ve <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType> hiçbir özel kısıtlama temsil eden aynı bayrak (), hiçbir Kovaryans veya değişken varyans de temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="ccbaa-126">Bu nedenle, bu koşullardan biri için test etmek üzere uygun maskeyi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="ccbaa-127">Bu durumda, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlama bayraklarını yalıtmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="ccbaa-128">Genel türde bir örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="ccbaa-128">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="ccbaa-129">Genel tür bir şablon gibidir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-129">A generic type is like a template.</span></span> <span data-ttu-id="ccbaa-130">Genel tür parametreleri için gerçek türler belirtmediğiniz müddetçe, bunun örneklerini oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="ccbaa-131">Bunu çalışma zamanında, yansıma kullanarak yapmak için <xref:System.Type.MakeGenericType%2A> yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="ccbaa-132">Genel türün bir örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ccbaa-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="ccbaa-133"><xref:System.Type>Genel türü temsil eden bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="ccbaa-134">Aşağıdaki kod, genel türü <xref:System.Collections.Generic.Dictionary%602> iki farklı şekilde alır: <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi tanımlayan bir dize ile yöntem aşırı yüklemesini kullanarak ve <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür üzerinde yöntemini çağırarak `Dictionary\<String, Example>` ( `Dictionary(Of String, Example)` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ccbaa-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="ccbaa-135"><xref:System.Type.MakeGenericType%2A>Yöntemi genel bir tür tanımı gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="ccbaa-136">Tür parametrelerinin yerine geçecek tür bağımsız değişkenleri dizisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="ccbaa-137">Dizi, <xref:System.Type> tür parametresi listesinde göründükleri şekilde doğru sayıda nesne içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="ccbaa-138">Bu durumda, anahtar (ilk tür parametresi) türündedir <xref:System.String> ve sözlükteki değerler adlı bir sınıfın örnekleridir `Example` .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="ccbaa-139">Tür <xref:System.Type.MakeGenericType%2A> bağımsız değişkenlerini tür parametrelerine bağlamak ve türü oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="ccbaa-140"><xref:System.Activator.CreateInstance%28System.Type%29>Oluşturulmuş türden bir nesne oluşturmak için yöntem aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="ccbaa-141">Aşağıdaki kod, `Example` elde edilen nesnede sınıfının iki örneğini depolar `Dictionary<String, Example>` .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="ccbaa-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccbaa-142">Example</span></span>  
 <span data-ttu-id="ccbaa-143">Aşağıdaki kod örneği, `DisplayGenericType` genel tür tanımlarını ve kodda kullanılan oluşturulmuş türleri incelemek için bir yöntem tanımlar ve bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="ccbaa-144">`DisplayGenericType`Yöntemi <xref:System.Type.IsGenericType%2A> ,, <xref:System.Type.IsGenericParameter%2A> ve <xref:System.Type.GenericParameterPosition%2A> özelliklerinin ve <xref:System.Type.GetGenericArguments%2A> yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="ccbaa-145">Örnek ayrıca `DisplayGenericParameter` genel tür parametresini İnceleme ve kısıtlamalarını görüntüleme yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="ccbaa-146">Kod örneği, tür parametresi kısıtlamalarını gösteren genel bir tür da dahil olmak üzere bir dizi test türü tanımlar ve bu türler hakkındaki bilgilerin nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="ccbaa-147">Örnek, <xref:System.Collections.Generic.Dictionary%602> türünde bağımsız değişkenlerin bir dizisini oluşturarak ve yöntemini çağırarak sınıfından bir tür oluşturur <xref:System.Type.MakeGenericType%2A> .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="ccbaa-148">Program, <xref:System.Type> kullanılarak oluşturulan nesneyi <xref:System.Type.MakeGenericType%2A> <xref:System.Type> `typeof` (Visual Basic) kullanarak, aynı olduğunu gösteren ile karşılaştırır `GetType` .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="ccbaa-149">Benzer şekilde, program, <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türün genel tür tanımını elde etmek için yöntemini kullanır ve <xref:System.Type> sınıfı temsil eden nesneyle karşılaştırır <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="ccbaa-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ccbaa-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccbaa-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="ccbaa-151">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ccbaa-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="ccbaa-152">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ccbaa-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="ccbaa-153">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="ccbaa-153">Generics</span></span>](../../standard/generics/index.md)
