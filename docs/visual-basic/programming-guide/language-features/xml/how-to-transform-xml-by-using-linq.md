---
title: "Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: a531b189074ac7bdd1c02935368c408ff506a6f1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353642"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)

[XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) , BIR kaynaktan XML okumayı ve bunu yenı bir XML biçimine dönüştürmeyi kolaylaştırır. Dönüştürülecek içeriği almak veya varolan bir belgedeki içeriği yeni bir XML biçimiyle değiştirmek için LINQ sorgularından yararlanabilirsiniz.

Bu konudaki örnek, bir XML kaynak belgesinden içeriği bir tarayıcıda görüntülenmek üzere HTML 'ye dönüştürür.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>Bir XML belgesini dönüştürmek için

1. Visual Studio 'da, **konsol uygulaması** proje şablonunda yeni bir Visual Basic projesi oluşturun.

2. Visual Basic kodunu değiştirmek için projede oluşturulan Module1. vb dosyasını çift tıklatın. Aşağıdaki kodu `Module1` modülünün `Sub Main` ekleyin. Bu kod, kaynak XML belgesini bir <xref:System.Xml.Linq.XDocument> nesnesi olarak oluşturur.

    ```vb
    Dim catalog =
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
              Get the expert insights, practical code samples,
              and best practices you need
              to advance your expertise with <technology>Visual
              Basic .NET</technology>.
              Learn how to create faster, more reliable applications
              based on professional,
              pragmatic guidance by today's top <audience>developers</audience>.
            </Description>
          </Book>
        </Catalog>
    ```

     [Nasıl yapılır: bir dosyadan, dizeden veya AKıŞTAN XML yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).

3. Kaynak XML belgesini oluşturma kodundan sonra, tüm \<kitabı > öğelerini almak ve bunları bir HTML belgesine dönüştürmek için aşağıdaki kodu ekleyin. \<Book > öğelerinin listesi, dönüştürülmüş HTML içeren <xref:System.Xml.Linq.XElement> nesnelerinin bir koleksiyonunu döndüren bir LINQ sorgusu kullanılarak oluşturulur. Kaynak belgeden yeni XML biçiminde değerleri yerleştirmek için katıştırılmış ifadeleri kullanabilirsiniz.

     Elde edilen HTML belgesi <xref:System.Xml.Linq.XElement.Save%2A> yöntemi kullanılarak bir dosyaya yazılır.

    ```vb
    Dim htmlOutput =
      <html>
        <body>
          <%= From book In catalog.<Catalog>.<Book>
              Select <div>
                       <h1><%= book.<Title>.Value %></h1>
                       <h3><%= "By " & book.<Author>.Value %></h3>
                        <h3><%= "Price = " & book.<Price>.Value %></h3>
                        <h2>Description</h2>
                        <%= TransformDescription(book.<Description>(0)) %>
                        <hr/>
                      </div> %>
        </body>
      </html>

    htmlOutput.Save("BookDescription.html")
    ```

4. `Module1``Sub Main` sonra, \<açıklama > düğümünü belirtilen HTML biçimine dönüştürmek için yeni bir Yöntem (`Sub`) ekleyin. Bu yöntem, önceki adımda kod tarafından çağrılır ve \<Description > öğelerinin biçimini korumak için kullanılır.

     Bu yöntem, \<Description > öğesinin alt öğelerini HTML ile değiştirir. `ReplaceWith` yöntemi alt öğelerin konumunu korumak için kullanılır. \<Description > öğesinin dönüştürülmüş içeriği bir HTML paragrafı (\<p >) öğesine dahil edilmiştir. <xref:System.Xml.Linq.XContainer.Nodes%2A> özelliği, \<Description > öğesinin dönüştürülmüş içeriğini almak için kullanılır. Bu, alt öğelerin dönüştürülmüş içeriğe dahil edilmesini sağlar.

     `Module1``Sub Main` sonra aşağıdaki kodu ekleyin.

    ```vb
    Public Function TransformDescription(ByVal desc As XElement) As XElement

      ' Replace <technology> elements with <b>.
      Dim content = (From element In desc...<technology>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)
        Next
      End If

      ' Replace <audience> elements with <i>.
      content = (From element In desc...<audience>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)
        Next
      End If

      ' Return the updated contents of the <Description> element.
      Return <p><%= desc.Nodes %></p>
    End Function
    ```

5. Yaptığınız değişiklikleri kaydedin.

6. Kodu çalıştırmak için F5 tuşuna basın. Sonuç olarak kaydedilen belge aşağıdakine benzeyecektir:

    ```html
    <?xml version="1.0"?>
    <html>
      <body>
        <div>
          <h1>XML Developer's Guide</h1>
          <h3>By Garghentini, Davide</h3>
          <h3>Price = 44.95</h3>
          <h2>Description</h2>
          <p>
            An in-depth look at creating applications
            with <b>XML</b>. For
            <i>beginners</i> or
            <i>advanced</i> developers.
          </p>
          <hr />
        </div>
        <div>
          <h1>Developing Applications with Visual Basic .NET</h1>
          <h3>By Spencer, Phil</h3>
          <h3>Price = 45.95</h3>
          <h2>Description</h2>
          <p>
            Get the expert insights, practical code
            samples, and best practices you need
            to advance your expertise with <b>Visual
            Basic .NET</b>. Learn how to create faster,
            more reliable applications based on
            professional, pragmatic guidance by today's
            top <i>developers</i>.
          </p>
          <hr />
        </div>
      </body>
    </html>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML 'yi düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Visual Basic LINQ 'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
