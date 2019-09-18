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
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme
Ad <xref:System.CodeDom.Compiler> alanı, CodeDOM nesne grafiklerinden kaynak kodu oluşturmak ve desteklenen derleyicilerle derlemeyi yönetmek için arabirimler sağlar. Bir kod sağlayıcısı, CodeDOM grafiğine göre belirli bir programlama dilinde kaynak kodu üretebilir. Öğesinden <xref:System.CodeDom.Compiler.CodeDomProvider> türetilen bir sınıf genellikle sağlayıcının desteklediği dil için kod oluşturmak ve derlemek için yöntemler sağlar.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Kaynak kodu oluşturmak için CodeDOM kod sağlayıcısı kullanma  
 Belirli bir dilde kaynak kodu oluşturmak için, oluşturulacak kaynak kodun yapısını temsil eden bir CodeDOM grafiğine ihtiyacınız vardır.  
  
 Aşağıdaki örnek, bir <xref:Microsoft.CSharp.CSharpCodeProvider>örneğinin nasıl oluşturulacağını göstermektedir:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Kod oluşturma için grafik genellikle bir <xref:System.CodeDom.CodeCompileUnit>içinde bulunur. CodeDOM grafiği içeren bir **CodeCompileUnit** için kod oluşturmak üzere kod sağlayıcısının <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemini çağırın. Bu yöntem, kaynak kodu oluşturmak için <xref:System.IO.TextWriter> kullandığı bir parametreye sahiptir, bu nedenle ilk olarak yazılacak bir **TextWriter** oluşturulması gerekir. Aşağıdaki örnek, bir **CodeCompileUnit** öğesinden kod oluşturmayı ve oluşturulan kaynak kodu HelloWorld.cs adlı bir dosyaya yazmayı gösterir.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Derlemeleri derlemek için CodeDOM kod sağlayıcısı kullanma  
 **Derleme çağrılıyor**  
  
 Bir CodeDom sağlayıcısı kullanarak bir derlemeyi derlemek için, derleyicinizin bulunduğu bir dilde derlemek için kaynak kodunuz veya derlenecek kaynak kodun üretibileceği bir CodeDOM Graf olması gerekir.  
  
 Bir CodeDOM grafiğinden derleme yapıyorsanız, grafiği <xref:System.CodeDom.CodeCompileUnit> <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> içeren kodu kod sağlayıcısının yöntemine geçirin. Derleyicinin anladığı bir dilde kaynak kodu dosyanız varsa, kaynak kodu <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> içeren dosyanın adını CodeDom sağlayıcısı yöntemine geçirin. Ayrıca, kaynak kodu içeren bir dizeyi derleyicinin CodeDom sağlayıcısı <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> yöntemine anladığı bir dilde geçirebilirsiniz.  
  
 **Derleme parametrelerini yapılandırma**  
  
 Bir CodeDOM sağlayıcısının standart derleme çağırma yöntemlerinin hepsi, derleme için kullanılacak seçenekleri belirten türünde <xref:System.CodeDom.Compiler.CompilerParameters> bir parametreye sahiptir.  
  
 <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> **CompilerParameters**özelliğinde çıkış derlemesi için bir dosya adı belirtebilirsiniz. Aksi takdirde, varsayılan bir çıkış dosyası adı kullanılacaktır.  
  
 Varsayılan olarak, yeni bir **CompilerParameters** <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliği **false**olarak ayarlanmış şekilde başlatılır. Yürütülebilir bir program derlerken **GenerateExecutable** özelliğini **true**olarak ayarlamanız gerekir. **Generateyürütülebilirdeğeri** **false**olarak ayarlandığında, derleyici bir sınıf kitaplığı oluşturur.  
  
 Bir CodeDOM grafiğinden yürütülebilir bir dosya derlerken, <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanmış olması gerekir. Birden çok kod giriş noktası varsa, <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> **CompilerParameters** özelliğinin, kullanılacak giriş noktasını tanımlayan sınıfın adına ayarlanması gerekebilir.  
  
 Oluşturulan bir çalıştırılabilire hata ayıklama bilgilerini eklemek için, <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliği **true**olarak ayarlayın.  
  
 Projeniz herhangi bir derlemeye başvuruyorsa, derleme adlarını derleme sırasında kullandığınız <xref:System.Collections.Specialized.StringCollection> **CompilerParameters** <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> özelliği olarak bir öğesi olarak belirtmeniz gerekir.  
  
 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> Özelliği **true**olarak ayarlayarak disk yerine belleğe yazılan bir derlemeyi derleyebilirsiniz. Bellekte bir derleme oluşturulduğunda kodunuz, ' <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> <xref:System.CodeDom.Compiler.CompilerResults>nin özelliğinden oluşturulan derleme için bir başvuru elde edebilir. Bir derlemeyi diske yazılmışsa, bir <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> **CompilerResults**özelliğinden oluşturulan derlemenin yolunu alabilirsiniz.  
  
 Derleme işlemini çağırırken kullanılacak özel bir komut satırı bağımsız değişken dizesi belirtmek için, <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliğindeki dizeyi ayarlayın.  
  
 Derleyici işlemini çağırmak için bir Win32 güvenlik belirteci gerekliyse, <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> özelliğindeki belirteci belirtin.  
  
 Bir Win32 kaynak dosyasını derlenmiş derlemeye bağlamak için, <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> özelliğindeki Win32 kaynak dosyasının adını belirtin.  
  
 Derlemenin durdurkaydedileceği bir uyarı düzeyi belirtmek için, <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> özelliği derlemenin durdurkaydedileceği uyarı düzeyini temsil eden bir tamsayı olarak ayarlayın. Ayrıca, <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliği **true**olarak ayarlayarak uyarılarla karşılaşıldığında derlemeyi durdurmak için derleyiciyi yapılandırabilirsiniz.  
  
 Aşağıdaki kod örneği, <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfından türetilen bir CodeDom sağlayıcısı kullanılarak kaynak dosyayı derlemeyi gösterir.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>Başlangıç desteğiyle diller  
 .NET Framework, aşağıdaki diller için kod derleyicileri ve kod oluşturucuları sağlar: C#, Visual Basic C++, ve JScript. CodeDOM desteği, dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak diğer dillere genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [Dinamik Kaynak Kodu Oluşturma ve Derleme](dynamic-source-code-generation-and-compilation.md)
- [CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))
