---
title: LINQ-XML genel bakış (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4ccc81f1f7b875c7388dc09cc45521c6257c00d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ-XML genel bakış (Visual Basic)
XML yaygın olarak birçok bağlamlarında biçim verileri için bir yol olarak benimsemiştir. Örneğin, Web, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanları XML bulabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir güncel, yeniden tasarlanan XML ile programlamaya yaklaşımdır. Bellek içi belge değişikliği özellikleri belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri. Bu sorgu ifadeleri XPath sözdizimsel olarak farklı olsa da, bunlar benzer bir işlevsellik sağlar.  
  
## <a name="linq-to-xml-developers"></a>LINQ-XML geliştiriciler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Geliştiriciler, çeşitli hedefler. Bir şey yapmanız, almak istediği bir ortalama geliştiriciye [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL benzer bir sorgu deneyimi sağlayarak kolaylaştırır. Yalnızca bir bit öğrenim, kendi seçtikleri programlama dilinde kısa ve güçlü sorgular yazmak programcıları öğrenebilirsiniz.  
  
 Profesyonel geliştiricilere kullanabileceğiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için. İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], daha açıklayıcı, daha küçük ve daha güçlü daha az kod yazabilirsiniz. Aynı anda birden çok veri etki alanından karşı sorgu ifadeleri kullanabilir.  
  
## <a name="what-is-linq-to-xml"></a>LINQ-XML nedir?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ile içinden çalışmanıza olanak sağlayan bir LINQ etkin, bellek içi XML programlama arabirimidir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama dilleri.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML belgesi belleğe getirir belge nesne modeli (DOM) gibi olmamasıdır. Sorgulamak ve belgeyi değiştirmek, ve değiştirdikten sonra bir dosyaya kaydedin veya bu seri hale getirmek ve Internet üzerinden göndermek. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı yeni bir nesne modeli sağlar ve birlikte çalışmak daha kolay ve, Visual Basic Dil özelliğinden yararlanır.  
  
 En önemli avantajlarından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olduğu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Bu tümleştirme öğeleri ve özniteliklerinin koleksiyonlarını almak için bellek içi XML belgesi sorguları yazmanızı sağlar. Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery. Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] daha güçlü yazarak, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı Visual Basic'te sağlar.  
  
 Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanmak için özelliği <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturmak için güçlü bir yaklaşım sağlar. Adlandırılan bu yaklaşım *işlevsel yapım*, başka bir XML ağaçları bir şeklin kolayca dönüştürmek için geliştiricilere olanak sağlar.  
  
 Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satınalma siparişi (LINQ-XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğesinde bölümü numara özniteliği değeri elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Başka bir örnek olarak, bölümü sayısı $100'den büyük bir değere sahip öğeleri sıralı liste, isteyebilirsiniz. Bu bilgiler edinmek için aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özellikleri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar. Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:  
  
-   XML dosyaları veya akışlar yüklenemiyor.  
  
-   XML dosyaları veya akışları serileştirir.  
  
-   XML işlevsel yapım kullanarak sıfırdan oluşturun.  
  
-   Sorgu XPath benzeri eksen kullanılarak XML.  
  
-   Bellek içi XML ağaç yöntemleri kullanarak işlemek <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   XML ağaçları XSD kullanarak doğrulayın.  
  
-   Başka bir şeklin XML ağaçları dönüştürmek için bu özellik bileşimi kullanın.  
  
## <a name="creating-xml-trees"></a>XML ağaçları oluşturma  
 En önemli avantajlarından biri ile programlama IOne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturmanın kolay olmasıdır. Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:  
  
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
  
 XML değişmez değerleri içine Visual Basic derleyici çevirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntem çağrıları.  
  
 Daha fazla bilgi için bkz: [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq>  
 [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [LINQ-XML Visual Basic'de genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
