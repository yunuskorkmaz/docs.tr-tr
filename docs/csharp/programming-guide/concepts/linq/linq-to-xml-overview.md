---
title: "LINQ-XML genel bakış (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c66e87ecc72bf711dfda33cd7c0ea35f126c1e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-xml-overview-c"></a>LINQ-XML genel bakış (C#)
XML yaygın olarak birçok bağlamlarında biçim verileri için bir yol olarak benimsemiştir. Örneğin, Web, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanları XML bulabilirsiniz.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir güncel, yeniden tasarlanan XML ile programlamaya yaklaşımdır. Bellek içi belge değişikliği özellikleri belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri. Bu sorgu ifadeleri XPath sözdizimsel olarak farklı olsa da, bunlar benzer bir işlevsellik sağlar.  
  
## <a name="linq-to-xml-developers"></a>LINQ-XML geliştiriciler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Geliştiriciler, çeşitli hedefler. Bir şey yapmanız, almak istediği bir ortalama geliştiriciye [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL benzer bir sorgu deneyimi sağlayarak kolaylaştırır. Yalnızca bir bit öğrenim, kendi seçtikleri programlama dilinde kısa ve güçlü sorgular yazmak programcıları öğrenebilirsiniz.  
  
 Profesyonel geliştiricilere kullanabileceğiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için. İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], daha açıklayıcı, daha küçük ve daha güçlü daha az kod yazabilirsiniz. Aynı anda birden çok veri etki alanından karşı sorgu ifadeleri kullanabilir.  
  
## <a name="what-is-linq-to-xml"></a>LINQ-XML nedir?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML ile içinden çalışmanıza olanak sağlayan bir LINQ etkin, bellek içi XML programlama arabirimidir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama dilleri.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML belgesi belleğe getirir belge nesne modeli (DOM) gibi olmamasıdır. Sorgulamak ve belgeyi değiştirmek, ve değiştirdikten sonra bir dosyaya kaydedin veya bu seri hale getirmek ve Internet üzerinden göndermek. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı yeni bir nesne modeli sağlar ve birlikte çalışmak daha kolay ve, dil özellikleri C# ' ta yararlanır.  
  
 En önemli avantajlarından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olduğu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Bu tümleştirme öğeleri ve özniteliklerinin koleksiyonlarını almak için bellek içi XML belgesi sorguları yazmanızı sağlar. Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery. Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] C# ' ta daha güçlü yazarak, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.  
  
 Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanmak için özelliği <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturmak için güçlü bir yaklaşım sağlar. Adlandırılan bu yaklaşım *işlevsel yapım*, başka bir XML ağaçları bir şeklin kolayca dönüştürmek için geliştiricilere olanak sağlar.  
  
 Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satınalma siparişi (LINQ-XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğesinde bölümü numara özniteliği değeri elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 Başka bir örnek olarak, bölümü sayısı $100'den büyük bir değere sahip öğeleri sıralı liste, isteyebilirsiniz. Bu bilgiler edinmek için aşağıdaki sorguyu çalıştırabilirsiniz:  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
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
 En önemli avantajlarından biri ile programlama [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturmanın kolay olmasıdır. Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:  
  
```csharp  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 Daha fazla bilgi için bkz: [XML ağaçları (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq>  
 [Başlarken (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
