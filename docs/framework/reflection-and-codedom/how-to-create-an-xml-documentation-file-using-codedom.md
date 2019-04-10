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
ms.openlocfilehash: d4088fe35d919cd579ed9f9a6275db8bb88300fe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297531"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma
CodeDOM, XML belgeleri oluşturan kodu oluşturmak için kullanılabilir. Kod oluşturma ve XML belgeleri çıktısı oluşturan derleyici seçeneğiyle oluşturulan kod derleme XML belge açıklamaları içeren CodeDOM grafik oluşturma işlemi içerir.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>XML belge açıklamaları içeren bir CodeDOM grafiği oluşturmak için  
  
1. Oluşturma bir <xref:System.CodeDom.CodeCompileUnit> örnek uygulama için CodeDOM grafiğini içeren.  
  
2. Kullanım <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> oluşturucuyla `docComment` parametresini `true` metin ve XML belgeleri açıklama öğeleri oluşturmak için.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit kodunu oluşturmak için  
  
1. Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kodun derlenmesi için bir kaynak dosyası oluşturmak için yöntemi.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kodu derlemek ve belge dosyası oluşturmak için  
  
1. Ekleme **/doc** derleyici seçeneği <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerParameters> nesne ve nesneyi geçirin <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kodu derlendiğinde XML belge dosyası oluşturmak için yöntemi.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği bir CodeDOM grafiği ile belge açıklamaları, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili XML belge dosyası oluşturur.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Kod örneği, aşağıdaki XML belgeleri HelloWorldDoc.xml dosyası oluşturur.  
  
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
  
-   Bu kod örneği gerektirir `FullTrust` izin kümesinin başarıyla yürütülemedi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Belgeleri Yorumları](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)
- [XML Belgeleri](/cpp/ide/xml-documentation-visual-cpp)
