---
title: CodeDOM'yi Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
ms.openlocfilehash: c4cab79976acae236de5a8eaad5a42cdba7d04f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130001"
---
# <a name="using-the-codedom"></a><span data-ttu-id="90c91-102">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="90c91-102">Using the CodeDOM</span></span>
<span data-ttu-id="90c91-103">CodeDOM birçok ortak kaynak kodu öğesi türünü temsil eden türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="90c91-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="90c91-104">Bir nesne grafiğini birleştirmek için CodeDOM öğelerini kullanarak kaynak kodu modeli oluşturan bir program tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90c91-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="90c91-105">Bu nesne grafiği, desteklenen bir programlama dili için CodeDOM Kod Oluşturucu kullanılarak kaynak kodu olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="90c91-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="90c91-106">CodeDOM, kaynak kodu ikili bir derlemeye derlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="90c91-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="90c91-107">CodeDOM için bazı yaygın kullanımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="90c91-107">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="90c91-108">Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy 'leri, kod sihirbazları, tasarımcılar veya diğer kod yayma mekanizmaları için kod üretme.</span><span class="sxs-lookup"><span data-stu-id="90c91-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="90c91-109">Dinamik derleme: kod derlemesini tek veya birden çok dilde destekleme.</span><span class="sxs-lookup"><span data-stu-id="90c91-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="90c91-110">CodeDOM grafiği oluşturma</span><span class="sxs-lookup"><span data-stu-id="90c91-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="90c91-111"><xref:System.CodeDom> ad alanı, dil sözdiziminden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="90c91-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="90c91-112">CodeDOM grafiğinin yapısı</span><span class="sxs-lookup"><span data-stu-id="90c91-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="90c91-113">CodeDOM grafiğinin yapısı bir kapsayıcı ağacı gibidir.</span><span class="sxs-lookup"><span data-stu-id="90c91-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="90c91-114">Her derlenebilir CodeDOM grafiğinin en üst veya kök, kapsayıcısı bir <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="90c91-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="90c91-115">Kaynak kodu modelinizdeki her öğe, grafikteki bir <xref:System.CodeDom.CodeObject> özelliği aracılığıyla grafiğe bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90c91-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="90c91-116">Örnek bir Merhaba Dünya program için kaynak kodu modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="90c91-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="90c91-117">Aşağıdaki izlenecek yol, basit bir Merhaba Dünya uygulaması için kodu temsil eden bir CodeDOM nesne grafiğinin nasıl derlendiğini gösteren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="90c91-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="90c91-118">Bu kod örneği için tüm kaynak kodu için <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="90c91-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="90c91-119">Derleme birimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="90c91-119">Creating a compile unit</span></span>  
 <span data-ttu-id="90c91-120">CodeDOM, derleme için kaynak kodu modelleyen bir CodeDOM nesne grafiğine başvuruda bulunan <xref:System.CodeDom.CodeCompileUnit>adlı bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="90c91-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="90c91-121">**CodeCompileUnit** , başvuruları özniteliklere, ad alanlarına ve derlemelere depolamaya yönelik özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="90c91-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="90c91-122"><xref:System.CodeDom.Compiler.CodeDomProvider> sınıfından türetilen CodeDom sağlayıcıları, bir **CodeCompileUnit**tarafından başvurulan nesne grafiğini işleyen yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="90c91-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="90c91-123">Basit bir uygulama için bir nesne grafiği oluşturmak için, kaynak kodu modelini oluşturmanız ve bir **CodeCompileUnit**öğesinden başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="90c91-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="90c91-124">Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90c91-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="90c91-125"><xref:System.CodeDom.CodeSnippetCompileUnit>, kaynak kodun zaten hedef dilde olan bir bölümünü içerebilir, ancak başka bir dile işlenemez.</span><span class="sxs-lookup"><span data-stu-id="90c91-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="90c91-126">Ad alanı tanımlama</span><span class="sxs-lookup"><span data-stu-id="90c91-126">Defining a namespace</span></span>  
 <span data-ttu-id="90c91-127">Bir ad alanı tanımlamak için bir <xref:System.CodeDom.CodeNamespace> oluşturun ve uygun oluşturucuyu kullanarak ya da **Name** özelliğini ayarlayarak bunun için bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="90c91-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="90c91-128">Ad alanı içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="90c91-128">Importing a namespace</span></span>  
 <span data-ttu-id="90c91-129">Ad alanına bir ad alanı içeri aktarma yönergesi eklemek için, **CodeNamespace. Imports** koleksiyonuna aktarılacak ad alanını belirten bir <xref:System.CodeDom.CodeNamespaceImport> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="90c91-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="90c91-130">Aşağıdaki kod, **System** ad alanı için `samples`adlı bir **CodeNamespace** **Imports** koleksiyonuna bir içeri aktarma ekler:</span><span class="sxs-lookup"><span data-stu-id="90c91-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="90c91-131">Kod öğelerini nesne grafiğine bağlama</span><span class="sxs-lookup"><span data-stu-id="90c91-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="90c91-132">CodeDOM grafiği oluşturan tüm kod öğeleri, grafiğin kök nesnesinin özelliklerinden doğrudan başvurulan öğeler arasında bir dizi başvuruya göre ağacın kök öğesi olan <xref:System.CodeDom.CodeCompileUnit> bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="90c91-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="90c91-133">Container nesnesinden bir başvuru oluşturmak için bir nesneyi kapsayıcı nesnesinin özelliğine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="90c91-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="90c91-134">Aşağıdaki ifade, **CodeNamespace** `samples`, kök **CodeCompileUnit**öğesinin **namespaces** koleksiyon özelliğine ekler.</span><span class="sxs-lookup"><span data-stu-id="90c91-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="90c91-135">Bir tür tanımlama</span><span class="sxs-lookup"><span data-stu-id="90c91-135">Defining a type</span></span>  
 <span data-ttu-id="90c91-136">CodeDOM kullanarak bir sınıf, yapı, arabirim veya sabit listesi bildirmek için yeni bir <xref:System.CodeDom.CodeTypeDeclaration>oluşturun ve bu ada bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="90c91-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="90c91-137">Aşağıdaki örnek, **ad** özelliğini ayarlamak için bir Oluşturucu aşırı yüklemesi kullanarak bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="90c91-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="90c91-138">Bir ad alanına bir tür eklemek için, bir **CodeNamespace** **Types** koleksiyonuna ad alanına eklenecek türü temsil eden bir <xref:System.CodeDom.CodeTypeDeclaration> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="90c91-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="90c91-139">Aşağıdaki örnek, `samples`adlı bir **CodeNamespace** `class1` adlı bir sınıfın nasıl ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="90c91-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="90c91-140">Sınıf üyelerini bir sınıfa ekleme</span><span class="sxs-lookup"><span data-stu-id="90c91-140">Adding class members to a class</span></span>  
 <span data-ttu-id="90c91-141"><xref:System.CodeDom> ad alanı, sınıf üyelerini temsil etmek için kullanılabilecek çeşitli öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="90c91-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="90c91-142">Her sınıf üyesi bir <xref:System.CodeDom.CodeTypeDeclaration>**Üyeler** koleksiyonuna eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="90c91-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="90c91-143">Yürütülebilir dosya için kod giriş noktası yöntemi tanımlama</span><span class="sxs-lookup"><span data-stu-id="90c91-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="90c91-144">Yürütülebilir bir program için kod oluşturuyorsanız, program yürütmenin başlayacağı yöntemi temsil eden bir <xref:System.CodeDom.CodeEntryPointMethod> oluşturarak programın giriş noktasını göstermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="90c91-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="90c91-145">Aşağıdaki örnek, "Merhaba Dünya!" yazdırmak için **System. Console. WriteLine** ' ı çağıran bir <xref:System.CodeDom.CodeMethodInvokeExpression> içeren bir giriş noktası yönteminin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="90c91-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="90c91-146">Aşağıdaki ifade, `Start` adlı giriş noktası yöntemini `class1`**Üyeler** koleksiyonuna ekler:</span><span class="sxs-lookup"><span data-stu-id="90c91-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="90c91-147">Artık `compileUnit` adlı <xref:System.CodeDom.CodeCompileUnit> basit bir Merhaba Dünya programı için CodeDOM grafiğini içerir.</span><span class="sxs-lookup"><span data-stu-id="90c91-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="90c91-148">CodeDOM grafiğinden kod oluşturma ve derleme hakkında daha fazla bilgi için bkz. [kaynak kodu oluşturma ve bir CodeDOM grafiğinden program derleme](generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="90c91-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="90c91-149">CodeDOM grafiği oluşturma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="90c91-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="90c91-150">CodeDOM, ortak dil çalışma zamanını destekleyen programlama dillerinde bulunan birçok ortak kod öğesi türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="90c91-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="90c91-151">CodeDOM, tüm olası programlama dili özelliklerini temsil eden öğeler sağlamak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="90c91-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="90c91-152">CodeDOM öğeleriyle kolayca gösterilemeyen kod <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>veya <xref:System.CodeDom.CodeSnippetCompileUnit>kapsüllenebilir.</span><span class="sxs-lookup"><span data-stu-id="90c91-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="90c91-153">Ancak, kod parçacıkları CodeDOM tarafından otomatik olarak diğer dillere çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="90c91-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="90c91-154">CodeDOM türlerinin her biri için belgeler için, <xref:System.CodeDom> ad alanı için başvuru belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="90c91-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="90c91-155">Belirli bir kod öğesi türünü temsil eden CodeDOM öğesini bulmak için hızlı bir grafik için, [CodeDOM hızlı başvurusuna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="90c91-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
