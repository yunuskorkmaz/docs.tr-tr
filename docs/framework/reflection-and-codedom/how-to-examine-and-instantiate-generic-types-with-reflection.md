---
title: "Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5439975adcb6329ef072ef5a2bc98155e56c033
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="d57e3-102">Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d57e3-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="d57e3-103">Genel türler hakkında bilgi tıpkı diğer türleri hakkında bilgi elde edilir: inceleniyor tarafından bir <xref:System.Type> genel türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d57e3-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="d57e3-104">İlkeye genel bir tür listesini içeren farktır <xref:System.Type> genel tür parametreleri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d57e3-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="d57e3-105">Bu bölümdeki ilk yordam genel türler inceler.</span><span class="sxs-lookup"><span data-stu-id="d57e3-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="d57e3-106">Oluşturabileceğiniz bir <xref:System.Type> genel tür tanımında türü parametreleri bağlama tür bağımsız değişkeni tarafından oluşturulan bir türü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d57e3-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="d57e3-107">İkinci yordam bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="d57e3-108">Genel bir tür ve tür parametrelerinin incelemek için</span><span class="sxs-lookup"><span data-stu-id="d57e3-108">To examine a generic type and its type parameters</span></span>  
  
1.  <span data-ttu-id="d57e3-109">Bir örneğini almak <xref:System.Type> , genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d57e3-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="d57e3-110">Aşağıdaki kodda, C# kullanarak türü elde `typeof` işleci (`GetType` Visual Basic'te `typeid` Visual C++'ta).</span><span class="sxs-lookup"><span data-stu-id="d57e3-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="d57e3-111">Bkz: <xref:System.Type> almak diğer yolları için sınıf konusuna bir <xref:System.Type> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="d57e3-112">Bu yordamın geri kalanını içinde adlandırılmış bir yöntem parametresinde türü içeriyordu Not `t`.</span><span class="sxs-lookup"><span data-stu-id="d57e3-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  <span data-ttu-id="d57e3-113">Kullanmak <xref:System.Type.IsGenericType%2A> türü genel olup olmadığını belirlemek ve kullanmak için özelliği <xref:System.Type.IsGenericTypeDefinition%2A> özellik türü bir genel tür tanımı olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="d57e3-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  <span data-ttu-id="d57e3-114">Kullanarak genel tür bağımsız değişkenleri içeren bir dizi almak <xref:System.Type.GetGenericArguments%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  <span data-ttu-id="d57e3-115">Her tür bağımsız değişkeni için bir tür parametresi (örneğin, bir genel tür tanımında) veya (örneğin, gelen bir oluşturulan türü), bir tür parametresi için belirtilen bir tür olup olmadığını belirleme kullanarak <xref:System.Type.IsGenericParameter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d57e3-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  <span data-ttu-id="d57e3-116">Tür sistemi genel tür parametresi bir örneği tarafından temsil edilen <xref:System.Type>, normal türleri gibi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="d57e3-117">Aşağıdaki kod adı ve parametre konumunu görüntüler bir <xref:System.Type> genel tür parametresi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d57e3-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="d57e3-118">Buraya Önemsiz bilgileri parametresi konumdur; Bunu başka bir genel tür bir tür bağımsız değişkeni olarak kullanılan bir tür parametresi incelerken daha fazla ilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  <span data-ttu-id="d57e3-119">Temel tür sınırlaması ve bir genel tür parametresi arabirimi kısıtlamaları kullanarak belirlemek <xref:System.Type.GetGenericParameterConstraints%2A> tek bir dizi tüm kısıtlamalar elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="d57e3-120">Kısıtlamaları belirli bir sırada olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="d57e3-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  <span data-ttu-id="d57e3-121">Kullanım <xref:System.Type.GenericParameterAttributes%2A> özelliği bir başvuru türü olmasını gerektiren gibi bir tür parametresi özel kısıtlamalar keşfedin.</span><span class="sxs-lookup"><span data-stu-id="d57e3-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="d57e3-122">Özellik ayrıca aşağıdaki kodda gösterildiği gibi devre dışı maskeleyebilirsiniz farkı temsil eden değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  <span data-ttu-id="d57e3-123">Bayrakları ve aynı bayrağı özel kısıtlaması öznitelikleridir (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) özel temsil eden kısıtlamaları da temsil eden Kovaryans veya değişken karşıtı yok.</span><span class="sxs-lookup"><span data-stu-id="d57e3-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="d57e3-124">Bu nedenle, ya da bu koşullar test etmek için uygun maskesi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="d57e3-125">Bu durumda, kullanarak <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlaması bayrakları yalıtmak için.</span><span class="sxs-lookup"><span data-stu-id="d57e3-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="d57e3-126">Genel bir tür örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="d57e3-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="d57e3-127">Genel bir tür gibi bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="d57e3-127">A generic type is like a template.</span></span> <span data-ttu-id="d57e3-128">Genel tür parametreleri gerçek türlerinde belirtmediğiniz sürece örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="d57e3-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="d57e3-129">Yansıma, kullanarak çalışma zamanında bunun için gerektirir <xref:System.Type.MakeGenericType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="d57e3-130">Genel bir tür örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d57e3-130">To construct an instance of a generic type</span></span>  
  
