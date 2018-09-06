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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864179"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a>CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme
<xref:System.CodeDom.Compiler> Ad alanı, kaynak kodundan CodeDOM nesne grafikler oluşturma ve derleme desteklenen derleyicileri ile yönetmek için arabirim sağlar. CodeDOM grafiği göre belirli bir programlama dili için kaynak kodunda bir kod sağlayıcısı üretebilir. Türetilen bir sınıf <xref:System.CodeDom.Compiler.CodeDomProvider> oluşturma ve dil sağlayıcısı destekler, kod derleme için yöntemler genellikle sağlayabilir.  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a>Kaynak kodu oluşturmak için bir CodeDOM kod sağlayıcısını kullanma  
 Belirli bir dilde kaynak kodu oluşturmak için oluşturulacak kaynak kodunun yapısını temsil eden CodeDOM grafiği gerekir.  
  
 Aşağıdaki örnek bir örneğini oluşturma işlemini gösteren bir <xref:Microsoft.CSharp.CSharpCodeProvider>:  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 Kod oluşturma için graf tipik olarak bulunan bir <xref:System.CodeDom.CodeCompileUnit>. Kodunu oluşturmak için bir **CodeCompileUnit** bir CodeDOM grafiği içeren, çağrı <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kod sağlayıcının yöntemi. Bu yöntem için bir parametre olan bir <xref:System.IO.TextWriter> bazen ilk oluşturmak için gerekli olacak şekilde kaynak kodunu oluşturmak için kullandığı bir **TextWriter** için yazılabilir. Aşağıdaki örnek oluşturma koddan gösterir bir **CodeCompileUnit** ve HelloWorld.cs olarak adlı bir dosyaya oluşturulan kaynak kod yazma.  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a>Derlemeleri derlemek için bir CodeDOM kod sağlayıcısını kullanma  
 **Derleme çağırma**  
  
 CodeDom sağlayıcısı'nı kullanarak bir derleme olarak derlemek için olan bir derleyici bir dili derlemek için ya da kaynak kodu olmalıdır veya bir CodeDOM grafiğini, Kaynak Kodu derlemek için gelen oluşturulabilir.  
  
 Bir CodeDOM grafiği derleme yapıyorsanız geçirmek <xref:System.CodeDom.CodeCompileUnit> grafiğe içeren <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> kod sağlayıcının yöntemi. Bir derleyici anlayan bir dilde kaynak kodu dosyası varsa, kaynak kodu içeren dosyanın adını geçirin <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> CodeDom sağlayıcısının yöntemi. Derleyici için anlayan bir dilde kaynak kodu içeren bir dize geçebilen <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> CodeDom sağlayıcısının yöntemi.  
  
 **Derleme parametreleri yapılandırma**  
  
 Tüm standart derleme çağırma yöntemleri bir CodeDom sağlayıcısının türü bir parametreye sahip <xref:System.CodeDom.Compiler.CompilerParameters> derleme için kullanılacak seçeneklerini gösterir.  
  
 İçinde çıkış derlemesi için bir dosya adı belirtebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> özelliği **CompilerParameters**. Aksi takdirde varsayılan çıkış dosyası adı kullanılır.  
  
 Varsayılan olarak, yeni bir **CompilerParameters** ile başlatılır, <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> özelliğini **false**. Yürütülebilir program derleme yapıyorsanız ayarlamalısınız **GenerateExecutable** özelliğini **true**. Zaman **GenerateExecutable** ayarlanır **false**, derleyici bir sınıf kitaplığı oluşturur.  
  
 CodeDOM grafiğinden, yürütülebilir bir dosya derleme yapıyorsanız bir <xref:System.CodeDom.CodeEntryPointMethod> grafikte tanımlanması gerekir. Birden çok kod girişi noktası varsa, ayarlamak gerekli olabilir <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> özelliği **CompilerParameters** kullanmak için giriş noktasını tanımlayan sınıfının adı.  
  
 Oluşturulan yürütülebilir dosya içinde hata ayıklama bilgilerini dahil etmek için ayarlama <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> özelliğini **true**.  
  
 Projenizi tüm derlemelere başvuru yapıyorsa, öğeleri olarak derleme adları belirtmelisiniz bir <xref:System.Collections.Specialized.StringCollection> olarak <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> özelliği **CompilerParameters** derleme çağrılırken kullanın.  
  
 Disk yerine bellek ayarlayarak yazılır bütünleştirilmiş derleyebilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> özelliğini **true**. Bir derlemeyi bellekte oluşturulduğunda, kodunuzu oluşturulan bütünleştirilmiş koddan başvuru elde edebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerResults>. Bir derleme için yazılmış olan disk için oluşturulan derlemeden yolu edinebilirsiniz <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> özelliği bir **CompilerResults**.  
  
 Derleme işlemi çağrılırken kullanılacak bir özel komut satırı bağımsız değişkenleri dize belirtmek için dize kümesi'nde <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği.  
  
 Derleyici işlemi çağırmak için bir Win32 güvenlik belirteci gerekiyorsa belirteç belirtin <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> özelliği.  
  
 Derlenmiş derlemeye bir Win32 kaynak dosyası bağlamak için Win32 kaynak dosyası adını belirtin. <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> özelliği.  
  
 Bu derlemeyi durdurmak bir uyarı düzeyinde belirtmek için ayarlayın <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> derlemeyi durdurmak, uyarı düzeyini temsil eden bir tamsayı özelliği. Derleyici uyarılarını ayarlayarak karşılaşılırsa derlemeyi durdurmak için de yapılandırabilirsiniz <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> özelliğini **true**.  
  
 Aşağıdaki kod örneği, türetilen bir CodeDom sağlayıcısı'nı kullanarak bir kaynak dosyası derleniyor gösterir <xref:System.CodeDom.Compiler.CodeDomProvider> sınıfı.  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a>İlk desteğiyle dilleri  
 .NET Framework kod derleyicileri ve aşağıdaki dilleri için kod oluşturucuları sağlar: C#, Visual Basic, C++ ve JScript. CodeDOM desteği, dile özgü kod oluşturucuları ve kod derleyicileri uygulayarak, diğer diller için genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [Dinamik Kaynak Kodu Oluşturma ve Derleme](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [CodeDOM hızlı başvuru](https://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
