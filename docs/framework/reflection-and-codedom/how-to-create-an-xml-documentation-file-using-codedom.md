---
title: 'Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: cdd1f173274b6bd33c4a67ed8eb0974c4c8e8e70
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130184"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="7d103-102">Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d103-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="7d103-103">CodeDOM, XML belgeleri üreten kodu oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d103-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="7d103-104">İşlem, XML belge açıklamalarını içeren CodeDOM grafiğinin oluşturulmasını, kodun oluşturulmasını ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="7d103-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="7d103-105">XML belgesi açıklamalarını içeren bir CodeDOM grafiği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7d103-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1. <span data-ttu-id="7d103-106">Örnek uygulama için CodeDOM grafiğini içeren bir <xref:System.CodeDom.CodeCompileUnit> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d103-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="7d103-107">XML belge açıklaması öğelerini ve metnini oluşturmak için `true` olarak ayarlanan `docComment` parametresi ile <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d103-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="7d103-108">CodeCompileUnit öğesinden kod oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7d103-108">To generate the code from the CodeCompileUnit</span></span>  
  
1. <span data-ttu-id="7d103-109">Kodu oluşturmak ve derlenecek kaynak dosya oluşturmak için <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d103-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="7d103-110">Kodu derlemek ve belge dosyasını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7d103-110">To compile the code and generate the documentation file</span></span>  
  
1. <span data-ttu-id="7d103-111">**/Doc** derleyici seçeneğini bir <xref:System.CodeDom.Compiler.CompilerParameters> nesnesinin <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliğine ekleyin ve kodu derlendiğinde XML belge dosyasını oluşturmak için nesneyi <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="7d103-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7d103-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d103-112">Example</span></span>  
 <span data-ttu-id="7d103-113">Aşağıdaki kod örneği, belge açıklamalarını içeren bir CodeDOM grafiği oluşturur, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili bir XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d103-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="7d103-114">Kod örneği, HelloWorldDoc. xml dosyasında aşağıdaki XML belgelerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d103-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
```xml  
<?xml version="1.0" ?>   
<doc>  
  <assembly>  
    <name>HelloWorld</name>   
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.   
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.   
        <para>Add a new paragraph to the description.</para>   
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d103-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7d103-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="7d103-116">Bu kod örneği, `FullTrust` izninin başarıyla yürütülmesi için ayarlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7d103-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d103-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d103-117">See also</span></span>

- [<span data-ttu-id="7d103-118">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="7d103-118">Documenting Your Code with XML</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="7d103-119">XML Belge Açıklamaları</span><span class="sxs-lookup"><span data-stu-id="7d103-119">XML Documentation Comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="7d103-120">XML Belgeleri</span><span class="sxs-lookup"><span data-stu-id="7d103-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
