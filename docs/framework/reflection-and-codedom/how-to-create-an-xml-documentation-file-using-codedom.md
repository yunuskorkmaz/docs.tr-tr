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
ms.openlocfilehash: a0ccb469a43c3a21a76eaf24fa7ce7b490dd5c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180516"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma
CodeDOM, XML belgeleri üreten kodu oluşturmak için kullanılabilir. İşlem, XML belge açıklamalarını içeren CodeDOM grafiğinin oluşturulmasını, kodun oluşturulmasını ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>XML belgesi açıklamalarını içeren bir CodeDOM grafiği oluşturmak için  
  
1. Örnek uygulama <xref:System.CodeDom.CodeCompileUnit> için CodeDOM grafiğini içeren bir oluştur.  
  
2. XML belge <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> açıklaması öğelerini ve `docComment` metnini oluşturmak için `true` , öğesini olarak ayarlanan parametresiyle birlikte kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit öğesinden kod oluşturmak için  
  
1. Kodu oluşturmak <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> ve derlenecek kaynak dosya oluşturmak için yöntemini kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kodu derlemek ve belge dosyasını oluşturmak için  
  
1. <xref:System.CodeDom.Compiler.CompilerParameters> Bir <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> nesnenin <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliğine **/doc** derleyici seçeneğini ekleyin ve kod derlendiğinde XML belge dosyasını oluşturmak için nesneyi yöntemine geçirin.  
  
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
  
- Bu kod örneği, `FullTrust` izin kümesinin başarıyla yürütülmesine gerek duyar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML belge açıklamaları](../../csharp/programming-guide/xmldoc/index.md)
- [XML belgeleri](/cpp/ide/xml-documentation-visual-cpp)
