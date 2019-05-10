---
title: XDocument sınıfına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 135d775a914bc6a440c639628281aa313cb85636
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639182"
---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument sınıfına genel bakış (Visual Basic)
Bu konu tanıtır <xref:System.Xml.Linq.XDocument> sınıfı.  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument sınıfına genel bakış  
 <xref:System.Xml.Linq.XDocument> Sınıfı, geçerli bir XML belgesi için gereken bilgileri içerir. Bu işleme yönergeleri ve açıklamaları, bir XML bildirimi içerir.  
  
 Yalnızca oluşturmak zorunda Not <xref:System.Xml.Linq.XDocument> tarafından sağlanan belirli işlevleri gerektirip gerektirmediğini nesneleri <xref:System.Xml.Linq.XDocument> sınıfı. Çoğu durumda, doğrudan çalışabileceğiniz <xref:System.Xml.Linq.XElement>. Doğrudan çalışma <xref:System.Xml.Linq.XElement> daha basit bir programlama modelidir.  
  
 <xref:System.Xml.Linq.XDocument> öğesinden türetilen <xref:System.Xml.Linq.XContainer>. Bu nedenle, bu alt düğümler içerebilir. Ancak, <xref:System.Xml.Linq.XDocument> nesneler yalnızca bir alt sahip <xref:System.Xml.Linq.XElement> düğümü. Bu, bir XML belgesinde yalnızca bir kök öğe olabileceğini XML standardı yansıtır.  
  
## <a name="components-of-xdocument"></a>XDocument bileşenleri  
 Bir <xref:System.Xml.Linq.XDocument> aşağıdaki öğeleri içerebilir:  
  
- Bir <xref:System.Xml.Linq.XDeclaration> nesne. <xref:System.Xml.Linq.XDeclaration> bir XML bildirimi ilgili bölümleri belirtmenize olanak tanıyan: kodlama belgenin XML sürümü ve XML belge tek başına olup.  
  
- Bir <xref:System.Xml.Linq.XElement> nesne. Bu işlev, XML belgesi kök düğümüdür.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> nesneleri. Bir işlem yönergesi, XML işleme uygulamaya bilgi iletişim kurar.  
  
- Herhangi bir sayıda <xref:System.Xml.Linq.XComment> nesneleri. Açıklamalar, kök öğe kardeş olacaktır. <xref:System.Xml.Linq.XComment> Bir yorum ile başlatmak bir XML belgesi için geçerli olmadığından, nesne ilk bağımsız değişken listesinde olamaz.  
  
- Bir <xref:System.Xml.Linq.XDocumentType> DTD'nin için.  
  
 Serileştirmek ne zaman bir <xref:System.Xml.Linq.XDocument>bile `XDocument.Declaration` olduğu `null`, yazıcı çıkış XML bildirimi varsa `Writer.Settings.OmitXmlDeclaration` kümesine `false` (varsayılan).  
  
 Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ayarlar sürüm "1.0" ve "utf-8" kodlama ayarlar.  
  
## <a name="using-xelement-without-xdocument"></a>XElement XDocument olmadan kullanma  
 Daha önce belirtildiği gibi <xref:System.Xml.Linq.XElement> ana sınıfı içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabirimi. Çoğu durumda, bir belge oluşturmak, uygulamanızın gerek yoktur. Kullanarak <xref:System.Xml.Linq.XElement> sınıfı, bir XML ağacı oluşturma, diğer XML ağaçlarını ekleyin, XML ağacı değiştirebilir ve kaydedebilirsiniz.  
  
## <a name="using-xdocument"></a>XDocument kullanma  
 Oluşturmak için bir <xref:System.Xml.Linq.XDocument>, oluşturmak için yaptığınız gibi işlev yapım kullanın <xref:System.Xml.Linq.XElement> nesneleri.  
  
 Aşağıdaki kod oluşturur bir <xref:System.Xml.Linq.XDocument> nesne ve onun ilişkili kapsanan nesneleri.  
  
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
  
 Dosya test.xml incelediğinizde, aşağıdaki çıkışı alırsınız:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
