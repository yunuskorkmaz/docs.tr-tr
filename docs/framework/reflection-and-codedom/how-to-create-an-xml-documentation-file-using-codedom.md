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
CodeDOM, XML belgeleri oluşturan kod oluşturmak için kullanılabilir. İşlem, XML dokümantasyon açıklamalarını içeren CodeDOM grafiğini oluşturmayı, kodu oluşturmayı ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>XML belge leme yorumlarını içeren bir CodeDOM grafiği oluşturmak için  
  
1. Örnek <xref:System.CodeDom.CodeCompileUnit> uygulama için CodeDOM grafiğiiçeren bir grafik oluşturun.  
  
2. XML <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> dokümantasyon `docComment` yorum öğeleri `true` ve metin oluşturmak için parametre kümesi ile oluşturucu kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit'ten kodu oluşturmak için  
  
1. Kodu <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> oluşturmak ve derlenecek bir kaynak dosyası oluşturmak için yöntemi kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kodu derlemek ve dokümantasyon dosyasını oluşturmak için  
  
1. **/doc** derleyici seçeneğini bir <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> <xref:System.CodeDom.Compiler.CompilerParameters> nesnenin özelliğine ekleyin ve <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kod derlendiğinde XML belge dosyasını oluşturmak için nesneyi yönteme geçirin.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, belge açıklamaları içeren bir CodeDOM grafiği oluşturur, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili bir XML belge dosyası oluşturur.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Kod örneği HelloWorldDoc.xml dosyasında aşağıdaki XML belgelerini oluşturur.  
  
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
  
- Bu kod örneği, başarılı bir `FullTrust` şekilde yürütülmesi için izin kümesini gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Dokümantasyon Yorumları](../../csharp/programming-guide/xmldoc/index.md)
- [XML Dokümantasyon](/cpp/ide/xml-documentation-visual-cpp)
