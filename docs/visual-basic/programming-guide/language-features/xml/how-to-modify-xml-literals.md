---
title: 'Nasıl yapılır: XML değişmez değerleri (Visual Basic) değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 6e11c1ed4cfe4edc1c88dbbff2e9f555b1a028c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974724"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Nasıl yapılır: XML değişmez değerleri (Visual Basic) değiştirme
Visual Basic, XML değişmez değerlerini değiştirme için kullanışlı yöntemler sağlar. Ekleyebilir veya öğeler ve öznitelikler silme ve var olan bir öğe olan yeni bir XML öğesi değiştirebilirsiniz. Bu konu, varolan bir XML değişmez değer değiştirme çeşitli örneklerini sağlamaktadır.  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>Bir XML değişmez değeri değerini değiştirmek için  
  
1.  Bir XML değişmez değeri değerini değiştirmek için XML değişmez ve ayarlanmış bir başvuru elde `Value` özelliğini istediğiniz değer.  
  
     Aşağıdaki kod örneği, tüm değerini güncelleştirir \<fiyat > öğeleri bir XML belgesi.  
  
     [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  `Value` Bir koleksiyondaki ilk XML öğesi özelliği başvurur. Bir koleksiyonda aynı ada sahip birden fazla öğe varsa, ayarı `Value` özelliği yalnızca koleksiyon içindeki ilk öğeyi etkiler.  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>Bir XML değişmez değeri için bir öznitelik eklemek için  
  
1.  XML değişmez değer için bir öznitelik eklemek için ilk XML değişmez değer için bir başvuru alın. Ardından, yeni bir XML özniteliği axis özelliği ekleyerek bir öznitelik ekleyebilirsiniz. Ayrıca, yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XAttribute> nesne değişmez değeri kullanarak XML <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi. Aşağıdaki örnek, her iki seçeneği gösterir.  
  
     [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     XML özniteliği eksen özellikleri hakkında daha fazla bilgi için bkz: [XML özniteliği Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>Bir XML değişmez değeri için bir öğe eklemek için  
  
1.  XML değişmez değer için bir öğe eklemek için ilk XML değişmez değer için bir başvuru alın. Daha sonra yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak öğesinin son alt öğesi olarak <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi. Yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak ilk alt öğe olarak <xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemi.  
  
     Diğer alt öğelerine göre belirli bir konumda yeni bir öğe eklemek için öncelikle bitişik bir alt öğeye bir başvuru alın. Daha sonra yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> kullanarak bitişik alt öğeden önce nesne <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> yöntemi. Ayrıca, yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> kullanarak bitişik alt öğeden sonra nesne <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemi.  
  
     Aşağıdaki örnek, her tekniğin örneklerini gösterir.  
  
     [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Bir öğe veya öznitelik, bir XML değişmez değeri kaldırmak için  
  
1.  Bir öğe veya öznitelik, bir XML değişmez değeri kaldırmak için öğe veya öznitelik ve çağrı başvuru elde `Remove` yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
     [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book></Catalog>  
    ```  
  
     Tüm öğeler veya öznitelikleri bir XML değişmez değeri kaldırmak için XML değişmez değer için bir başvuru almak ve çağrı <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi.  
  
### <a name="to-modify-an-xml-literal"></a>Bir XML değişmez değeri değiştirmek için  
  
1.  Bir XML öğesi adını değiştirmek için ilk öğeye bir başvuru alın. Daha sonra yeni bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> yeni bir ad ve yeni geçirin nesnesi <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XNode.ReplaceWith%2A> varolan yöntemi <xref:System.Xml.Linq.XElement> nesne.  
  
     Değiştirdiğiniz öğe korunmalıdır alt öğeleri varsa, yeni değerini ayarlamak <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği var olan öğe. Bu yeni öğenin değeri var olan öğenin iç XML ayarlayın. Aksi takdirde, yeni bir öğe için değeri ayarlayabilirsiniz `Value` özelliği var olan öğe.  
  
     Aşağıdaki kod örneği, tüm değiştirir \<açıklaması > öğeleri ile bir \<soyut > öğesi. İçeriği \<açıklaması > öğesi yeni korunur \<soyut > öğesi kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği \<açıklaması > <xref:System.Xml.Linq.XElement> nesne.  
  
     [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirdi.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
        <Description>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Description>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <Description>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Nasıl yapılır: Dosya, dize veya Stream XML yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
