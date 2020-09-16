---
title: CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme
description: .NET 'teki CodeDOM grafiğindeki kaynak kodu oluşturun ve derleyin. Kaynak kodu oluşturmak ve derlemeleri derlemek için CodeDOM Kod sağlayıcısını kullanın.
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
ms.openlocfilehash: 3aad7b2ff047a2d9ad12c23d16773e482a395c10
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551203"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="99bc2-104">CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="99bc2-104">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="99bc2-105"><xref:System.CodeDom.Compiler>Ad alanı, CodeDOM nesne grafiklerinden kaynak kodu oluşturmak ve desteklenen derleyicilerle derlemeyi yönetmek için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bc2-105">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="99bc2-106">Bir kod sağlayıcısı, CodeDOM grafiğine göre belirli bir programlama dilinde kaynak kodu üretebilir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-106">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="99bc2-107">Öğesinden türetilen bir sınıf <xref:System.CodeDom.Compiler.CodeDomProvider> genellikle sağlayıcının desteklediği dil için kod oluşturmak ve derlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="99bc2-107">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="99bc2-108">Kaynak kodu oluşturmak için CodeDOM kod sağlayıcısı kullanma</span><span class="sxs-lookup"><span data-stu-id="99bc2-108">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="99bc2-109">Belirli bir dilde kaynak kodu oluşturmak için, oluşturulacak kaynak kodun yapısını temsil eden bir CodeDOM grafiğine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="99bc2-109">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="99bc2-110">Aşağıdaki örnek, bir örneğinin nasıl oluşturulacağını göstermektedir <xref:Microsoft.CSharp.CSharpCodeProvider> :</span><span class="sxs-lookup"><span data-stu-id="99bc2-110">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="99bc2-111">Kod oluşturma için grafik genellikle bir içinde bulunur <xref:System.CodeDom.CodeCompileUnit> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-111">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="99bc2-112">CodeDOM grafiği içeren bir **CodeCompileUnit** için kod oluşturmak üzere <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kod sağlayıcısının yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="99bc2-112">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="99bc2-113">Bu yöntem, <xref:System.IO.TextWriter> kaynak kodu oluşturmak için kullandığı bir parametreye sahiptir, bu nedenle ilk olarak yazılacak bir **TextWriter** oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-113">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="99bc2-114">Aşağıdaki örnek, bir **CodeCompileUnit** öğesinden kod oluşturmayı ve oluşturulan kaynak kodu HelloWorld.cs adlı bir dosyaya yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-114">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="99bc2-115">Derlemeleri derlemek için CodeDOM kod sağlayıcısı kullanma</span><span class="sxs-lookup"><span data-stu-id="99bc2-115">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="99bc2-116">**Derleme çağrılıyor**</span><span class="sxs-lookup"><span data-stu-id="99bc2-116">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="99bc2-117">Bir CodeDom sağlayıcısı kullanarak bir derlemeyi derlemek için, derleyicinizin bulunduğu bir dilde derlemek için kaynak kodunuz veya derlenecek kaynak kodun üretibileceği bir CodeDOM Graf olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-117">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="99bc2-118">Bir CodeDOM grafiğinden derleme yapıyorsanız, <xref:System.CodeDom.CodeCompileUnit> grafiği içeren <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> kodu kod sağlayıcısının yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="99bc2-118">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="99bc2-119">Derleyicinin anladığı bir dilde kaynak kodu dosyanız varsa, kaynak kodu içeren dosyanın adını <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> CodeDom sağlayıcısı yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="99bc2-119">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="99bc2-120">Ayrıca, kaynak kodu içeren bir dizeyi derleyicinin CodeDom sağlayıcısı yöntemine anladığı bir dilde geçirebilirsiniz <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-120">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="99bc2-121">**Derleme parametrelerini yapılandırma**</span><span class="sxs-lookup"><span data-stu-id="99bc2-121">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="99bc2-122">Bir CodeDom sağlayıcısının standart derleme çağırma yöntemlerinin hepsi, <xref:System.CodeDom.Compiler.CompilerParameters> derleme için kullanılacak seçenekleri belirten türünde bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-122">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="99bc2-123"><xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> **CompilerParameters**özelliğinde çıkış derlemesi için bir dosya adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99bc2-123">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="99bc2-124">Aksi takdirde, varsayılan bir çıkış dosyası adı kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="99bc2-124">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="99bc2-125">Varsayılan olarak, yeni bir **CompilerParameters** <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliği **false**olarak ayarlanmış şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="99bc2-125">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="99bc2-126">Yürütülebilir bir program derlerken **GenerateExecutable** özelliğini **true**olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-126">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="99bc2-127">**Generateyürütülebilirdeğeri** **false**olarak ayarlandığında, derleyici bir sınıf kitaplığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99bc2-127">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="99bc2-128">Bir CodeDOM grafiğinden yürütülebilir bir dosya derlerken, <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-128">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="99bc2-129">Birden çok kod giriş noktası varsa, <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> **CompilerParameters** özelliğinin, kullanılacak giriş noktasını tanımlayan sınıfın adına ayarlanması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-129">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="99bc2-130">Oluşturulan bir çalıştırılabilire hata ayıklama bilgilerini eklemek için, <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99bc2-130">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="99bc2-131">Projeniz herhangi bir derlemeye başvuruyorsa, derleme adlarını <xref:System.Collections.Specialized.StringCollection> <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> derleme sırasında kullandığınız **CompilerParameters** özelliği olarak bir öğesi olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-131">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="99bc2-132"><xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A>Özelliği **true**olarak ayarlayarak disk yerine belleğe yazılan bir derlemeyi derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99bc2-132">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="99bc2-133">Bellekte bir derleme oluşturulduğunda kodunuz, ' nin özelliğinden oluşturulan derleme için bir başvuru elde edebilir <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> <xref:System.CodeDom.Compiler.CompilerResults> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-133">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="99bc2-134">Bir derlemeyi diske yazılmışsa, <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> bir **CompilerResults**özelliğinden oluşturulan derlemenin yolunu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99bc2-134">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="99bc2-135">Derleme işlemini çağırırken kullanılacak özel bir komut satırı bağımsız değişken dizesi belirtmek için, özelliğindeki dizeyi ayarlayın <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-135">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="99bc2-136">Derleyici işlemini çağırmak için bir Win32 güvenlik belirteci gerekliyse, özelliğindeki belirteci belirtin <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-136">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="99bc2-137">Bir Win32 kaynak dosyasını derlenmiş derlemeye bağlamak için, özelliğindeki Win32 kaynak dosyasının adını belirtin <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-137">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="99bc2-138">Derlemenin durdurkaydedileceği bir uyarı düzeyi belirtmek için, <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> özelliği derlemenin durdurkaydedileceği uyarı düzeyini temsil eden bir tamsayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="99bc2-138">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="99bc2-139">Ayrıca, <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliği **true**olarak ayarlayarak uyarılarla karşılaşıldığında derlemeyi durdurmak için derleyiciyi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99bc2-139">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="99bc2-140">Aşağıdaki kod örneği, sınıfından türetilen bir CodeDom sağlayıcısı kullanılarak kaynak dosyayı derlemeyi gösterir <xref:System.CodeDom.Compiler.CodeDomProvider> .</span><span class="sxs-lookup"><span data-stu-id="99bc2-140">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="99bc2-141">Başlangıç desteğiyle diller</span><span class="sxs-lookup"><span data-stu-id="99bc2-141">Languages with Initial Support</span></span>  
 <span data-ttu-id="99bc2-142">.NET Framework, aşağıdaki diller için kod derleyicileri ve kod oluşturucuları sağlar: C#, Visual Basic, C++ ve JScript.</span><span class="sxs-lookup"><span data-stu-id="99bc2-142">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="99bc2-143">CodeDOM desteği, dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak diğer dillere genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="99bc2-143">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bc2-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99bc2-144">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="99bc2-145">Dinamik kaynak kodu oluşturma ve derleme</span><span class="sxs-lookup"><span data-stu-id="99bc2-145">Dynamic Source Code Generation and Compilation</span></span>](dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="99bc2-146">[CodeDOM hızlı başvurusu](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="99bc2-146">[CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
