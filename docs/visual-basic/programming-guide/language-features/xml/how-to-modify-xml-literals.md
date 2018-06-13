---
title: 'Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 17da86d6d10fb1602c16fc2a8c4d6f9f8acf8ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656051"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)
Visual Basic XML değişmez değerleri değiştirmek için kullanışlı yöntemler sağlar. Ekleme veya öğeleri ve özniteliklerinin silme ve varolan öğeyi yeni bir XML öğesi ile değiştirebilirsiniz. Bu konu, mevcut XML değişmez değer değiştirmek çeşitli örnekleri sağlar.  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>XML değişmez değeri değerini değiştirmek için  
  
1.  XML değişmez değeri değerini değiştirmek için XML değişmez değer ve ayarlanan bir başvuru elde `Value` istenen değeri özelliğine.  
  
     Aşağıdaki kod örneğinde tüm değerini güncelleştirmeleri \<fiyat > öğelerini bir XML belgesi.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.  
  
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
    >  `Value` Özelliği bir koleksiyon ilk XML öğe anlamına gelmektedir. Bir koleksiyondaki aynı ada sahip birden fazla öğe varsa, ayarı `Value` özelliği yalnızca ilk öğe koleksiyonda etkiler.  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>Öznitelik bir XML değişmez değeri eklemek için  
  
1.  Öznitelik bir XML değişmez değer eklemek için önce değişmez değer XML başvurusu edinin. Ardından, yeni bir XML özniteliği axis özelliği ekleyerek bir öznitelik ekleyebilirsiniz. Ayrıca, yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XAttribute> kullanarak değişmez değer XML nesnesine <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi. Aşağıdaki örnek, her iki seçenek gösterir.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.  
  
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
  
     XML özniteliği axis özellikleri hakkında daha fazla bilgi için bkz: [XML özniteliği Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>Bir XML değişmez değeri için bir öğe eklemek için  
  
1.  XML değişmez değer için bir öğe eklemek için önce değişmez değer XML başvurusu edinin. Daha sonra yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak öğesinin son alt öğesi olarak <xref:System.Xml.Linq.XContainer.Add%2A> yöntemi. Yeni bir ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak ilk alt öğesi olarak <xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemi.  
  
     Diğer alt öğeleri göre belirli bir konumda yeni bir öğe eklemek için öncelikle bitişik bir alt öğe başvurusu edinin. Daha sonra yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak bitişik alt öğe önce <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> yöntemi. Ayrıca, yeni ekleyebilirsiniz <xref:System.Xml.Linq.XElement> nesnesi kullanarak bitişik alt öğe sonra <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemi.  
  
     Aşağıdaki örnekte, her tekniğin örnekler gösterir.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Öğe veya öznitelik bir XML değişmez değeri kaldırmak için  
  
1.  Bir öğe veya öznitelik bir XML değişmez değeri kaldırmak için öğe veya öznitelik ve çağrı başvuru elde `Remove` aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.  
  
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
  
     Tüm öğeleri ve öznitelikleri bir XML değişmez değeri kaldırmak için değişmez değer XML başvurusu edinin ve çağrı <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi.  
  
### <a name="to-modify-an-xml-literal"></a>XML değişmez değeri değiştirmek için  
  
1.  Bir XML öğesi adını değiştirmek için ilk öğe başvurusu edinin. Daha sonra yeni bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> , yeni bir ad ve yeni geçirin sahip bir nesne <xref:System.Xml.Linq.XElement> nesnesini <xref:System.Xml.Linq.XNode.ReplaceWith%2A> var olan yöntemi <xref:System.Xml.Linq.XElement> nesnesi.  
  
     Değiştirdiğiniz öğenin korunmalıdır alt öğeleri varsa, yeni değerini <xref:System.Xml.Linq.XElement> nesnesine <xref:System.Xml.Linq.XContainer.Nodes%2A> varolan öğesi özelliği. Bu yeni öğenin değerini var olan öğenin iç XML'e ayarlayın. Aksi takdirde, yeni öğe değerini ayarlayabilir `Value` varolan öğesi özelliği.  
  
     Aşağıdaki kod örneğinde tüm değiştirir \<açıklama > öğelerle bir \<soyut > öğesi. İçeriği \<açıklama > öğesi yeni korunur \<soyut > öğesi kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği \<açıklama > <xref:System.Xml.Linq.XElement> nesnesi.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     Aşağıdaki örnek kaynak XML gösterir ve bu kod örneğindeki XML değiştirilebilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'te XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
