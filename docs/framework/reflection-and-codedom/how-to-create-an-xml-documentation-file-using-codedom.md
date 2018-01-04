---
title: "Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma"
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
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88792aeef4e1a18807267334b6c9ef722cb48d24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma
CodeDOM XML belgeleri oluşturan kodu oluşturmak için kullanılabilir. Kod oluşturma ve XML belgeleri çıkışı oluşturur derleyici seçeneği ile oluşturulan kod derleme XML belge açıklamaları içeren CodeDOM grafik oluşturma işlemi içerir.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>XML belgeleri yorumları içeren bir CodeDOM grafik oluşturmak için  
  
1.  Oluşturma bir <xref:System.CodeDom.CodeCompileUnit> örnek uygulama için CodeDOM grafiği içeren.  
  
2.  Kullanım <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> Oluşturucu `docComment` parametre kümesine `true` metin ve XML belgeleri açıklama öğeleri oluşturmak için.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>CodeCompileUnit'ten kodunu oluşturmak için  
  
1.  Kullanım <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> kodu derlenmesi için bir kaynak dosyası oluşturmak için yöntem.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Kodu derlemek ve belge dosyası oluşturmak için  
  
1.  Ekleme **/doc** derleyici seçeneği <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> özelliği bir <xref:System.CodeDom.Compiler.CompilerParameters> nesne ve nesneyi geçirin <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> kodu derlendiğinde XML belge dosyası oluşturma yöntemi.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir CodeDOM grafik ile belge açıklamaları, grafikten bir kod dosyası oluşturur ve dosyayı derler ve ilişkili XML belge dosyası oluşturur.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 Kod örneği aşağıdaki XML belgeleri HelloWorldDoc.xml dosyasında oluşturur.  
  
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
  
-   Bu kod örneği gerektirir `FullTrust` izni Ayarla başarıyla yürütülemedi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ile Kodunuzu Belgeleme](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [XML Belge Açıklamaları](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [XML Belgeleri](/cpp/ide/xml-documentation-visual-cpp)