1.  <span data-ttu-id="d57e3-131">Alma bir <xref:System.Type> genel türünü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d57e3-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="d57e3-132">Genel türü aşağıdaki kodu alır <xref:System.Collections.Generic.Dictionary%602> iki farklı yolla: kullanarak <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini türünü tanımlayan bir dize ile çağırarak <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türünün yöntemi `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` içinde Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d57e3-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="d57e3-133"><xref:System.Type.MakeGenericType%2A> Yöntemi, bir genel tür tanımı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  <span data-ttu-id="d57e3-134">Tür bağımsız değişkeni için tür parametreleri değiştirmek için bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d57e3-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="d57e3-135">Dizi doğru sayıda içermelidir <xref:System.Type> türü parametre listesinde göründükleri gibi aynı sırada nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d57e3-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="d57e3-136">Bu durumda, anahtarı (ilk tür parametresi) türüdür <xref:System.String>, ve sözlükteki değerleri adlı bir sınıfın örneklerini `Example`.</span><span class="sxs-lookup"><span data-stu-id="d57e3-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  <span data-ttu-id="d57e3-137">Çağrı <xref:System.Type.MakeGenericType%2A> tür bağımsız değişkeni tür parametreleri bağlamak ve türü oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d57e3-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  <span data-ttu-id="d57e3-138">Kullanım <xref:System.Activator.CreateInstance%28System.Type%29> oluşturulan türünde bir nesne oluşturmak için yöntemi aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="d57e3-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="d57e3-139">Aşağıdaki kod iki örneğini depolar `Example` elde edilen içinde sınıf `Dictionary<String, Example>` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="d57e3-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="d57e3-140">Example</span></span>  
 <span data-ttu-id="d57e3-141">Aşağıdaki kod örneğinde tanımlayan bir `DisplayGenericType` genel tür tanımları ve kod içinde kullanılan oluşturulan türler inceleyin ve kendi bilgilerini görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d57e3-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="d57e3-142">`DisplayGenericType` Yönteminin nasıl kullanılacağını gösterir <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, ve <xref:System.Type.GenericParameterPosition%2A> özellikleri ve <xref:System.Type.GetGenericArguments%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="d57e3-143">Örnek ayrıca tanımlar bir `DisplayGenericParameter` genel tür parametresi inceleyin ve kendi kısıtlamaları görüntülemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d57e3-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="d57e3-144">Kod örneği, bir dizi türü parametresi kısıtlamaları gösterir ve bu tür hakkındaki bilgileri görüntülemek nasıl gösterir genel bir tür dahil olmak üzere test türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d57e3-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="d57e3-145">Örnek bir türden yapıları <xref:System.Collections.Generic.Dictionary%602> tür bağımsız değişkenleri dizisini oluşturarak ve çağırma sınıfı <xref:System.Type.MakeGenericType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d57e3-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="d57e3-146">Program karşılaştırır <xref:System.Type> kullanılarak oluşturulan nesne <xref:System.Type.MakeGenericType%2A> ile bir <xref:System.Type> kullanarak elde nesne `typeof` (`GetType` Visual Basic'te), bunların aynı olduğunu gösteren.</span><span class="sxs-lookup"><span data-stu-id="d57e3-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="d57e3-147">Benzer şekilde, programın kullandığı <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türün genel tür tanımında elde etmek için yöntemi ve kendisine karşılaştırır <xref:System.Type> nesnesini temsil eden <xref:System.Collections.Generic.Dictionary%602> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d57e3-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d57e3-148">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d57e3-148">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d57e3-149">C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="d57e3-149">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="d57e3-150">Hiçbir ek derleme başvurularını gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d57e3-150">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="d57e3-151">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="d57e3-151">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="d57e3-152">Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d57e3-152">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57e3-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d57e3-153">See Also</span></span>  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="d57e3-154">Yansıma ve genel türler</span><span class="sxs-lookup"><span data-stu-id="d57e3-154">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [<span data-ttu-id="d57e3-155">Tür bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d57e3-155">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [<span data-ttu-id="d57e3-156">Genel türler</span><span class="sxs-lookup"><span data-stu-id="d57e3-156">Generics</span></span>](../../../docs/standard/generics/index.md)
