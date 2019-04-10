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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2871d273e0bbb09ff5bf440ea943cdac3f8e061
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201955"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="824e4-102">Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="824e4-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="824e4-103">CodeDOM, XML belgeleri oluşturan kodu oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="824e4-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="824e4-104">Kod oluşturma ve XML belgeleri çıktısı oluşturan derleyici seçeneğiyle oluşturulan kod derleme XML belge açıklamaları içeren CodeDOM grafik oluşturma işlemi içerir.</span><span class="sxs-lookup"><span data-stu-id="824e4-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="824e4-105">XML belge açıklamaları içeren bir CodeDOM grafiği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="824e4-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1.  <span data-ttu-id="824e4-106">Oluşturma bir <xref:System.CodeDom.CodeCompileUnit> örnek uygulama için CodeDOM grafiğini içeren.</span><span class="sxs-lookup"><span data-stu-id="824e4-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2.  <span data-ttu-id="824e4-107">Kullanım <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> oluşturucuyla `docComment` parametresini `true` metin ve XML belgeleri açıklama öğeleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="824e4-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="824e4-108">CodeCompileUnit kodunu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="824e4-108">To generate the code from the CodeCompileUnit</span></span>  
  
1.  <span data-ttu-id="824e4-109">Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kodun derlenmesi için bir kaynak dosyası oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="824e4-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="824e4-110">Kodu derlemek ve belge dosyası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="824e4-110">To compile the code and generate the documentation file</span></span>  
  
1.  <span data-ttu-id="824e4-111">Ekleme **/doc** derleyici seçeneği <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerParameters> nesne ve nesneyi geçirin <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kodu derlendiğinde XML belge dosyası oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="824e4-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="824e4-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="824e4-112">Example</span></span>  
 <span data-ttu-id="824e4-113">Aşağıdaki kod örneği bir CodeDOM grafiği ile belge açıklamaları, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="824e4-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="824e4-114">Kod örneği, aşağıdaki XML belgeleri HelloWorldDoc.xml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="824e4-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="824e4-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="824e4-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="824e4-116">Bu kod örneği gerektirir `FullTrust` izin kümesinin başarıyla yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="824e4-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="824e4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="824e4-117">See also</span></span>

- [<span data-ttu-id="824e4-118">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="824e4-118">Documenting Your Code with XML</span></span>](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="824e4-119">XML Belgeleri Yorumları</span><span class="sxs-lookup"><span data-stu-id="824e4-119">XML Documentation Comments</span></span>](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [<span data-ttu-id="824e4-120">XML Belgeleri</span><span class="sxs-lookup"><span data-stu-id="824e4-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
