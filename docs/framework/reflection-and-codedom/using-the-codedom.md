---
title: CodeDOM'yi Kullanma
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bb3ab57d78e1a7b6d53261af50d4698ab1a4ff2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-codedom"></a><span data-ttu-id="71501-102">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="71501-102">Using the CodeDOM</span></span>
<span data-ttu-id="71501-103">CodeDOM genel türlerde kaynak kod öğeleri temsil eden türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="71501-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="71501-104">Bir nesne grafiğinin derlemek için CodeDOM öğeleri kullanılarak bir kaynak kod modeli derlemeler bir program tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71501-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="71501-105">Bu nesne grafiği, kaynak kodu CodeDOM Kod Oluşturucu için desteklenen bir programlama dili kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="71501-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="71501-106">CodeDOM ikili derlemeye kaynak kodu derlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71501-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="71501-107">CodeDOM için bazı yaygın kullanımları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="71501-107">Some common uses for the CodeDOM include:</span></span>  
  
-   <span data-ttu-id="71501-108">Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy'leri, kod sihirbazları, tasarımcıları veya diğer kod yayma mekanizmaları için kod oluşturma.</span><span class="sxs-lookup"><span data-stu-id="71501-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
-   <span data-ttu-id="71501-109">Dinamik derleme: tek veya birden çok dil kodu derleme destekleme.</span><span class="sxs-lookup"><span data-stu-id="71501-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="71501-110">CodeDOM grafik oluşturma</span><span class="sxs-lookup"><span data-stu-id="71501-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="71501-111"><xref:System.CodeDom> Ad alanı dili sözdizimini bağımsız kaynak kodu mantıksal yapısını temsil eden sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="71501-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="71501-112">CodeDOM grafik yapısı</span><span class="sxs-lookup"><span data-stu-id="71501-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="71501-113">CodeDOM grafik kapsayıcıları ağacının gibi yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="71501-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="71501-114">En üstteki, veya kök, kapsayıcı her derlenebilir CodeDOM grafiğin bir <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="71501-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="71501-115">Kaynak kodu modelinizin her öğenin özelliği aracılığıyla grafiği içine bağlanmalıdır bir <xref:System.CodeDom.CodeObject> grafikte.</span><span class="sxs-lookup"><span data-stu-id="71501-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="71501-116">Bir kaynak kod modeli için bir örnek Hello World Program oluşturma</span><span class="sxs-lookup"><span data-stu-id="71501-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="71501-117">Aşağıdaki örneklerde, basit bir Hello World uygulamasının kodunu temsil eden bir CodeDOM Nesne grafiği oluşturmak nasıl bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="71501-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="71501-118">Bu kod örneği için tam kaynak kodunu için bkz: <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> konu.</span><span class="sxs-lookup"><span data-stu-id="71501-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="71501-119">Derleme birimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="71501-119">Creating a compile unit</span></span>  
 <span data-ttu-id="71501-120">CodeDOM adlı bir nesne tanımlayan bir <xref:System.CodeDom.CodeCompileUnit>, hangi derlemek için kaynak kodu modelleri CodeDOM nesne grafiğinin başvuru.</span><span class="sxs-lookup"><span data-stu-id="71501-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="71501-121">A **CodeCompileUnit** öznitelikler, ad alanları ve derlemeler başvurularını depolamak için özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="71501-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="71501-122">Öğesinden türetilen CodeDom sağlayıcıları <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı tarafından başvurulan nesne grafiği işleme yöntemleri içeren bir **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="71501-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="71501-123">Basit bir uygulama için bir nesne grafiğinin oluşturmak için kaynak kod modeli derlemek ve ondan başvuran bir **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="71501-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="71501-124">Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="71501-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="71501-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> bir bölümünü zaten hedef dilde olan ancak başka bir dilde işlenemiyor. kaynak kodu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="71501-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="71501-126">Bir ad alanı tanımlama</span><span class="sxs-lookup"><span data-stu-id="71501-126">Defining a namespace</span></span>  
 <span data-ttu-id="71501-127">Bir ad alanı tanımlamak üzere oluşturma bir <xref:System.CodeDom.CodeNamespace> ve uygun oluşturucuyu kullanarak veya ayarlayarak bir ad atayın kendi **adı** özelliği.</span><span class="sxs-lookup"><span data-stu-id="71501-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="71501-128">Bir ad alanı içe aktarma</span><span class="sxs-lookup"><span data-stu-id="71501-128">Importing a namespace</span></span>  
 <span data-ttu-id="71501-129">Ad alanına ad alanı içe aktarma yönergesi eklemek için Ekle bir <xref:System.CodeDom.CodeNamespaceImport> almak için ad alanı gösterir **CodeNamespace.Imports** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="71501-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="71501-130">Alma için aşağıdaki kodu ekler **sistem** ad alanına **içeri aktarmalar** koleksiyonu bir **CodeNamespace** adlı `samples`:</span><span class="sxs-lookup"><span data-stu-id="71501-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="71501-131">Nesne grafiği kod öğeleri bağlama</span><span class="sxs-lookup"><span data-stu-id="71501-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="71501-132">CodeDOM grafik form tüm kod öğeleri bağlanması <xref:System.CodeDom.CodeCompileUnit> diğer bir deyişle başvuruları doğrudan kök nesnesi grafik özelliklerinden başvuru öğeler arasında bir dizi ağacın kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="71501-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="71501-133">Kapsayıcı nesne başvurusundan kurmak için bir kapsayıcı nesnesinin bir özellik için bir nesne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71501-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="71501-134">Aşağıdaki deyim ekler `samples` **CodeNamespace** için **ad alanları** koleksiyon özelliği kök **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="71501-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="71501-135">Bir türü tanımlama</span><span class="sxs-lookup"><span data-stu-id="71501-135">Defining a type</span></span>  
 <span data-ttu-id="71501-136">Bir sınıf, yapı, arabirimi ya da CodeDOM kullanarak numaralandırması bildirmek için yeni bir oluşturma <xref:System.CodeDom.CodeTypeDeclaration>ve bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="71501-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="71501-137">Aşağıdaki örnekte bu ayarlamak için bir oluşturucu aşırı kullanmayı gösterir. **adı** özelliği:</span><span class="sxs-lookup"><span data-stu-id="71501-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="71501-138">Bir tür için bir ad eklemek için Ekle bir <xref:System.CodeDom.CodeTypeDeclaration> ad alanına eklemek için türünü temsil eden **türleri** koleksiyonu bir **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="71501-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="71501-139">Aşağıdaki örnek adlı bir sınıf eklemek gösterilmiştir `class1` için bir **CodeNamespace** adlı `samples`:</span><span class="sxs-lookup"><span data-stu-id="71501-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="71501-140">Sınıf üyeleri için sınıf ekleme</span><span class="sxs-lookup"><span data-stu-id="71501-140">Adding class members to a class</span></span>  
 <span data-ttu-id="71501-141"><xref:System.CodeDom> Ad alanı, sınıf üyeleri temsil etmek için kullanılan öğelerin çeşitli sağlar.</span><span class="sxs-lookup"><span data-stu-id="71501-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="71501-142">Her sınıf üyesi eklenebilir **üyeleri** koleksiyonu bir <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="71501-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="71501-143">Yürütülebilir bir dosya için bir kod giriş noktası yöntem tanımlama</span><span class="sxs-lookup"><span data-stu-id="71501-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="71501-144">Kod bir yürütülebilir programı için oluşturuluyorsa oluşturarak bir programın giriş noktasını belirtmek gerekli olan bir <xref:System.CodeDom.CodeEntryPointMethod> program yürütme başlamalıdır yöntemi temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="71501-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="71501-145">Aşağıdaki örnek içeren bir giriş noktası yöntemi tanımlamak gösterilmiştir bir <xref:System.CodeDom.CodeMethodInvokeExpression> çağrısı **System.Console.WriteLine** "Hello World!" yazdırmak için:</span><span class="sxs-lookup"><span data-stu-id="71501-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="71501-146">Aşağıdaki deyim adlı giriş noktası yöntemi ekler `Start` için **üyeleri** koleksiyonu `class1`:</span><span class="sxs-lookup"><span data-stu-id="71501-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="71501-147">Şimdi <xref:System.CodeDom.CodeCompileUnit> adlı `compileUnit` basit bir Hello World program CodeDOM grafik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="71501-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="71501-148">CodeDOM grafiğinden kodu oluşturma ve derleme hakkında daha fazla bilgi için bkz: [kaynak kodu oluşturma ve CodeDOM grafiğinden programını derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="71501-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="71501-149">CodeDOM grafik oluşturma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="71501-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="71501-150">CodeDOM ortak dil çalışma zamanı desteği programlama dillerinde bulunan kod öğeleri birçok ortak türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="71501-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="71501-151">CodeDOM tüm olası programlama dil özelliklerini temsil etmek için öğeleri sağlamak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="71501-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="71501-152">CodeDOM öğeleriyle kolayca gösterilemez kodu kapsüllenmiş içinde bir <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, veya bir <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="71501-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="71501-153">Ancak, parçacıkları diğer diller için otomatik olarak CodeDOM tarafından çevrilemiyor.</span><span class="sxs-lookup"><span data-stu-id="71501-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="71501-154">CodeDOM türlerinin her belge için başvuru belgelerine bakın <xref:System.CodeDom> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="71501-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="71501-155">Kod öğesi belirli bir türü temsil eden CodeDOM öğesi bulmak hızlı grafiği için bkz: [CodeDOM hızlı başvuru](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span><span class="sxs-lookup"><span data-stu-id="71501-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span></span>
