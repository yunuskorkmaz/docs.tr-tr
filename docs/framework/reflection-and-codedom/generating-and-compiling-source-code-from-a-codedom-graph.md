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
ms.openlocfilehash: 4f2576aa0d1cf6a4938c8b1c8ee7883251cc192d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046072"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="4097c-102">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="4097c-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="4097c-103">Ad <xref:System.CodeDom.Compiler> alanı, CodeDOM nesne grafiklerinden kaynak kodu oluşturmak ve desteklenen derleyicilerle derlemeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4097c-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="4097c-104">Bir kod sağlayıcısı, CodeDOM grafiğine göre belirli bir programlama dilinde kaynak kodu üretebilir.</span><span class="sxs-lookup"><span data-stu-id="4097c-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="4097c-105">Öğesinden <xref:System.CodeDom.Compiler.CodeDomProvider> türetilen bir sınıf genellikle sağlayıcının desteklediği dil için kod oluşturmak ve derlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4097c-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="4097c-106">Kaynak kodu oluşturmak için CodeDOM kod sağlayıcısı kullanma</span><span class="sxs-lookup"><span data-stu-id="4097c-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="4097c-107">Belirli bir dilde kaynak kodu oluşturmak için, oluşturulacak kaynak kodun yapısını temsil eden bir CodeDOM grafiğine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="4097c-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="4097c-108">Aşağıdaki örnek, bir <xref:Microsoft.CSharp.CSharpCodeProvider>örneğinin nasıl oluşturulacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="4097c-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="4097c-109">Kod oluşturma için grafik genellikle bir <xref:System.CodeDom.CodeCompileUnit>içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4097c-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="4097c-110">CodeDOM grafiği içeren bir **CodeCompileUnit** için kod oluşturmak üzere kod sağlayıcısının <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4097c-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="4097c-111">Bu yöntem, kaynak kodu oluşturmak için <xref:System.IO.TextWriter> kullandığı bir parametreye sahiptir, bu nedenle ilk olarak yazılacak bir **TextWriter** oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4097c-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="4097c-112">Aşağıdaki örnek, bir **CodeCompileUnit** öğesinden kod oluşturmayı ve oluşturulan kaynak kodu HelloWorld.cs adlı bir dosyaya yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4097c-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="4097c-113">Derlemeleri derlemek için CodeDOM kod sağlayıcısı kullanma</span><span class="sxs-lookup"><span data-stu-id="4097c-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="4097c-114">**Derleme çağrılıyor**</span><span class="sxs-lookup"><span data-stu-id="4097c-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="4097c-115">Bir CodeDom sağlayıcısı kullanarak bir derlemeyi derlemek için, derleyicinizin bulunduğu bir dilde derlemek için kaynak kodunuz veya derlenecek kaynak kodun üretibileceği bir CodeDOM Graf olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4097c-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="4097c-116">Bir CodeDOM grafiğinden derleme yapıyorsanız, grafiği <xref:System.CodeDom.CodeCompileUnit> <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> içeren kodu kod sağlayıcısının yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="4097c-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="4097c-117">Derleyicinin anladığı bir dilde kaynak kodu dosyanız varsa, kaynak kodu <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> içeren dosyanın adını CodeDom sağlayıcısı yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="4097c-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="4097c-118">Ayrıca, kaynak kodu içeren bir dizeyi derleyicinin CodeDom sağlayıcısı <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> yöntemine anladığı bir dilde geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4097c-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="4097c-119">**Derleme parametrelerini yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="4097c-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="4097c-120">Bir CodeDOM sağlayıcısının standart derleme çağırma yöntemlerinin hepsi, derleme için kullanılacak seçenekleri belirten türünde <xref:System.CodeDom.Compiler.CompilerParameters> bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4097c-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="4097c-121"><xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> **CompilerParameters**özelliğinde çıkış derlemesi için bir dosya adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4097c-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="4097c-122">Aksi takdirde, varsayılan bir çıkış dosyası adı kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="4097c-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="4097c-123">Varsayılan olarak, yeni bir **CompilerParameters** <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliği **false**olarak ayarlanmış şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4097c-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="4097c-124">Yürütülebilir bir program derlerken **GenerateExecutable** özelliğini **true**olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4097c-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="4097c-125">**Generateyürütülebilirdeğeri** **false**olarak ayarlandığında, derleyici bir sınıf kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4097c-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="4097c-126">Bir CodeDOM grafiğinden yürütülebilir bir dosya derlerken, <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4097c-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="4097c-127">Birden çok kod giriş noktası varsa, <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> **CompilerParameters** özelliğinin, kullanılacak giriş noktasını tanımlayan sınıfın adına ayarlanması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4097c-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="4097c-128">Oluşturulan bir çalıştırılabilire hata ayıklama bilgilerini eklemek için, <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4097c-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="4097c-129">Projeniz herhangi bir derlemeye başvuruyorsa, derleme adlarını derleme sırasında kullandığınız <xref:System.Collections.Specialized.StringCollection> **CompilerParameters** <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> özelliği olarak bir öğesi olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4097c-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="4097c-130"><xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> Özelliği **true**olarak ayarlayarak disk yerine belleğe yazılan bir derlemeyi derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4097c-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="4097c-131">Bellekte bir derleme oluşturulduğunda kodunuz, ' <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> <xref:System.CodeDom.Compiler.CompilerResults>nin özelliğinden oluşturulan derleme için bir başvuru elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="4097c-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="4097c-132">Bir derlemeyi diske yazılmışsa, bir <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> **CompilerResults**özelliğinden oluşturulan derlemenin yolunu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4097c-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="4097c-133">Derleme işlemini çağırırken kullanılacak özel bir komut satırı bağımsız değişken dizesi belirtmek için, <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliğindeki dizeyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4097c-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="4097c-134">Derleyici işlemini çağırmak için bir Win32 güvenlik belirteci gerekliyse, <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> özelliğindeki belirteci belirtin.</span><span class="sxs-lookup"><span data-stu-id="4097c-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="4097c-135">Bir Win32 kaynak dosyasını derlenmiş derlemeye bağlamak için, <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> özelliğindeki Win32 kaynak dosyasının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4097c-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="4097c-136">Derlemenin durdurkaydedileceği bir uyarı düzeyi belirtmek için, <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> özelliği derlemenin durdurkaydedileceği uyarı düzeyini temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4097c-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="4097c-137">Ayrıca, <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliği **true**olarak ayarlayarak uyarılarla karşılaşıldığında derlemeyi durdurmak için derleyiciyi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4097c-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="4097c-138">Aşağıdaki kod örneği, <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfından türetilen bir CodeDom sağlayıcısı kullanılarak kaynak dosyayı derlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4097c-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="4097c-139">Başlangıç desteğiyle diller</span><span class="sxs-lookup"><span data-stu-id="4097c-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="4097c-140">.NET Framework, aşağıdaki diller için kod derleyicileri ve kod oluşturucuları sağlar: C#, Visual Basic C++, ve JScript.</span><span class="sxs-lookup"><span data-stu-id="4097c-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="4097c-141">CodeDOM desteği, dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak diğer dillere genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="4097c-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4097c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4097c-142">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="4097c-143">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="4097c-143">Dynamic Source Code Generation and Compilation</span></span>](dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="4097c-144">[CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4097c-144">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
