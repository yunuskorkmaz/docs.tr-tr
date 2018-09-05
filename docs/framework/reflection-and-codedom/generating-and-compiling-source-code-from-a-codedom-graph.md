---
title: CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5d1546bb9c47d30806d857fa55e1d19fdc2c777
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559098"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="73bb5-102">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="73bb5-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="73bb5-103"><xref:System.CodeDom.Compiler> Ad alanı, kaynak kodundan CodeDOM nesne grafikler oluşturma ve derleme desteklenen derleyicileri ile yönetmek için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="73bb5-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="73bb5-104">CodeDOM grafiği göre belirli bir programlama dili için kaynak kodunda bir kod sağlayıcısı üretebilir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="73bb5-105">Türetilen bir sınıf <xref:System.CodeDom.Compiler.CodeDomProvider> oluşturma ve dil sağlayıcısı destekler, kod derleme için yöntemler genellikle sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="73bb5-106">Kaynak kodu oluşturmak için bir CodeDOM kod sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="73bb5-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="73bb5-107">Belirli bir dilde kaynak kodu oluşturmak için oluşturulacak kaynak kodunun yapısını temsil eden CodeDOM grafiği gerekir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="73bb5-108">Aşağıdaki örnek bir örneğini oluşturma işlemini gösteren bir <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="73bb5-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="73bb5-109">Kod oluşturma için graf tipik olarak bulunan bir <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="73bb5-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="73bb5-110">Kodunu oluşturmak için bir **CodeCompileUnit** bir CodeDOM grafiği içeren, çağrı <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kod sağlayıcının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="73bb5-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="73bb5-111">Bu yöntem için bir parametre olan bir <xref:System.IO.TextWriter> bazen ilk oluşturmak için gerekli olacak şekilde kaynak kodunu oluşturmak için kullandığı bir **TextWriter** için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="73bb5-112">Aşağıdaki örnek oluşturma koddan gösterir bir **CodeCompileUnit** ve HelloWorld.cs olarak adlı bir dosyaya oluşturulan kaynak kod yazma.</span><span class="sxs-lookup"><span data-stu-id="73bb5-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="73bb5-113">Derlemeleri derlemek için bir CodeDOM kod sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="73bb5-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="73bb5-114">**Derleme çağırma**</span><span class="sxs-lookup"><span data-stu-id="73bb5-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="73bb5-115">CodeDom sağlayıcısı'nı kullanarak bir derleme olarak derlemek için olan bir derleyici bir dili derlemek için ya da kaynak kodu olmalıdır veya bir CodeDOM grafiğini, Kaynak Kodu derlemek için gelen oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="73bb5-116">Bir CodeDOM grafiği derleme yapıyorsanız geçirmek <xref:System.CodeDom.CodeCompileUnit> grafiğe içeren <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> kod sağlayıcının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="73bb5-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="73bb5-117">Bir derleyici anlayan bir dilde kaynak kodu dosyası varsa, kaynak kodu içeren dosyanın adını geçirin <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> CodeDom sağlayıcısının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="73bb5-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="73bb5-118">Derleyici için anlayan bir dilde kaynak kodu içeren bir dize geçebilen <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> CodeDom sağlayıcısının yöntemi.</span><span class="sxs-lookup"><span data-stu-id="73bb5-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="73bb5-119">**Derleme parametreleri yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="73bb5-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="73bb5-120">Tüm standart derleme çağırma yöntemleri bir CodeDom sağlayıcısının türü bir parametreye sahip <xref:System.CodeDom.Compiler.CompilerParameters> derleme için kullanılacak seçeneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="73bb5-121">İçinde çıkış derlemesi için bir dosya adı belirtebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> özelliği **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="73bb5-122">Aksi takdirde varsayılan çıkış dosyası adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73bb5-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="73bb5-123">Varsayılan olarak, yeni bir **CompilerParameters** ile başlatılır, <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliğini **false**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="73bb5-124">Yürütülebilir program derleme yapıyorsanız ayarlamalısınız **GenerateExecutable** özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="73bb5-125">Zaman **GenerateExecutable** ayarlanır **false**, derleyici bir sınıf kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73bb5-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="73bb5-126">CodeDOM grafiğinden, yürütülebilir bir dosya derleme yapıyorsanız bir <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="73bb5-127">Birden çok kod girişi noktası varsa, ayarlamak gerekli olabilir <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> özelliği **CompilerParameters** kullanmak için giriş noktasını tanımlayan sınıfının adı.</span><span class="sxs-lookup"><span data-stu-id="73bb5-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="73bb5-128">Oluşturulan yürütülebilir dosya içinde hata ayıklama bilgilerini dahil etmek için ayarlama <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="73bb5-129">Projenizi tüm derlemelere başvuru yapıyorsa, öğeleri olarak derleme adları belirtmelisiniz bir <xref:System.Collections.Specialized.StringCollection> olarak <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> özelliği **CompilerParameters** derleme çağrılırken kullanın.</span><span class="sxs-lookup"><span data-stu-id="73bb5-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="73bb5-130">Disk yerine bellek ayarlayarak yazılır bütünleştirilmiş derleyebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="73bb5-131">Bir derlemeyi bellekte oluşturulduğunda, kodunuzu oluşturulan bütünleştirilmiş koddan başvuru elde edebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="73bb5-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="73bb5-132">Bir derleme için yazılmış olan disk için oluşturulan derlemeden yolu edinebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> özelliği bir **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="73bb5-133">Derleme işlemi çağrılırken kullanılacak bir özel komut satırı bağımsız değişkenleri dize belirtmek için dize kümesi'nde <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="73bb5-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="73bb5-134">Derleyici işlemi çağırmak için bir Win32 güvenlik belirteci gerekiyorsa belirteç belirtin <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="73bb5-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="73bb5-135">Derlenmiş derlemeye bir Win32 kaynak dosyası bağlamak için Win32 kaynak dosyası adını belirtin. <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="73bb5-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="73bb5-136">Bu derlemeyi durdurmak bir uyarı düzeyinde belirtmek için ayarlayın <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> derlemeyi durdurmak, uyarı düzeyini temsil eden bir tamsayı özelliği.</span><span class="sxs-lookup"><span data-stu-id="73bb5-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="73bb5-137">Derleyici uyarılarını ayarlayarak karşılaşılırsa derlemeyi durdurmak için de yapılandırabilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliğini **true**.</span><span class="sxs-lookup"><span data-stu-id="73bb5-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="73bb5-138">Aşağıdaki kod örneği, türetilen bir CodeDom sağlayıcısı'nı kullanarak bir kaynak dosyası derleniyor gösterir <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="73bb5-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="73bb5-139">İlk desteğiyle dilleri</span><span class="sxs-lookup"><span data-stu-id="73bb5-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="73bb5-140">.NET Framework kod derleyicileri ve aşağıdaki dilleri için kod oluşturucuları sağlar: C#, Visual Basic, C++ ve JScript.</span><span class="sxs-lookup"><span data-stu-id="73bb5-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="73bb5-141">CodeDOM desteği, dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak, diğer diller için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="73bb5-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bb5-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73bb5-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [<span data-ttu-id="73bb5-143">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="73bb5-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [<span data-ttu-id="73bb5-144">CodeDOM hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="73bb5-144">CodeDOM Quick Reference</span></span>](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
