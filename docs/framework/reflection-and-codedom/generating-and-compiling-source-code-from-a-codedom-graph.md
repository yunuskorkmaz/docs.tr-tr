---
title: "CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme"
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
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b99dacb5a30cd7b12a5a5dd96bf9fe25b32ab984
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme
<xref:System.CodeDom.Compiler> Ad alanı, CodeDOM nesne grafikleri gelen kaynak kodu oluşturma ve derleme desteklenen derleyicileri ile yönetme için arabirim sağlar. Kod sağlayıcının belirli bir programlama dili CodeDOM grafiğe göre kaynak kodunda üretebilir. Öğesinden türeyen bir sınıf <xref:System.CodeDom.Compiler.CodeDomProvider> yöntemler kodu oluşturma ve dil sağlayıcısı Desteler derleme için genellikle sağlayabilir.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Kaynak kodu oluşturmak için bir CodeDOM kod sağlayıcı kullanma  
 Belirli bir dilde kaynak kodu oluştur oluşturmak için kaynak kod yapısını temsil eden bir CodeDOM grafik gerekir.  
  
 Aşağıdaki örnek gösteren bir örneğini oluşturmak nasıl bir <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Grafik kod oluşturma için genellikle bulunan bir <xref:System.CodeDom.CodeCompileUnit>. Kodunu oluşturmak için bir **CodeCompileUnit** CodeDOM grafiği içeren, çağrı <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kod sağlayıcının yöntemi. Bu yöntem için bir parametreye sahip bir <xref:System.IO.TextWriter> bazen önce oluşturmak için gerekli olacak şekilde kaynak kodunu oluşturmak için kullandığı bir **TextWriter** için yazılabilir. Aşağıdaki örnek oluşturma koddan gösterir bir **CodeCompileUnit** ve oluşturulan kaynak kod HelloWorld.cs adlı bir dosyaya yazma.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>CodeDOM kod sağlayıcı derlemeleri derlemek için kullanma  
 **Derleme çağırma**  
  
 CodeDom sağlayıcısının kullanarak bir derlemeyi derlemek için bir derleyici elinizde bir dilde derlemek için iki kaynak kodu olmalıdır ya da bir CodeDOM graph Kaynak Kodu derlemek için gelen oluşturulabilir.  
  
 CodeDOM grafikten derleme, geçirmek <xref:System.CodeDom.CodeCompileUnit> grafiğe içeren <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> kod sağlayıcının yöntemi. Derleyici özelliğini algılayan bir dilde kaynak kodu dosyası varsa, kaynak koduna içeren dosyanın adını geçirmek <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> CodeDom sağlayıcısının yöntemi. Derleyici özelliğini algılayan bir dilde kaynak kodu içeren bir dize geçebilen <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> CodeDom sağlayıcısının yöntemi.  
  
 **Derleme parametrelerini yapılandırma**  
  
 Tüm standart derleme çağırma yöntemleri CodeDom sağlayıcısının türü bir parametreye sahip <xref:System.CodeDom.Compiler.CompilerParameters> derlemesi için kullanılacak seçeneklerini gösterir.  
  
 Çıkış derlemesi için bir dosya adı belirtebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> özelliği **CompilerParameters**. Aksi takdirde, varsayılan çıktı dosyası adı kullanılır.  
  
 Varsayılan olarak, yeni bir **CompilerParameters** ile başlatılmış kendi <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliğini **false**. Bir yürütülebilir programı derleme, ayarlamalısınız **GenerateExecutable** özelliğine **doğru**. Zaman **GenerateExecutable** ayarlanır **yanlış**, derleyici bir sınıf kitaplığı oluşturur.  
  
 CodeDOM grafiğinden yürütülebilir bir derleme varsa bir <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanması gerekir. Birden çok kod giriş noktası varsa, ayarlamak gerekli olabilir <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> özelliği **CompilerParameters** kullanmak için giriş noktasını tanımlayan sınıfının adı.  
  
 Oluşturulan bir yürütülebilir dosya içinde hata ayıklama bilgileri içerecek şekilde <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliğine **doğru**.  
  
 Projenizi tüm derlemelerde başvuruyorsa, öğeleri olarak derleme adları belirtmelisiniz bir <xref:System.Collections.Specialized.StringCollection> olarak <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> özelliği **CompilerParameters** derleme çağrılırken kullanın.  
  
 Disk yerine bellek ayarlayarak yazılır bütünleştirilmiş derleyebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> özelliğine **doğru**. Bir derlemeyi bellekte oluşturulduğunda, kodunuzu oluşturulan derlemeden başvuru edinebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerResults>. Bir derlemeyi yazılmış olan disk için oluşturulan derlemeden yolu edinebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> özelliği bir **CompilerResults**.  
  
 Dize derleme işlemi başlatılırken kullanmak için bir özel komut satırı bağımsız değişkenleri dize belirtmek için kümesinde <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği.  
  
 Derleyici işlemi çağırmak için bir Win32 güvenlik belirteci gerekirse, belirteçte belirtin <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> özelliği.  
  
 Derlenmiş derlemeye Win32 kaynak dosyasını bağlamak için Win32 kaynak dosyanın adını belirtin <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> özelliği.  
  
 Derleme durdurmak için uyarı düzeyinde belirtmek için ayarlayın <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> derleme durdurmak için uyarı düzeyinde temsil eden bir tamsayı özelliği. Uyarılar ayarlayarak karşılaşıldıysa derleme durdurmak için derleyici de yapılandırabilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliğine **doğru**.  
  
 Aşağıdaki kod örneğinde, türetilmiş bir CodeDom sağlayıcısı kullanarak bir kaynak dosyası derleme gösterilmektedir <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>İlk desteğiyle dilleri  
 Kod derleyicileri ve kod oluşturucuları aşağıdaki diller için .NET Framework sağlar: C#, Visual Basic, C++ ve JScript. CodeDOM desteğini dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak diğer diller için genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [Dinamik Kaynak Kodu Oluşturma ve Derleme](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [CodeDOM hızlı başvuru](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
