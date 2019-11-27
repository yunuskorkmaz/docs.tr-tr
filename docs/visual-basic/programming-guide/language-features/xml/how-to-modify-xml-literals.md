---
title: 'Nasıl yapılır: XML Değişmez Değerlerini Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 99ec35addcb9fc8d886c9151cde87227b5113eb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330854"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerlerini Değiştirme (Visual Basic)

Visual Basic, XML değişmez değerlerini değiştirmek için kullanışlı yollar sağlar. Öğeleri ve öznitelikleri ekleyebilir ya da silebilirsiniz ve ayrıca var olan bir öğeyi yeni bir XML öğesiyle değiştirebilirsiniz. Bu konuda, var olan bir XML sabit değerinin nasıl değiştirileceği hakkında birkaç örnek verilmiştir.

### <a name="to-modify-the-value-of-an-xml-literal"></a>Bir XML sabit değerinin değerini değiştirmek için

1. Bir XML sabit değerinin değerini değiştirmek için, XML değişmez değerine bir başvuru alın ve `Value` özelliğini istenen değere ayarlayın.

    Aşağıdaki kod örneği bir XML belgesindeki tüm \<Price > öğelerinin değerini günceller.

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.

    Kaynak XML:

    ```xml
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
    ```

    Değiştirilen XML:

    ```xml
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
    > `Value` özelliği, bir koleksiyondaki ilk XML öğesine başvurur. Koleksiyonda aynı ada sahip birden fazla öğe varsa, `Value` özelliğinin ayarlanması yalnızca koleksiyondaki ilk öğeyi etkiler.

### <a name="to-add-an-attribute-to-an-xml-literal"></a>Bir XML sabit değerine öznitelik eklemek için

1. Bir XML sabit değerine bir öznitelik eklemek için, önce XML değişmez değerine bir başvuru alın. Daha sonra yeni bir XML özniteliği eksen özelliği ekleyerek bir öznitelik ekleyebilirsiniz. Ayrıca, <xref:System.Xml.Linq.XContainer.Add%2A> metodunu kullanarak XML sabit değerine yeni bir <xref:System.Xml.Linq.XAttribute> nesnesi de ekleyebilirsiniz. Aşağıdaki örnekte her iki seçenek de gösterilmektedir.

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.

    Kaynak XML:

    ```xml
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
    ```

    Değiştirilen XML:

    ```xml
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

    XML özniteliği eksen özellikleri hakkında daha fazla bilgi için bkz. [XML özniteliği eksen özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).

### <a name="to-add-an-element-to-an-xml-literal"></a>Bir XML sabit değerine öğe eklemek için

1. Bir XML sabit değerine öğe eklemek için, önce XML değişmez değerine bir başvuru alın. Daha sonra, <xref:System.Xml.Linq.XContainer.Add%2A> yöntemini kullanarak, öğenin son alt öğesi olarak yeni bir <xref:System.Xml.Linq.XElement> nesnesi ekleyebilirsiniz. <xref:System.Xml.Linq.XContainer.AddFirst%2A> yöntemini kullanarak yeni bir <xref:System.Xml.Linq.XElement> nesnesini ilk alt öğe olarak ekleyebilirsiniz.

    Belirli bir konuma diğer alt öğelere göre yeni bir öğe eklemek için, önce bitişik bir alt öğeye bir başvuru alın. Sonra, <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metodunu kullanarak komşu alt öğeden önce yeni <xref:System.Xml.Linq.XElement> nesnesini ekleyebilirsiniz. Ayrıca, <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> yöntemini kullanarak komşu alt öğeden sonra yeni <xref:System.Xml.Linq.XElement> nesnesini ekleyebilirsiniz.

    Aşağıdaki örnek, bu tekniklerin her birinin örneklerini gösterir.

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.

    Kaynak XML:

    ```xml
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
    ```

    Değiştirilen XML:

    ```xml
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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>Bir XML sabit değerinden öğe veya öznitelik kaldırmak için

1. Bir öğeyi veya özniteliği bir XML sabit değerinden kaldırmak için, aşağıdaki örnekte gösterildiği gibi, öğe veya özniteliğe bir başvuru alın ve `Remove` yöntemini çağırın.

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.

    Kaynak XML:

    ```xml
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
    ```

    Değiştirilen XML:

    ```xml
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

    Bir XML sabit değerinden tüm öğeleri veya öznitelikleri kaldırmak için, XML değişmez değerine bir başvuru alın ve <xref:System.Xml.Linq.XElement.RemoveAll%2A> yöntemi çağırın.

### <a name="to-modify-an-xml-literal"></a>Bir XML sabit değerini değiştirmek için

1. Bir XML öğesinin adını değiştirmek için öncelikle öğesine bir başvuru alın. Daha sonra yeni bir ada sahip yeni bir <xref:System.Xml.Linq.XElement> nesnesi oluşturabilir ve yeni <xref:System.Xml.Linq.XElement> nesnesini varolan <xref:System.Xml.Linq.XElement> nesnesinin <xref:System.Xml.Linq.XNode.ReplaceWith%2A> yöntemine geçirebilirsiniz.

    Değiştirdiğiniz öğenin korunması gereken alt öğeleri varsa, yeni <xref:System.Xml.Linq.XElement> nesnesinin değerini varolan öğenin <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliğine ayarlayın. Bu, yeni öğenin değerini varolan öğenin iç XML değerine ayarlar. Aksi takdirde, yeni öğenin değerini varolan öğesinin `Value` özelliğine ayarlayabilirsiniz.

    Aşağıdaki kod örneği, tüm \<Description > öğelerini \<soyut > öğesi ile değiştirir. \<Description > öğesinin içeriği, yeni \<soyut > öğesinde <xref:System.Xml.Linq.XContainer.Nodes%2A> Description \<> nesnesinin <xref:System.Xml.Linq.XElement> özelliği kullanılarak korunur.

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    Aşağıdaki kod örneğinde örnek kaynak XML ve değiştirilmiş XML gösterilmektedir.

    Kaynak XML:

    ```xml
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
    ```

    Değiştirilen XML:

    ```xml
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

- [Visual Basic XML 'yi düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
