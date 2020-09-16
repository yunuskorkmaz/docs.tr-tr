---
title: CodeDOM'yi Kullanma
description: Bir nesne grafiğini birleştirmek için birçok ortak kaynak kodu öğesi türünü temsil eden türler sağlayan Kod Belge Nesne Modeli (CodeDOM) kullanın.
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
ms.openlocfilehash: 7a730a828488fd3ca04419588b3f32703dfda1c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541740"
---
# <a name="using-the-codedom"></a><span data-ttu-id="fac08-103">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="fac08-103">Using the CodeDOM</span></span>
<span data-ttu-id="fac08-104">CodeDOM birçok ortak kaynak kodu öğesi türünü temsil eden türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac08-104">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="fac08-105">Bir nesne grafiğini birleştirmek için CodeDOM öğelerini kullanarak kaynak kodu modeli oluşturan bir program tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fac08-105">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="fac08-106">Bu nesne grafiği, desteklenen bir programlama dili için CodeDOM Kod Oluşturucu kullanılarak kaynak kodu olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="fac08-106">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="fac08-107">CodeDOM, kaynak kodu ikili bir derlemeye derlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fac08-107">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="fac08-108">CodeDOM için bazı yaygın kullanımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fac08-108">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="fac08-109">Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy 'leri, kod sihirbazları, tasarımcılar veya diğer kod yayma mekanizmaları için kod üretme.</span><span class="sxs-lookup"><span data-stu-id="fac08-109">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="fac08-110">Dinamik derleme: kod derlemesini tek veya birden çok dilde destekleme.</span><span class="sxs-lookup"><span data-stu-id="fac08-110">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="fac08-111">CodeDOM grafiği oluşturma</span><span class="sxs-lookup"><span data-stu-id="fac08-111">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="fac08-112"><xref:System.CodeDom>Ad alanı, dil sözdiziminden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac08-112">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="fac08-113">CodeDOM grafiğinin yapısı</span><span class="sxs-lookup"><span data-stu-id="fac08-113">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="fac08-114">CodeDOM grafiğinin yapısı bir kapsayıcı ağacı gibidir.</span><span class="sxs-lookup"><span data-stu-id="fac08-114">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="fac08-115">Her bir derlenebilir CodeDOM grafiğinin en üst, veya kök kapsayıcısı bir <xref:System.CodeDom.CodeCompileUnit> .</span><span class="sxs-lookup"><span data-stu-id="fac08-115">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="fac08-116">Kaynak kodu modelinizdeki her öğe, grafikteki bir öğesinin özelliği aracılığıyla grafiğe bağlanmalıdır <xref:System.CodeDom.CodeObject> .</span><span class="sxs-lookup"><span data-stu-id="fac08-116">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="fac08-117">Örnek bir Merhaba Dünya program için kaynak kodu modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="fac08-117">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="fac08-118">Aşağıdaki izlenecek yol, basit bir Merhaba Dünya uygulaması için kodu temsil eden bir CodeDOM nesne grafiğinin nasıl derlendiğini gösteren bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac08-118">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="fac08-119">Bu kod örneği için tüm kaynak kodu için konusuna bakın <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fac08-119">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="fac08-120">Derleme birimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fac08-120">Creating a compile unit</span></span>  
 <span data-ttu-id="fac08-121">CodeDOM, <xref:System.CodeDom.CodeCompileUnit> kaynak kodu derlemek için modelleyen bir CodeDOM nesne grafiğine başvuruda bulunan, adlı bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fac08-121">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="fac08-122">**CodeCompileUnit** , başvuruları özniteliklere, ad alanlarına ve derlemelere depolamaya yönelik özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fac08-122">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="fac08-123">Sınıfından türetilen CodeDom sağlayıcıları, <xref:System.CodeDom.Compiler.CodeDomProvider> bir **CodeCompileUnit**tarafından başvurulan nesne grafiğini işleyen yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="fac08-123">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="fac08-124">Basit bir uygulama için bir nesne grafiği oluşturmak için, kaynak kodu modelini oluşturmanız ve bir **CodeCompileUnit**öğesinden başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fac08-124">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="fac08-125">Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fac08-125">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="fac08-126">, <xref:System.CodeDom.CodeSnippetCompileUnit> Kaynak kodun zaten hedef dilde olan bir bölümünü içerebilir, ancak başka bir dile işlenemez.</span><span class="sxs-lookup"><span data-stu-id="fac08-126">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="fac08-127">Ad alanı tanımlama</span><span class="sxs-lookup"><span data-stu-id="fac08-127">Defining a namespace</span></span>  
 <span data-ttu-id="fac08-128">Bir ad alanı tanımlamak için, <xref:System.CodeDom.CodeNamespace> uygun oluşturucuyu kullanarak veya **ad** özelliğini ayarlayarak bir ad oluşturun ve buna bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="fac08-128">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="fac08-129">Ad alanı içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="fac08-129">Importing a namespace</span></span>  
 <span data-ttu-id="fac08-130">Ad alanına içeri aktarma yönergesi eklemek için, <xref:System.CodeDom.CodeNamespaceImport> **CodeNamespace. Imports** koleksiyonuna aktarılacak ad alanını belirten bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fac08-130">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="fac08-131">Aşağıdaki kod, **sistem** ad alanı için adlı bir **CodeNamespace** **Imports** koleksiyonuna bir içeri aktarma ekler `samples` :</span><span class="sxs-lookup"><span data-stu-id="fac08-131">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="fac08-132">Kod öğelerini nesne grafiğine bağlama</span><span class="sxs-lookup"><span data-stu-id="fac08-132">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="fac08-133">CodeDOM grafiği oluşturan tüm kod öğeleri, <xref:System.CodeDom.CodeCompileUnit> grafiğin kök nesnesinin özelliklerinden doğrudan başvurulan öğeler arasında bir dizi başvuruya göre ağacın kök öğesi olan ile bağlantılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fac08-133">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="fac08-134">Container nesnesinden bir başvuru oluşturmak için bir nesneyi kapsayıcı nesnesinin özelliğine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fac08-134">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="fac08-135">Aşağıdaki ifade, `samples` **CodeNamespace** öğesini kök **CodeCompileUnit**öğesinin **namespaces** koleksiyon özelliğine ekler.</span><span class="sxs-lookup"><span data-stu-id="fac08-135">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="fac08-136">Bir tür tanımlama</span><span class="sxs-lookup"><span data-stu-id="fac08-136">Defining a type</span></span>  
 <span data-ttu-id="fac08-137">CodeDOM kullanarak bir sınıf, yapı, arabirim veya sabit listesi bildirmek için yeni bir oluşturun <xref:System.CodeDom.CodeTypeDeclaration> ve bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="fac08-137">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="fac08-138">Aşağıdaki örnek, **ad** özelliğini ayarlamak için bir Oluşturucu aşırı yüklemesi kullanarak bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="fac08-138">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="fac08-139">Bir ad alanına bir tür eklemek için, bir <xref:System.CodeDom.CodeTypeDeclaration> **CodeNamespace** **Types** koleksiyonuna ad alanına eklenecek türü temsil eden bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fac08-139">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="fac08-140">Aşağıdaki örnek `class1` adlı bir **CodeNamespace** adlı sınıfın nasıl ekleneceğini göstermektedir `samples` :</span><span class="sxs-lookup"><span data-stu-id="fac08-140">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="fac08-141">Sınıf üyelerini bir sınıfa ekleme</span><span class="sxs-lookup"><span data-stu-id="fac08-141">Adding class members to a class</span></span>  
 <span data-ttu-id="fac08-142"><xref:System.CodeDom>Ad alanı, sınıf üyelerini temsil etmek için kullanılabilecek çeşitli öğeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac08-142">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="fac08-143">Her sınıf üyesi bir öğesinin **Üyeler** koleksiyonuna eklenebilir <xref:System.CodeDom.CodeTypeDeclaration> .</span><span class="sxs-lookup"><span data-stu-id="fac08-143">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="fac08-144">Yürütülebilir dosya için kod giriş noktası yöntemi tanımlama</span><span class="sxs-lookup"><span data-stu-id="fac08-144">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="fac08-145">Yürütülebilir bir program için kod oluşturuyorsanız, <xref:System.CodeDom.CodeEntryPointMethod> Program yürütmenin başlayacağı yöntemi temsil edecek bir programın giriş noktasını göstermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="fac08-145">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="fac08-146">Aşağıdaki örnek, <xref:System.CodeDom.CodeMethodInvokeExpression> "Merhaba Dünya!" yazdırmak Için **System. Console. WriteLine** çağıran bir içeren bir giriş noktası yönteminin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fac08-146">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="fac08-147">Aşağıdaki ifade, `Start` öğesinin **Üyeler** koleksiyonuna adlı giriş noktası yöntemini ekler `class1` :</span><span class="sxs-lookup"><span data-stu-id="fac08-147">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="fac08-148">Şimdi <xref:System.CodeDom.CodeCompileUnit> adlandırılmış `compileUnit` bir basit Merhaba Dünya program için CodeDOM grafiğini içerir.</span><span class="sxs-lookup"><span data-stu-id="fac08-148">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="fac08-149">CodeDOM grafiğinden kod oluşturma ve derleme hakkında daha fazla bilgi için bkz. [kaynak kodu oluşturma ve bir CodeDOM grafiğinden program derleme](generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="fac08-149">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="fac08-150">CodeDOM grafiği oluşturma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="fac08-150">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="fac08-151">CodeDOM, ortak dil çalışma zamanını destekleyen programlama dillerinde bulunan birçok ortak kod öğesi türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="fac08-151">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="fac08-152">CodeDOM, tüm olası programlama dili özelliklerini temsil eden öğeler sağlamak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="fac08-152">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="fac08-153">CodeDOM öğeleriyle kolayca gösterilemeyen kod, bir,,, veya şeklinde kapsüllenebilir <xref:System.CodeDom.CodeSnippetExpression> <xref:System.CodeDom.CodeSnippetStatement> <xref:System.CodeDom.CodeSnippetTypeMember> <xref:System.CodeDom.CodeSnippetCompileUnit> .</span><span class="sxs-lookup"><span data-stu-id="fac08-153">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="fac08-154">Ancak, kod parçacıkları CodeDOM tarafından otomatik olarak diğer dillere çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="fac08-154">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="fac08-155">CodeDOM türlerinin her biri için belgeler için bkz <xref:System.CodeDom> . ad alanı için başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="fac08-155">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="fac08-156">Belirli bir kod öğesi türünü temsil eden CodeDOM öğesini bulmak için hızlı bir grafik için, [CodeDOM hızlı başvurusuna](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="fac08-156">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
