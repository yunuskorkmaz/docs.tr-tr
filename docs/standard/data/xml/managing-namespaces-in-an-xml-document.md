---
title: XML Belgesinde Ad Alanlarını Yönetme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0ace73d81783852242a52bec006b0ad2edaadd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650199"
---
# <a name="managing-namespaces-in-an-xml-document"></a>XML Belgesinde Ad Alanlarını Yönetme
XML ad alanları XML belgesinde öğe ve öznitelik adları, özel ve önceden tanımlanmış bir URI'leri ile ilişkilendirin. Bu ilişkileri oluşturmak için URI ad alanı ön eklerini tanımlayın ve bu ön ekler öğe ve öznitelik adları XML verisindeki nitelemek için kullanın. Ad alanları, öğe ve öznitelik adı çakışmalarını önlemek ve öğeleri ve öznitelikleri aynı ada sahip işlenmesini ve farklı şekilde doğrulanmış etkinleştirin.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Ad alanlarını bildirme  
 Bir öğe üzerinde bir ad alanı bildirmek için kullanmanız `xmlns:` özniteliği:  
  
 `xmlns:<name>=<"uri">`  
  
 Burada `<name>` ad alanı öneki ve `<"uri">` ad alanını tanımlayan URI. Önek bildirdikten sonra öğeleri ve özniteliklerinin bir XML belgesi sınıflandırmak ve ad alanı URI ile ilişkilendirmek için kullanabilirsiniz. Ad alanı öneki belge kullanılmakta olduğundan uzunluğu kısa olmalıdır.  
  
 Bu örnek iki tanımlar `BOOK` öğeleri. Ön eke göre ilk öğeyi nitelenmiş `mybook`, ve ikinci öğe ön eke göre nitelenmiş `bb`. Her ön eki farklı ad alanı URI ile ilişkilendirilir:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Bir öğenin belirli bir ad alanının bir parçası olduğunu belirtmek için ad alanı öneki ekleyin. Örneğin, bir `Author` öğenin ait olduğu `mybook` ad alanı, bildirilen olarak `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Bildirim kapsamı  
 Bir ad alanı içinde bildirilen öğe sonuna kadar bildirim noktasında etkilidir. Bu örnekte ad alanı tanımlı `BOOK` öğesi öğeler için geçerli değildir `BOOK` öğesi gibi `Publisher` öğesi:  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Bir ad alanı, kullanılabilir, ancak XML belgenin üst kısmında görünmesini yok önce bildirilmelidir.  
  
 Bir XML belgesinde birden çok ad alanını kullandığınızda, bir ad alanı Temizleyicisi görünümlü bir belge oluşturmak için varsayılan ad alanı olarak tanımlayabilirsiniz. Varsayılan ad alanı, kök öğesi bildirilmiş ve belgedeki tüm nitelenmemiş öğeleri için geçerlidir. Varsayılan ad alanlarını öznitelikler için yalnızca öğeler için geçerlidir.  
  
 Varsayılan ad alanı kullanılacak önek ve virgül gelen öğede bildirimi atla:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Ad alanlarını yönetme  
 <xref:System.Xml.XmlNamespaceManager> Sınıf ad alanı URI koleksiyonunu depolar ve bunların ön ekleri ve sağlar, konum ekleyin ve bu koleksiyondan ad alanları. Belirli bağlamlarda bu sınıfı daha iyi XML işlem performansı için gereklidir. Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfının kullandığı <xref:System.Xml.XmlNamespaceManager> XPath desteği.  
  
 Ad alanı Yöneticisi'ni ad alanlarında herhangi doğrulaması gerçekleştirmez, ancak önek ve ad alanları zaten doğrulandı ve uygun varsayar [W3C ad alanları](https://www.w3.org/TR/REC-xml-names/) belirtimi.  
  
> [!NOTE]
> [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) kullanmayın <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için. Bkz: [XML ad alanları ile çalışma (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) ve [(Visual Basic) XML ad alanları ile çalışma](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) LINQ to XML kullanarak ad alanlarını yönetme hakkında bilgi için LINQ belgelerinde.  
  
 Bazı görevlerin ile gerçekleştirebileceğiniz yönetim ve arama <xref:System.Xml.XmlNamespaceManager> sınıfı. Daha fazla bilgi ve örnekler için her bir metot veya Özellik Başvurusu sayfasına bağlantıları izleyin.  
  
|Bitiş|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------|---------|  
|Bir ad alanı Ekle|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> Yöntemi|  
|Bir ad alanını Kaldır|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> Yöntemi|  
|Varsayılan ad alanı URI bulma|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Özelliği|  
|İçin bir ad alanı öneki URI bulma|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> Yöntemi|  
|Ad alanı için URI öneki bulun|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> Yöntemi|  
|Geçerli düğüm ad alanlarının listesini alın|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> Yöntemi|  
|Bir ad alanı kapsamı|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri|  
|Bir önek geçerli kapsamda tanımlı olup olmadığını denetleyin|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> Yöntemi|  
|Ön ekleri ve URI'leri ara için kullanılan ad tablosu Al|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Özelliği|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlNamespaceManager>
- [XML Belgeleri ve Verileri](../../../../docs/standard/data/xml/index.md)
