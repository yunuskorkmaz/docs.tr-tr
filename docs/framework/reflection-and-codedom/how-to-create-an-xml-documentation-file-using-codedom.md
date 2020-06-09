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
ms.openlocfilehash: b9e11a51048733dbfc42ff9f575e18effc80db07
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596252"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Nasıl yapılır: CodeDOM kullanarak XML belge dosyası oluşturma

CodeDOM, XML belgeleri üreten kodu oluşturmak için kullanılabilir. İşlem, XML belge açıklamalarını içeren CodeDOM grafiğinin oluşturulmasını, kodun oluşturulmasını ve oluşturulan kodu XML belge çıktısını oluşturan derleyici seçeneğiyle derlemeyi içerir.  
  
## <a name="create-a-codedom-graph"></a>CodeDOM grafiği oluşturma
  
1. <xref:System.CodeDom.CodeCompileUnit>Örnek uygulama Için CodeDOM grafiğini içeren bir oluştur.  
  
2. <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> `docComment` `true` XML belge açıklaması öğelerini ve metnini oluşturmak için, öğesini olarak ayarlanan parametresiyle birlikte kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit öğesinden kod oluşturma
  
1. <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A>Kodu oluşturmak ve derlenecek kaynak dosya oluşturmak için yöntemini kullanın.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="compile-the-code-and-generate-the-documentation-file"></a>Kodu derleyin ve belge dosyasını oluşturun
  
1. Bir nesnenin özelliğine **/doc** derleyici seçeneğini ekleyin <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> <xref:System.CodeDom.Compiler.CompilerParameters> ve <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kod derlendiğinde XML belge dosyasını oluşturmak için nesneyi yöntemine geçirin.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Örnek

Aşağıdaki kod örneği, belge açıklamalarını içeren bir CodeDOM grafiği oluşturur, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili bir XML belge dosyası oluşturur.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Kod örneği, *Helloworlddoc. xml* dosyasında aşağıdaki XML belgelerini oluşturur.  
  
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
  
## <a name="compile-permissions"></a>Derleme izinleri
  
Bu kod örneği, `FullTrust` izin kümesinin başarıyla yürütülmesine gerek duyar.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu XML ile belgeleyin (Visual Basic)](../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML belgeleri yorumları](../../csharp/programming-guide/xmldoc/index.md)
- [XML belgeleri (C++)](/cpp/ide/xml-documentation-visual-cpp)
