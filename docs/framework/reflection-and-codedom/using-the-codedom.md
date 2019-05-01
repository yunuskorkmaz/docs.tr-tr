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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73810330c1ec44aa3a5edf47b3062bc2df267008
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792983"
---
# <a name="using-the-codedom"></a><span data-ttu-id="8a7c4-102">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="8a7c4-102">Using the CodeDOM</span></span>
<span data-ttu-id="8a7c4-103">CodeDOM, kaynak kod öğelerinin birçok ortak türleri temsil eden türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="8a7c4-104">Bir nesne grafiğini derlemek için CodeDOM öğelerini kullanarak bir kaynak kod modeli oluşturan bir program tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="8a7c4-105">Bu nesne grafiği, desteklenen bir programlama dili için bir CodeDOM kod üreticisi kullanan bir kaynak kodu olarak işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="8a7c4-106">CodeDOM, kaynak kodu ikili bir birleştirme dosyasına derlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="8a7c4-107">CodeDOM bazı yaygın kullanımları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-107">Some common uses for the CodeDOM include:</span></span>  
  
- <span data-ttu-id="8a7c4-108">Şablonlu kod oluşturma: ASP.NET, XML Web Hizmetleri istemci proxy'leri, kod sihirbazları, tasarımcılar veya diğer kod yayan mekanizmaları için kod oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
- <span data-ttu-id="8a7c4-109">Dinamik derleme: tek veya birden çok dilde kod derlemesini destekleme.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="8a7c4-110">CodeDOM grafiği derleme</span><span class="sxs-lookup"><span data-stu-id="8a7c4-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="8a7c4-111"><xref:System.CodeDom> Ad alanı dil sözdiziminden bağımsız kaynak kodu mantıksal yapısını temsil etmek için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="8a7c4-112">CodeDOM grafiği yapısı</span><span class="sxs-lookup"><span data-stu-id="8a7c4-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="8a7c4-113">CodeDOM grafiği yapısı, bir kapsayıcılar ağacı gibidir ' dir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="8a7c4-114">En üstteki veya kök, her bir derlenebilir CodeDOM grafiğinin kapsayıcı bir <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="8a7c4-115">Her öğenin kaynak kod modelinizin özelliği ile grafikle bağlanmalıdır bir <xref:System.CodeDom.CodeObject> grafiğinde.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="8a7c4-116">Örnek Hello World programı için bir kaynak kod modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a7c4-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="8a7c4-117">Aşağıdaki örneklerde, basit bir Hello World uygulaması kodunu temsil eden bir CodeDOM nesne grafiğinin nasıl bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="8a7c4-118">Bu kod örneği için tam kaynak kodunu görmek <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> konu.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="8a7c4-119">Derleme birimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8a7c4-119">Creating a compile unit</span></span>  
 <span data-ttu-id="8a7c4-120">CodeDOM adlı bir nesne tanımlayan bir <xref:System.CodeDom.CodeCompileUnit>, derlenecek kaynağı modelleyen bir CodeDOM nesnesi grafiğine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="8a7c4-121">A **CodeCompileUnit** başvuruları özniteliklere, ad alanları ve derlemelere depolama özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="8a7c4-122">Öğesinden türetilen CodeDom sağlayıcıları <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı tarafından başvurulan nesne grafiğini işleyen yöntemleri içeren bir **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="8a7c4-123">Basit bir uygulama için bir nesne grafiği oluşturmak için kaynak kod modelini bir araya getirmeli ve ondan başvuru bir **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="8a7c4-124">Bu örnekte gösterilen sözdizimi ile yeni bir derleme birimi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="8a7c4-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> hedef dilde zaten olan ancak başka bir dile işlenemeyen kaynak kodunun bir bölüm içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="8a7c4-126">Ad alanı tanımlama</span><span class="sxs-lookup"><span data-stu-id="8a7c4-126">Defining a namespace</span></span>  
 <span data-ttu-id="8a7c4-127">Ad alanı tanımlamak için oluşturun bir <xref:System.CodeDom.CodeNamespace> ve uygun oluşturucuyu kullanarak veya ayarlayarak bir ad atayın, **adı** özelliği.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="8a7c4-128">Bir ad alanı alma</span><span class="sxs-lookup"><span data-stu-id="8a7c4-128">Importing a namespace</span></span>  
 <span data-ttu-id="8a7c4-129">Ad alanı için bir ad alanı içe aktarma yönergesi eklemek için Ekle bir <xref:System.CodeDom.CodeNamespaceImport> almak için ad alanı belirten **CodeNamespace.Imports** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="8a7c4-130">Aşağıdaki kod bir içe aktarım ekler **sistem** ad alanına **içeri aktarmalar** koleksiyonunu bir **CodeNamespace** adlı `samples`:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="8a7c4-131">Kod öğelerini nesne grafiğine bağlama</span><span class="sxs-lookup"><span data-stu-id="8a7c4-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="8a7c4-132">CodeDOM grafiği oluşturan tüm kod öğelerini bağlanmalıdır <xref:System.CodeDom.CodeCompileUnit> diğer bir deyişle başvuruları grafiğin kök nesnesinin özelliklerinden doğrudan başvurulan öğeler arasındaki bir dizi göre ağacın kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="8a7c4-133">Bir nesneyi kapsayıcı nesnenin bir başvuru oluşturmak için bir kapsayıcı nesnenin bir özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="8a7c4-134">Aşağıdaki deyimi ekler `samples` **CodeNamespace** için **ad alanları** koleksiyon özelliği kök **CodeCompileUnit**.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="8a7c4-135">Türü tanımlama</span><span class="sxs-lookup"><span data-stu-id="8a7c4-135">Defining a type</span></span>  
 <span data-ttu-id="8a7c4-136">Bir sınıf, yapı, arabirimi ya da CodeDOM kullanarak numaralandırma bildirmek için yeni bir oluşturma <xref:System.CodeDom.CodeTypeDeclaration>ve bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="8a7c4-137">Aşağıdaki örnek bu ayarlamak için bir yapıcı yeniden yüklemesi kullanarak göstermektedir **adı** özelliği:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="8a7c4-138">Bir tür için bir ad alanı eklemek için Ekle bir <xref:System.CodeDom.CodeTypeDeclaration> ad alanına eklenecek türünü temsil eden **türleri** koleksiyonunu bir **CodeNamespace**.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="8a7c4-139">Aşağıdaki örnekte adlı bir sınıf eklemek gösterilmiştir `class1` için bir **CodeNamespace** adlı `samples`:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="8a7c4-140">Sınıf üyeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="8a7c4-140">Adding class members to a class</span></span>  
 <span data-ttu-id="8a7c4-141"><xref:System.CodeDom> Ad alanı sınıf üyelerini temsil etmek için kullanılan öğeleri çeşitli sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="8a7c4-142">Her sınıf üyesi eklenebilir **üyeleri** koleksiyonunu bir <xref:System.CodeDom.CodeTypeDeclaration>.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="8a7c4-143">Bir yürütülebilir dosya için bir kod girişi noktası yönetimini tanımlama</span><span class="sxs-lookup"><span data-stu-id="8a7c4-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="8a7c4-144">Yürütülebilir program kodunu oluşturuyorsanız oluşturarak programın giriş noktasını belirtmek gerekli bir <xref:System.CodeDom.CodeEntryPointMethod> , program yürütmenin başlaması gerektiği yöntemi temsil edecek.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="8a7c4-145">Aşağıdaki örnek içeren bir giriş noktası yönteminin nasıl tanımlanacağını gösterir bir <xref:System.CodeDom.CodeMethodInvokeExpression> çağrılarının **System.Console.WriteLine** "Hello World!" yazdırmak için:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="8a7c4-146">Aşağıdaki deyim adlı giriş noktası yöntemi eklemektedir `Start` için **üyeleri** koleksiyonunu `class1`:</span><span class="sxs-lookup"><span data-stu-id="8a7c4-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="8a7c4-147">Artık <xref:System.CodeDom.CodeCompileUnit> adlı `compileUnit` basit bir Hello World programı için CodeDOM grafiğini içerir.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="8a7c4-148">CodeDOM grafiğinden kodu oluşturma ve derleme hakkında daha fazla bilgi için bkz: [kaynak kodu üretme ve CodeDOM grafiğinden bir programı derleme](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span><span class="sxs-lookup"><span data-stu-id="8a7c4-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="8a7c4-149">CodeDOM grafik oluşturma hakkında daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="8a7c4-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="8a7c4-150">CodeDOM kod öğeleri, ortak dil çalışma zamanını destekleyen programlama dillerinde bulunan pek çok ortak türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="8a7c4-151">CodeDOM, olası programlama dili özelliklerini temsil edecek öğeleri sağlamak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="8a7c4-152">CodeDOM öğeleri ile kolayca gösterilemeyen kod, içinde kapsüllenebilir bir <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>, veya bir <xref:System.CodeDom.CodeSnippetCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="8a7c4-153">Ancak, kod parçacıkları diğer diller için otomatik olarak CodeDOM tarafından tercüme edilemez.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="8a7c4-154">CodeDOM türlerinin her biri için belgeler için başvuru belgelerine bakın <xref:System.CodeDom> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8a7c4-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="8a7c4-155">Belirli bir kod öğesi türünü temsil eden CodeDOM öğesini bulmaya yönelik hızlı bir grafik için bkz: [CodeDOM hızlı başvuru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8a7c4-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)).</span></span>
