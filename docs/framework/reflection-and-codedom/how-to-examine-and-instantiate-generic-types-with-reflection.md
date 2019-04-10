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
ms.openlocfilehash: ddddc746eb29c526adb8a15fc6ac40acc22954cf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337233"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="6a56f-102">Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a56f-102">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="6a56f-103">Genel türler hakkında bilgi tıpkı diğer türler hakkında bilgi elde edilir: inceleme tarafından bir <xref:System.Type> genel türü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-103">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="6a56f-104">İlkeye genel bir türün bir listesi olduğunu fark <xref:System.Type> , genel tür parametrelerini temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6a56f-104">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="6a56f-105">Bu bölümdeki ilk yordam, genel türler inceler.</span><span class="sxs-lookup"><span data-stu-id="6a56f-105">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="6a56f-106">Oluşturabileceğiniz bir <xref:System.Type> oluşturulan tür, genel tür tanımı için tür parametreleri bağlama tür bağımsız değişkeni tarafından temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-106">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="6a56f-107">İkinci yordam bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a56f-107">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="6a56f-108">Genel bir tür ve tür parametrelerinden biri incelemek için</span><span class="sxs-lookup"><span data-stu-id="6a56f-108">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="6a56f-109">Bir kopyasını almak <xref:System.Type> , genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6a56f-109">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="6a56f-110">Aşağıdaki kodda, türü kullanılarak edinilen C# `typeof` işleci (`GetType` Visual Basic'te `typeid` Visual C++'ta).</span><span class="sxs-lookup"><span data-stu-id="6a56f-110">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="6a56f-111">Bkz: <xref:System.Type> almanın diğer yolları için sınıf konusuna bir <xref:System.Type> nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-111">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="6a56f-112">Bu yordamın kalan adlı bir yöntem parametre türü içerdiği Not `t`.</span><span class="sxs-lookup"><span data-stu-id="6a56f-112">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="6a56f-113">Kullanma <xref:System.Type.IsGenericType%2A> türünün genel olup olmadığını belirlemek ve özellik <xref:System.Type.IsGenericTypeDefinition%2A> özellik türü bir genel tür tanımı olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="6a56f-113">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="6a56f-114">Kullanarak genel tür bağımsız değişkenleri içeren bir dizi alma <xref:System.Type.GetGenericArguments%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-114">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="6a56f-115">Her tür bağımsız değişkeni için bir tür parametresi (örneğin, bir genel tür tanımında) veya (örneğin, bir oluşturulmuş tür içinde), bir tür parametresi için belirtilen bir tür olup olmadığını belirlemek kullanarak <xref:System.Type.IsGenericParameter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6a56f-115">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="6a56f-116">İçindeki tür sisteminde, genel tür parametresi bir örneği tarafından temsil edilen <xref:System.Type>sıradan türleri aynı şekilde.</span><span class="sxs-lookup"><span data-stu-id="6a56f-116">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="6a56f-117">Aşağıdaki kod adı ve parametre konumunu görüntüleyen bir <xref:System.Type> bir genel tür parametresini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-117">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="6a56f-118">Parametresi, burada Önemsiz bilgi konumudur; Bu, başka bir genel türün tür bağımsız değişkeni kullanılan bir tür parametresi incelerken daha fazla ilgi olur.</span><span class="sxs-lookup"><span data-stu-id="6a56f-118">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="6a56f-119">Temel tür kısıtlaması ve genel tür parametresi kısıtlamaları arabirimi kullanarak belirlemek <xref:System.Type.GetGenericParameterConstraints%2A> tüm kısıtlamalar tek bir dizi elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-119">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="6a56f-120">Kısıtlamaları herhangi belirli bir sırada olması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="6a56f-120">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="6a56f-121">Kullanım <xref:System.Type.GenericParameterAttributes%2A> özelliği özel bir başvuru türü olmasını gerektirme gibi bir tür parametresi kısıtlamaları bulunacak.</span><span class="sxs-lookup"><span data-stu-id="6a56f-121">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="6a56f-122">Özelliği, ayrıca, aşağıdaki kodda gösterildiği gibi devre dışı maskeleyebilirsiniz varyansı gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a56f-122">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="6a56f-123">Bayraklar ve aynı bayrağı özel kısıtlaması öznitelikleridir (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) temsil eden özel kısıtlamaları da temsil Kovaryans veya kontravaryans yok.</span><span class="sxs-lookup"><span data-stu-id="6a56f-123">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="6a56f-124">Bu nedenle, Bu koşullardan birini test etmek için uygun maskesi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a56f-124">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="6a56f-125">Bu durumda, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlaması bayrakları yalıtmak için.</span><span class="sxs-lookup"><span data-stu-id="6a56f-125">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="6a56f-126">Genel bir türün bir örneği oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a56f-126">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="6a56f-127">Genel bir tür gibi bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="6a56f-127">A generic type is like a template.</span></span> <span data-ttu-id="6a56f-128">Kendi genel tür parametreleri için gerçek türler belirtmediğiniz sürece örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="6a56f-128">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="6a56f-129">Çalışma zamanında Bunu yapmak için yansıma kullanarak gerektirir <xref:System.Type.MakeGenericType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-129">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="6a56f-130">Genel bir türün bir örneğini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6a56f-130">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="6a56f-131">Alma bir <xref:System.Type> genel türü temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-131">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="6a56f-132">Aşağıdaki kod genel tür alır <xref:System.Collections.Generic.Dictionary%602> iki farklı yolla: kullanarak <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini çağırarak ve türünü tanımlayan bir dize <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür metodunda `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` içinde Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6a56f-132">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="6a56f-133"><xref:System.Type.MakeGenericType%2A> Yöntem genel tür tanımı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6a56f-133">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="6a56f-134">Tür parametreleri için eklenecek tür bağımsız değişkeni bir dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6a56f-134">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="6a56f-135">Dizi doğru sayıda içermelidir <xref:System.Type> türü parametre listesinde göründükleri gibi aynı sırada nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6a56f-135">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="6a56f-136">Bu durumda, anahtar türüdür (ilk tür parametresi) <xref:System.String>, ve sözlükteki değerlerin adlı bir sınıfın örneklerini `Example`.</span><span class="sxs-lookup"><span data-stu-id="6a56f-136">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="6a56f-137">Çağrı <xref:System.Type.MakeGenericType%2A> tür bağımsız değişkenleri için tür parametreleri bağlama ve tür oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="6a56f-137">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="6a56f-138">Kullanım <xref:System.Activator.CreateInstance%28System.Type%29> yöntemi aşırı yüklemesi, oluşturulan türde bir nesne oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6a56f-138">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="6a56f-139">Aşağıdaki kod iki örneğini depolar `Example` sonuç sınıfı `Dictionary<String, Example>` nesne.</span><span class="sxs-lookup"><span data-stu-id="6a56f-139">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="6a56f-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a56f-140">Example</span></span>  
 <span data-ttu-id="6a56f-141">Aşağıdaki kod örneği tanımlayan bir `DisplayGenericType` genel tür tanımları ve kod içinde kullanılan oluşturulan türler inceleyin ve kullanıcıların bilgilerini görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-141">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="6a56f-142">`DisplayGenericType` Yönteminin nasıl kullanılacağını göstermektedir <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, ve <xref:System.Type.GenericParameterPosition%2A> özellikleri ve <xref:System.Type.GetGenericArguments%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-142">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="6a56f-143">Örnek ayrıca tanımlar bir `DisplayGenericParameter` genel tür parametresi inceleyin ve kısıtlamaları görüntülemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-143">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="6a56f-144">Kod örneği, tür parametresi kısıtlamaları gösterir ve bu türleri hakkında bilgileri görüntülemeyi gösterir genel bir tür gibi test türleri kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a56f-144">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="6a56f-145">Bir türden örneğin yapıları <xref:System.Collections.Generic.Dictionary%602> sınıf türü bağımsız değişken bir dizi oluşturarak ve çağırma <xref:System.Type.MakeGenericType%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6a56f-145">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="6a56f-146">Program karşılaştırır <xref:System.Type> kullanılarak oluşturulan nesne <xref:System.Type.MakeGenericType%2A> ile bir <xref:System.Type> kullanılarak elde edilen nesnenin `typeof` (`GetType` Visual Basic'te), bunların aynı olduğunu gösteren.</span><span class="sxs-lookup"><span data-stu-id="6a56f-146">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="6a56f-147">Benzer şekilde, programın kullandığı <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür, genel tür tanımını almak için yöntemi ve kendisine karşılaştırır <xref:System.Type> nesnesini temsil eden <xref:System.Collections.Generic.Dictionary%602> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6a56f-147">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a56f-148">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6a56f-148">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6a56f-149">C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="6a56f-149">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="6a56f-150">Hiçbir ek derleme başvurularını gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a56f-150">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="6a56f-151">Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin.</span><span class="sxs-lookup"><span data-stu-id="6a56f-151">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="6a56f-152">Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.</span><span class="sxs-lookup"><span data-stu-id="6a56f-152">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a56f-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a56f-153">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="6a56f-154">Yansıma ve Genel Türler</span><span class="sxs-lookup"><span data-stu-id="6a56f-154">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [<span data-ttu-id="6a56f-155">Tür Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6a56f-155">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [<span data-ttu-id="6a56f-156">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="6a56f-156">Generics</span></span>](../../../docs/standard/generics/index.md)
