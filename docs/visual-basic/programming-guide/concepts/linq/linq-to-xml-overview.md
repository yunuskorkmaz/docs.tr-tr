---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368745"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ to XML genel bakış (Visual Basic)
XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir. Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır. Belge Nesne Modeli (DOM) bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler. Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML geliştiriciler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]çeşitli geliştiricileri hedefler. Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] SQL 'e benzer bir sorgu deneyimi sağlayarak xml 'i daha kolay hale getirir. Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.  
  
 Profesyonel geliştiriciler, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliğini önemli ölçüde artırmak için kullanabilir. İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir. Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.  
  
## <a name="what-is-linq-to-xml"></a>LINQ to XML nedir?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], .NET Framework programlama dilleri içinden XML ile çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir. Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Dom 'dan farklıdır: daha açık ağırlığı olan yeni bir nesne modeli sağlar ve ile çalışmak daha kolay ve Visual Basic dil özelliklerinden faydalanır.  
  
 Uygulamasının en önemli avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dil Ile tümleşik sorgu (LINQ) ile tümleştirmedir. Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar. Öğesinin sorgu özelliği, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath ve XQuery için işlevsellik (sözdiziminde değil) ile karşılaştırılabilir. Visual Basic LINQ 'ın tümleştirilmesi, daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.  
  
 ' In başka bir avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçlarının parametre olarak kullanılması <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları, xml ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar. *İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.  
  
 Örneğin, örnek XML dosyasında açıklandığı gibi tipik bir XML satın alma siparişiniz olabilir [: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md). Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:  
  
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
  
 Bu LINQ özelliklerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş BIR XML programlama arabirimi sağlar. Kullanarak şunları [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapabilirsiniz:  
  
- Dosyalardan veya akışlardan XML yükleyin.  
  
- XML 'yi dosyalara veya akışlara seri hale getirme.  
  
- İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.  
  
- XPath benzeri eksenleri kullanarak XML 'yi sorgula.  
  
- ,, Ve gibi yöntemleri kullanarak bellek içi xml ağacını işleme <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> <xref:System.Xml.Linq.XElement.SetValue%2A> .  
  
- XSD kullanarak XML ağaçlarını doğrulayın.  
  
- XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.  
  
## <a name="creating-xml-trees"></a>XML Ağaçları Oluşturma  
 Programlama kullanmanın en önemli avantajlarından biri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , xml ağaçları oluşturmak kolaydır. Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:  
  
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
  
 Visual Basic Derleyicisi, XML değişmez değerlerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntem çağrılarına çevirir.  
  
 Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](creating-xml-trees.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq>
- [Başlarken (LINQ to XML)](getting-started-linq-to-xml.md)
- [Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış](../../language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../language-features/xml/index.md)
