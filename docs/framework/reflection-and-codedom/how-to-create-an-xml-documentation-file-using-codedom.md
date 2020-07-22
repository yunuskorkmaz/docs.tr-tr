---
title: 'Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma'
description: Bu ayrıntılı örnekte, bkz. Kod Belge Nesne Modeli (CodeDOM) kullanarak XML belge dosyası oluşturan kod oluşturma.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
ms.openlocfilehash: f905b996910c6cfbc62378cc4cd6bb8c0e0e6fd4
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865157"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="7803b-103">Nasıl yapılır: CodeDOM kullanarak XML belge dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="7803b-103">How to: Create an XML documentation file using CodeDOM</span></span>

<span data-ttu-id="7803b-104">CodeDOM, XML belgeleri üreten kodu oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7803b-104">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="7803b-105">İşlem, XML belge açıklamalarını içeren CodeDOM grafiğinin oluşturulmasını, kodun oluşturulmasını ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="7803b-105">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
## <a name="create-a-codedom-graph"></a><span data-ttu-id="7803b-106">CodeDOM grafiği oluşturma</span><span class="sxs-lookup"><span data-stu-id="7803b-106">Create a CodeDOM graph</span></span>
  
1. <span data-ttu-id="7803b-107"><xref:System.CodeDom.CodeCompileUnit>Örnek uygulama Için CodeDOM grafiğini içeren bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="7803b-107">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2. <span data-ttu-id="7803b-108"><xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> `docComment` `true` XML belge açıklaması öğelerini ve metnini oluşturmak için, öğesini olarak ayarlanan parametresiyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="7803b-108">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="7803b-109">CodeCompileUnit öğesinden kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="7803b-109">Generate the code from the CodeCompileUnit</span></span>
  
1. <span data-ttu-id="7803b-110"><xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>Kodu oluşturmak ve derlenecek kaynak dosya oluşturmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7803b-110">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="7803b-111">Kodu derleyin ve belge dosyasını oluşturun</span><span class="sxs-lookup"><span data-stu-id="7803b-111">Compile the code and generate the documentation file</span></span>
  
1. <span data-ttu-id="7803b-112">Bir nesnenin özelliğine **/doc** derleyici seçeneğini ekleyin <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> <xref:System.CodeDom.Compiler.CompilerParameters> ve <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kod derlendiğinde XML belge dosyasını oluşturmak için nesneyi yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="7803b-112">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="7803b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7803b-113">Example</span></span>

<span data-ttu-id="7803b-114">Aşağıdaki kod örneği, belge açıklamalarını içeren bir CodeDOM grafiği oluşturur, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili bir XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7803b-114">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="7803b-115">Kod örneği, *HelloWorldDoc.xml* dosyasında aşağıdaki XML belgelerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7803b-115">The code example creates the following XML documentation in the *HelloWorldDoc.xml* file.</span></span>  
  
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
      </summary>
      <seealso cref="M:Samples.Class1.Main" />
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
  
## <a name="compile-permissions"></a><span data-ttu-id="7803b-116">Derleme izinleri</span><span class="sxs-lookup"><span data-stu-id="7803b-116">Compile permissions</span></span>
  
<span data-ttu-id="7803b-117">Bu kod örneği, `FullTrust` izin kümesinin başarıyla yürütülmesine gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="7803b-117">This code example requires the `FullTrust` permission set to execute successfully.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7803b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7803b-118">See also</span></span>

- [<span data-ttu-id="7803b-119">Kodunuzu XML ile belgeleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7803b-119">Document your code with XML (Visual Basic)</span></span>](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="7803b-120">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="7803b-120">XML documentation comments</span></span>](../../csharp/programming-guide/xmldoc/index.md)
- [<span data-ttu-id="7803b-121">XML belgeleri (C++)</span><span class="sxs-lookup"><span data-stu-id="7803b-121">XML documentation (C++)</span></span>](/cpp/ide/xml-documentation-visual-cpp)
