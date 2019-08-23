---
title: 'Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6517edcc2784b7d70c08c4d15d837fc1f209c49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928236"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="5166f-102">Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5166f-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="5166f-103">Genel türler hakkında bilgi, genel türü temsil eden bir <xref:System.Type> nesneyi inceleyerek, diğer türlerle ilgili bilgilerle aynı şekilde alınır:</span><span class="sxs-lookup"><span data-stu-id="5166f-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="5166f-104">Prensibi, genel bir türün genel tür parametrelerini temsil eden bir <xref:System.Type> nesne listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5166f-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="5166f-105">Bu bölümdeki ilk yordam genel türleri inceler.</span><span class="sxs-lookup"><span data-stu-id="5166f-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="5166f-106">Tür bağımsız değişkenlerini genel <xref:System.Type> tür tanımının tür parametrelerine bağlayarak, oluşturulmuş bir türü temsil eden bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5166f-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="5166f-107">İkinci yordam bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5166f-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="5166f-108">Genel bir tür ve tür parametrelerini incelemek için</span><span class="sxs-lookup"><span data-stu-id="5166f-108">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="5166f-109">Genel türü temsil <xref:System.Type> eden bir örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="5166f-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="5166f-110">C# `typeof` Aşağıdaki kodda, türü işleci kullanılarak elde edilir (`GetType` Visual Basic, `typeid` görselde C++).</span><span class="sxs-lookup"><span data-stu-id="5166f-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="5166f-111">Nesne almanın diğer yolları için bkz. sınıfkonusu.<xref:System.Type> <xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="5166f-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="5166f-112">Bu yordamın geri kalanında, türünün adlı `t`bir yöntem parametresinde yer aldığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5166f-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="5166f-113">Türün genel olup olmadığını anlamak için <xref:System.Type.IsGenericTypeDefinition%2A> özelliğinikullanınvetürüngeneltürtanımıolupolmadığınıanlamakiçinözelliğinikullanın.<xref:System.Type.IsGenericType%2A></span><span class="sxs-lookup"><span data-stu-id="5166f-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="5166f-114"><xref:System.Type.GetGenericArguments%2A> Yöntemini kullanarak genel tür bağımsız değişkenlerini içeren bir dizi alın.</span><span class="sxs-lookup"><span data-stu-id="5166f-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="5166f-115">Her tür bağımsız değişkeni için, bir tür parametresi (örneğin, genel tür tanımında) veya tür parametresi için belirtilmiş bir tür (örneğin, oluşturulmuş bir tür için), <xref:System.Type.IsGenericParameter%2A> özelliğini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5166f-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="5166f-116">Tür sisteminde, genel tür parametresi <xref:System.Type>, normal türler gibi bir örneği tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="5166f-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="5166f-117">Aşağıdaki kod, genel bir tür parametresini temsil eden bir <xref:System.Type> nesnenin adını ve parametre konumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5166f-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="5166f-118">Burada parametre konumu önemsiz bir bilgi; başka bir genel türün tür bağımsız değişkeni olarak kullanılmış bir tür parametresi incelerken daha fazla ilgi çekici olur.</span><span class="sxs-lookup"><span data-stu-id="5166f-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="5166f-119">Tüm kısıtlamaları tek bir dizide elde etmek için <xref:System.Type.GetGenericParameterConstraints%2A> yöntemini kullanarak bir genel tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını saptayın.</span><span class="sxs-lookup"><span data-stu-id="5166f-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="5166f-120">Kısıtlamaların belirli bir sırada olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="5166f-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="5166f-121">Bir tür parametresindeki özel kısıtlamaları (örneğin, bir başvuru türü olması gerekir) bulmaya yönelik özelliğinikullanın.<xref:System.Type.GenericParameterAttributes%2A></span><span class="sxs-lookup"><span data-stu-id="5166f-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="5166f-122">Özelliği, aşağıdaki kodda gösterildiği gibi, bir varyansı temsil eden değerleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="5166f-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="5166f-123">Özel kısıtlama öznitelikleri bayraklardır ve hiçbir özel kısıtlama temsil eden aynı<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>bayrak (), hiçbir Kovaryans veya değişken varyans de temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5166f-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="5166f-124">Bu nedenle, bu koşullardan biri için test etmek üzere uygun maskeyi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5166f-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="5166f-125">Bu durumda, özel kısıtlama <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> bayraklarını yalıtmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5166f-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="5166f-126">Genel türde bir örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="5166f-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="5166f-127">Genel tür bir şablon gibidir.</span><span class="sxs-lookup"><span data-stu-id="5166f-127">A generic type is like a template.</span></span> <span data-ttu-id="5166f-128">Genel tür parametreleri için gerçek türler belirtmediğiniz müddetçe, bunun örneklerini oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5166f-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="5166f-129">Bunu çalışma zamanında, yansıma kullanarak yapmak için <xref:System.Type.MakeGenericType%2A> yöntemi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5166f-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="5166f-130">Genel türün bir örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5166f-130">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="5166f-131">Genel türü <xref:System.Type> temsil eden bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="5166f-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="5166f-132">Aşağıdaki <xref:System.Collections.Generic.Dictionary%602> kod, genel türü iki farklı şekilde alır: <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi tanımlayan bir dize ile yöntem aşırı yüklemesini kullanarak ve oluşturulan tür `Dictionary\<String, Example>` üzerinde <xref:System.Type.GetGenericTypeDefinition%2A> yöntemini çağırarak (`Dictionary(Of String, Example)` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5166f-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="5166f-133"><xref:System.Type.MakeGenericType%2A> Yöntemi genel bir tür tanımı gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="5166f-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="5166f-134">Tür parametrelerinin yerine geçecek tür bağımsız değişkenleri dizisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5166f-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="5166f-135">Dizi, tür parametresi listesinde göründükleri şekilde doğru <xref:System.Type> sayıda nesne içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5166f-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="5166f-136">Bu durumda, anahtar (ilk tür parametresi) türündedir <xref:System.String>ve sözlükteki değerler adlı `Example`bir sınıfın örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="5166f-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="5166f-137">Tür bağımsız değişkenlerini tür parametrelerine bağlamak ve türü oluşturmak için yönteminiçağırın.<xref:System.Type.MakeGenericType%2A></span><span class="sxs-lookup"><span data-stu-id="5166f-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="5166f-138">Oluşturulmuş türden bir nesne oluşturmak için yöntemaşırıyüklemesinikullanın.<xref:System.Activator.CreateInstance%28System.Type%29></span><span class="sxs-lookup"><span data-stu-id="5166f-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="5166f-139">Aşağıdaki kod, elde edilen `Example` `Dictionary<String, Example>` nesnede sınıfının iki örneğini depolar.</span><span class="sxs-lookup"><span data-stu-id="5166f-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="5166f-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="5166f-140">Example</span></span>  
 <span data-ttu-id="5166f-141">Aşağıdaki kod örneği, genel tür `DisplayGenericType` tanımlarını ve kodda kullanılan oluşturulmuş türleri incelemek için bir yöntem tanımlar ve bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5166f-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="5166f-142">Yöntemi,<xref:System.Type.IsGenericType%2A> ,ve<xref:System.Type.GenericParameterPosition%2A> özelliklerinin ve<xref:System.Type.GetGenericArguments%2A> yönteminin nasıl kullanılacağını gösterir. <xref:System.Type.IsGenericParameter%2A> `DisplayGenericType`</span><span class="sxs-lookup"><span data-stu-id="5166f-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="5166f-143">Örnek ayrıca genel tür parametresini `DisplayGenericParameter` İnceleme ve kısıtlamalarını görüntüleme yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5166f-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="5166f-144">Kod örneği, tür parametresi kısıtlamalarını gösteren genel bir tür da dahil olmak üzere bir dizi test türü tanımlar ve bu türler hakkındaki bilgilerin nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5166f-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="5166f-145">Örnek, türünde bağımsız değişkenlerin bir dizisini <xref:System.Collections.Generic.Dictionary%602> oluşturarak ve <xref:System.Type.MakeGenericType%2A> yöntemini çağırarak sınıfından bir tür oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5166f-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="5166f-146">Program, kullanılarak <xref:System.Type.MakeGenericType%2A> oluşturulan <xref:System.Type> nesneyi ( `typeof` <xref:System.Type> VisualBasic)kullanarak,aynıolduğunugösterenilekarşılaştırır.`GetType`</span><span class="sxs-lookup"><span data-stu-id="5166f-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="5166f-147">Benzer şekilde, program, oluşturulan <xref:System.Type.GetGenericTypeDefinition%2A> türün genel tür tanımını elde etmek için yöntemini kullanır ve <xref:System.Collections.Generic.Dictionary%602> sınıfı temsil eden <xref:System.Type> nesneyle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5166f-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5166f-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5166f-148">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="5166f-149">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5166f-149">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [<span data-ttu-id="5166f-150">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5166f-150">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="5166f-151">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5166f-151">Generics</span></span>](../../standard/generics/index.md)
