---
title: XDocument sınıfına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 98ab095d67add2375eaf912ade71114c022b2ebb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument sınıfına genel bakış (Visual Basic)
Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfı genel bakış  
 <xref:System.Xml.Linq.XDocument> Sınıfı için geçerli bir XML belgesi gerekli bilgileri içerir. Bu işlem yönergeleri ve açıklamaları bir XML bildirimi içerir.  
  
 Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı. Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>. Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument> türetilen <xref:System.Xml.Linq.XContainer>. Bu nedenle, alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneleri, yalnızca bir alt olabilir <xref:System.Xml.Linq.XElement> düğümü. Bu bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standart yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:  
  
-   Bir <xref:System.Xml.Linq.XDeclaration> nesnesi. <xref:System.Xml.Linq.XDeclaration> bir XML bildirimi ilgili bölümleri belirtmenize olanak sağlar: belgenin kodlama XML sürümü ve XML belgesi tek başına olup.  
  
-   Bir <xref:System.Xml.Linq.XElement> nesnesi. XML belgesinin kök düğümü budur.  
  
-   Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri. Bir işleme yönergesi XML işleyen bir uygulama için bilgi iletişim kurar.  
  
-   Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri. Açıklamaları kök öğesi için eşdüzey olacaktır. <xref:System.Xml.Linq.XComment> Birlikte bir açıklama başlatmak bir XML belgesi için geçerli değil çünkü nesne listesinde, ilk bağımsız değişken olamaz.  
  
-   Bir <xref:System.Xml.Linq.XDocumentType> DTD için.  
  
 Ne zaman, seri bir <xref:System.Xml.Linq.XDocument>olsa bile `XDocument.Declaration` olan `null`, yazıcı varsa çıktı XML bildirimi olacaktır `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sürüm "1.0" olarak ayarlar ve "utf-8" kodlama ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XElement XDocument olmadan kullanma  
 Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> sınıfı, ana sınıfında [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi. Çoğu durumda, bir belge oluşturun, uygulamanızın gerektirmez. Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturmak, diğer XML ağaçları ekleyin, XML ağacını değiştirmek ve dosyayı kaydedin.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanmak <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onunla ilişkili bulunan nesneleri.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Dosya test.xml incelediğinizde, aşağıdaki çıkış alın:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
