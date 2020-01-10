---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: a30340e06a3f8eac9fe2b7718b14ba20363d682f
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636477"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ to XML genel bakış (Visual Basic)
XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir. Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır. Belge Nesne Modeli (DOM) bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler. Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML geliştiriciler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] çeşitli geliştiricilere hedefler. Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, SQL 'e benzer bir sorgu deneyimi sağlayarak XML 'i daha kolay hale getirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.  
  
 Profesyonel geliştiriciler, üretkenliğini önemli ölçüde artırmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]sayesinde, daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir. Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.  
  
## <a name="what-is-linq-to-xml"></a>LINQ to XML nedir?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML ile .NET Framework programlama dillerinin içinden çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir. Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM 'dan farklıdır: Bu, daha hafif ve daha kolay bir şekilde çalışacak ve Visual Basic dil özelliklerinden faydalanan yeni bir nesne modeli sağlar.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] en önemli avantajı, dil ile tümleşik sorgu (LINQ) ile tümleştirmedir. Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu özelliği, XPath ve XQuery için (sözdiziminde olmasa da) işlev olarak karşılaştırılabilir. Visual Basic LINQ 'ın tümleştirilmesi, daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] başka bir avantajı, sorgu sonuçlarının <xref:System.Xml.Linq.XElement> parametre olarak kullanılması ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları, XML ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar. *İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.  
  
 Örneğin, örnek XML dosyasında açıklandığı gibi tipik bir XML satın alma siparişiniz olabilir [: tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md). [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak, satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Başka bir örnek olarak, $100 'den büyük bir değere sahip olan öğelerin bölüm numarasına göre sıralanmış bir liste olmasını isteyebilirsiniz. Bu bilgileri almak için aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Bu LINQ özelliklerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]kullanarak şunları yapabilirsiniz:  
  
- Dosyalardan veya akışlardan XML yükleyin.  
  
- XML 'yi dosyalara veya akışlara seri hale getirme.  
  
- İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.  
  
- XPath benzeri eksenleri kullanarak XML 'yi sorgula.  
  
- <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>ve <xref:System.Xml.Linq.XElement.SetValue%2A>gibi yöntemleri kullanarak bellek içi XML ağacını işleme.  
  
- XSD kullanarak XML ağaçlarını doğrulayın.  
  
- XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.  
  
## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlamanın en önemli avantajlarından biri, XML ağaçları oluşturmak kolaydır. Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 Visual Basic Derleyicisi, XML değişmez değerlerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemi çağrılarına çevirir.  
  
 Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq>
- [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [Visual Basic LINQ to XML genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
