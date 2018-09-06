---
title: LINQ to XML genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 49533050efda4254f186a8c06f5c42bdd9555a23
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870379"
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ to XML genel bakış (Visual Basic)
XML, yaygın olarak birçok bağlamları verileri biçimlendirme bir yolu olarak benimsenmiştir. Örneğin, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanlarının Web XML bulabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] güncel ve yeniden tasarlanan XML ile programlamaya yaklaşımıdır. Bellek içi belge değiştirme özelliklerini belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde. Bu sorgu ifadeleri XPath sözdizimi kurallarına göre farklı olsa da, benzer bir işlevsellik sağlarlar.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML geliştiriciler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştiricilerin çeşitli hedefler. Yalnızca bir şey yapmanız, almak isteyen bir ortalama geliştiricinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL'e benzeyen bir sorgu deneyimi sunarak daha kolay hale getirir. Yalnızca bir bit öğrenim, programcılar kendi seçtiğiniz programlama dilinde birleştiren ve güçlü sorgular yazmak bilgi edinebilirsiniz.  
  
 Profesyonel Geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için. İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bunlar daha ifadesel, daha küçük ve daha güçlü daha az kod yazabilirsiniz. Aynı anda birden çok veri etki alanından bunlar sorgu ifadeleri kullanabilirsiniz.  
  
## <a name="what-is-linq-to-xml"></a>LINQ to XML nedir?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ile içinden çalışmanızı sağlayan bir LINQ-etkin, bellek içi XML programlama arabirimi olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML belgesi belleğe getirdiği belge nesne modeli (DOM) gibi olmamasıdır. Sorgulamak ve belgeyi değiştirmesine ve değiştirdikten sonra bir dosyaya kaydedebilir veya bu seri hale getirmek ve Internet üzerinden gönder. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı olan yeni bir nesne modeli sağlar ve çalışmak, daha kolay ve Visual Basic Dil özelliklerinden alan.  
  
 En önemli avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Bu tümleştirme, öğeleri ve özniteliklerinin koleksiyonu almak için bellek içi XML belgesi sorgular yazmaya olanak tanır. Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery. Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Visual Basic'te daha güçlü yazım, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.  
  
 Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanma olanağı <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturma için güçlü bir yaklaşım sağlar. Adlandırılan bu yaklaşım *işlevsel oluşturma*, geliştiricilerin bir şekilden XML ağaçlarını başka bir kolayca dönüştürüp olanak tanır.  
  
 Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](https://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğe için bölüm numarası özniteliği değeri elde etmek için şu sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Başka bir örnek olarak $100'den büyük bir değer ile öğelerinin parça numarası tarafından sıralanan bir liste isteyebilirsiniz. Bu bilgiler edinmek için şu sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar. Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:  
  
-   XML dosyaları ya da akış'ı yükleyin.  
  
-   XML dosyaları ya da akış serileştirir.  
  
-   XML işlevsel oluşturma kullanarak sıfırdan oluşturun.  
  
-   Sorgu XPath benzeri eksen kullanılarak XML.  
  
-   Bellek içi XML ağacı yöntemleri kullanarak işleme <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   XML ağaçlarını XSD kullanarak doğrulama.  
  
-   Başka bir şekilden XML ağaçlarını dönüştürmek için bu özellikleri bir birleşimini kullanın.  
  
## <a name="creating-xml-trees"></a>XML ağaçları oluşturma  
 En önemli avantajlarından biri ile programlama IOne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturma kolay olmasıdır. Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:  
  
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
  
 Visual Basic derleyici içine XML sabit değerleri çevirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntemi çağırır.  
  
 Daha fazla bilgi için [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq>  
 [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [LINQ to XML Visual Basic'de genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
