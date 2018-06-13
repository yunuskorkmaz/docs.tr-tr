---
title: Bir XML belgesi ad alanlarını yönetme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47162a43c942416c5a2b842663288290c9f43f62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574728"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Bir XML belgesi ad alanlarını yönetme
XML ad alanları, özel ve önceden tanımlanmış URI ile bir XML belgesi öğe ve öznitelik adları ilişkilendirin. Bu ilişkileri oluşturmak için ad alanı URI ön eklerini tanımlayın ve XML verileri öğe ve öznitelik adları nitelemek için ön eklerin kullanın. Ad alanları öğe ve öznitelik ad çakışmaları önlemek ve öğeleri ve özniteliklerinin aynı ada sahip işlenmesini ve farklı bir şekilde doğrulandı etkinleştirin.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Ad alanlarını bildirme  
 Bir öğe üzerinde bir ad alanı bildirmek için kullandığınız `xmlns:` özniteliği:  
  
 `xmlns:<name>=<"uri">`  
  
 Burada `<name>` ad alanı öneki ve `<"uri">` ad alanını tanımlayan bir URI. Önek bildirme sonra öğeleri ve özniteliklerinin bir XML belgesi nitelemek ve ad alanı URI'si ile ilişkilendirmek için kullanabilirsiniz. Ad alanı öneki belge boyunca kullanıldığından uzunluğu kısa olmalıdır.  
  
 Bu örnek iki tanımlar `BOOK` öğeleri. İlk öğe öğesi önekiyle tam `mybook`, ve ikinci öğe önekiyle tam `bb`. Her ön eki, farklı bir ad URI ile ilişkilidir:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Bir öğenin belirli bir ad alanının bir parçası olduğunu belirtmek için ad alanı önekini ekleyin. Örneğin, bir `Author` öğenin ait olduğu `mybook` ad alanı, onu bildirilen olarak `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Bildirim kapsamı  
 Bir ad alanı bildiriminin içinde bildirilen öğesinin sonuna kadar noktasından etkili olur. Bu örnekte, ad alanı tanımlanan `BOOK` öğesi olmayan uygulama dışında öğelerine `BOOK` öğesi, gibi `Publisher` öğe:  
  
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
  
 Bir ad alanı kullanılabilir, ancak XML belgesi üstünde görüntülenecek yok önce bildirilmesi gerekir.  
  
 Birden çok ad alanını bir XML belgesi kullandığınızda, bir ad alanı temizleyici görünümlü bir belge oluşturmak için varsayılan ad alanı tanımlayabilirsiniz. Varsayılan ad alanını kök öğesi içinde bildirilir ve belgedeki tüm nitelenmemiş öğelere uygulanır. Varsayılan ad alanlarını yalnızca öğelerine öznitelikler için geçerlidir.  
  
 Varsayılan ad alanını kullanmak için önek ve iki nokta üst üste öğesindeki bildirim alanından çıkarın:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Ad alanlarını yönetme  
 <xref:System.Xml.XmlNamespaceManager> Sınıfı ad alanı URI koleksiyonu depolar ve kendi önekleri ve yukarı, bakmanızı sağlayan ekleyin ve bu koleksiyondan ad alanlarını kaldırma. Bazı bağlamlarda bu sınıfı daha iyi XML işlem performansı için gereklidir. Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfını kullanan <xref:System.Xml.XmlNamespaceManager> XPath desteği.  
  
 Ad alanı manager ad alanında bulunan tüm doğrulaması gerçekleştirmez, ancak önekleri ve ad alanlarını zaten doğrulandı ve uygun varsayar [W3C ad alanları](https://www.w3.org/TR/REC-xml-names/) belirtimi.  
  
> [!NOTE]
>  [LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) kullanmayan <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için. Bkz: [XML ad alanları ile çalışma](https://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) LINQ belgelerinde LINQ-XML kullanırken ad alanlarını yönetme hakkında bilgi.  
  
 Bazı ile gerçekleştirebileceğiniz yönetimi ve arama görevleri <xref:System.Xml.XmlNamespaceManager> sınıfı. Daha fazla bilgi ve örnekler için her bir yöntemi veya özelliği için başvuru sayfası için bağlantıları izleyin.  
  
|Bitiş|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|--------|---------|  
|Bir ad alanı Ekle|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> Yöntemi|  
|Bir ad alanı Kaldır|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> Yöntemi|  
|Varsayılan ad alanı URI Bul|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Özelliği|  
|URI bulmak için bir ad alanı öneki|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> Yöntemi|  
|Bir ad alanı için URI öneki Bul|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> Yöntemi|  
|Geçerli düğümdeki ad alanlarının listesini alın|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> Yöntemi|  
|Bir ad alanı kapsam|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri|  
|Bir önek geçerli kapsamda tanımlı olup olmadığını denetleyin|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> Yöntemi|  
|Ön ekleri ve URI'ler aramak için kullanılan ad tablosunu Al|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Özelliği|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlNamespaceManager>  
 [XML Belgeleri ve Verileri](../../../../docs/standard/data/xml/index.md)
