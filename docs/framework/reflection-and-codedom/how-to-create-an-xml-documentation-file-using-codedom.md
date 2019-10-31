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
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma
CodeDOM, XML belgeleri üreten kodu oluşturmak için kullanılabilir. İşlem, XML belge açıklamalarını içeren CodeDOM grafiğinin oluşturulmasını, kodun oluşturulmasını ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>XML belgesi açıklamalarını içeren bir CodeDOM grafiği oluşturmak için  
  
1. Örnek uygulama için CodeDOM grafiğini içeren bir <xref:System.CodeDom.CodeCompileUnit> oluşturun.  
  
2. XML belge açıklaması öğelerini ve metnini oluşturmak için `true` olarak ayarlanan `docComment` parametresi ile <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> oluşturucusunu kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit öğesinden kod oluşturmak için  
  
1. Kodu oluşturmak ve derlenecek kaynak dosya oluşturmak için <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> yöntemini kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kodu derlemek ve belge dosyasını oluşturmak için  
  
1. **/Doc** derleyici seçeneğini bir <xref:System.CodeDom.Compiler.CompilerParameters> nesnesinin <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliğine ekleyin ve kodu derlendiğinde XML belge dosyasını oluşturmak için nesneyi <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> yöntemine geçirin.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, belge açıklamalarını içeren bir CodeDOM grafiği oluşturur, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili bir XML belge dosyası oluşturur.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Kod örneği, HelloWorldDoc. xml dosyasında aşağıdaki XML belgelerini oluşturur.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu kod örneği, `FullTrust` izninin başarıyla yürütülmesi için ayarlanmasını gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Belge Açıklamaları](../../csharp/programming-guide/xmldoc/index.md)
- [XML Belgeleri](/cpp/ide/xml-documentation-visual-cpp)
