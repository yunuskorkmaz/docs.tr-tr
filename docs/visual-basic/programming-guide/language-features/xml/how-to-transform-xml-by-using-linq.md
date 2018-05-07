---
title: "Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 94ad5180c7921a5ace09f9161de5f275475e46d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)
[XML değişmez değerleri](../../../../visual-basic/language-reference/xml-literals/index.md) XML bir kaynaktan okunan ve yeni bir XML biçimine dönüştürmek kolaylaştırır. LINQ sorgularını dönüştürmek için içerik almak için yararlanmak veya var olan bir belgeyi içeriği yeni bir XML biçimine değiştirin.  
  
 Bu konudaki örnek bir tarayıcıda görüntülenecek HTML içeriği bir XML kaynağını belgeden dönüştürür.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>Bir XML belgesi dönüştürmek için  
  
1.  Visual Studio'da yeni bir Visual Basic projesinde oluşturma **konsol uygulaması** proje şablonu.  
  
2.  Visual Basic kodu değiştirmek için projede oluşturulan Module1.vb dosyasını çift tıklatın. Aşağıdaki kodu ekleyin `Sub Main` , `Module1` modülü. Bu kod, kaynak XML belgesi olarak oluşturur. bir <xref:System.Xml.Linq.XDocument> nesnesi.  
  
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
  
     [Nasıl yapılır: dosya, dize veya akıştan XML yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Kaynak XML belgesi oluşturmak için kodu sonra tüm almak için aşağıdaki kodu ekleyin \<defteri > nesnesinden öğeleri ve bir HTML belgesine dönüştürmek. Listesini \<defteri > öğeleri koleksiyonu döndüren bir LINQ Sorgu kullanarak oluşturulur <xref:System.Xml.Linq.XElement> dönüştürülmüş HTML içeren nesne. Yeni XML biçiminde kaynak belgedeki değerlerinin yerleştirileceği katıştırılmış ifadeler kullanabilirsiniz.  
  
     Sonuçta elde edilen HTML belgesi kullanarak bir dosyaya yazılır <xref:System.Xml.Linq.XElement.Save%2A> yöntemi.  
  
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
  
4.  Sonra `Sub Main` , `Module1`, yeni bir yöntem ekleyin (`Sub`) dönüştürmek için bir \<açıklama > belirtilen HTML biçiminde düğümüne. Bu yöntem önceki adımda kodu tarafından çağrılır ve biçimini korumak için kullanılan \<açıklama > öğeleri.  
  
     Bu yöntem, alt öğeleri değiştirir \<açıklama > olan HTML öğesi. `ReplaceWith` Yöntemi alt öğeleri konumunu korumak için kullanılır. Dönüştürülmüş içeriği \<açıklama > öğesi bir HTML paragrafta dahil (\<p >) öğesi. <xref:System.Xml.Linq.XContainer.Nodes%2A> Dönüştürülmüş içeriğini almak için kullanılan özellik \<açıklama > öğesi. Bu, alt öğeleri dönüştürülmüş içeriği içerdiği sağlar.  
  
     Sonra aşağıdaki kodu ekleyin `Sub Main` , `Module1`.  
  
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
  
5.  Değişikliklerinizi kaydedin.  
  
6.  Kodu çalıştırmak için F5 tuşuna basın. Belge kaydedilmiş elde edilen şuna benzer:  
  
    ```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'te XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic'de LINQ'e giriş](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
