---
title: XML Belge Nesne Modeli (DOM)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: af9473af6a315feb6b1f0a741525cbf42dd32d1d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom"></a>XML Belge Nesne Modeli (DOM)
XML belge nesne modeli (DOM) sınıfı, bir XML belgesi bir bellek içi gösterimidir. DOM program aracılığıyla okuyun, yönetmek ve bir XML belgesi değiştirmenize olanak sağlar. **XmlReader** sınıfı ayrıca XML okur; ancak, önbelleğe alınmamış salt iletme, salt okunur erişim sağlar. Bu özniteliğin değerini veya bir öğenin veya ekleyin ve düğümleri kaldırma yeteneği içeriğini düzenlemek için özelliği yoktur anlamına gelir **XmlReader**. DOM birincil işlevi olduğu düzenleme Gerçek XML verilerini bir dosya veya başka bir nesneden gelen doğrusal bir biçimde depolanır ancak ortak ve yapılandırılmış şekilde XML verileri bellekte temsil edilen adıdır. XML verilerini verilmiştir.  
  
## <a name="input"></a>Giriş  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 Aşağıdaki çizimde, bu XML verileri DOM yapısına okunduğunda bellek nasıl yapılandırıldığını gösterir.  
  
 ![XML belge yapısı](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
XML belge yapısı  
  
 XML belge yapısında bu çizimdeki her bir daire olarak adlandırılan bir düğümü temsil eder. bir **XmlNode** nesnesi. **XmlNode** nesnesi DOM ağacında temel nesnedir. **XmlDocument** sınıfını genişletir **XmlNode**, (örneğin, belleğe yükleme veya XML bir dosyaya kaydetmeyi. bir bütün olarak belge üzerinde işlem gerçekleştirmek için yöntemlerini destekler Ayrıca, **XmlDocument** görüntülemek ve tüm XML belgesi düğümlerin işlemek için bir yol sağlar. Her ikisi de **XmlNode** ve **XmlDocument** performans ve kullanılabilirlik geliştirmeleri ve yöntemleri ve özellikleri:  
  
-   Erişim ve DOM öğesi düğümleri, varlık başvurusu düğümleri vb. gibi belirli düğümler değiştirin.  
  
-   Bir öğe düğümü metinde gibi düğüm içerir bilgilerine ek olarak tüm düğümleri alır.  
  
    > [!NOTE]
    >  Bir uygulama yapısı veya DOM tarafından sağlanan özellikleri düzenleme gerektirmiyorsa **XmlReader** ve **XmlWriter** sınıfları XML önbelleğe alınmamış, yalnızca ileri akış erişim sağlar. Daha fazla bilgi için bkz. <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.  
  
 **Düğüm** nesnelerin yöntemleri ve özellikleri yanı sıra, temel ve iyi tanımlanmış özellikleri kümesi vardır. Bu özelliklere bazıları şunlardır:  
  
-   Düğümlerin tek üst düğümü, bir düğüm doğrudan yukarıda olan bir üst düğümü vardır. Bir üst öğeye sahip değil yalnızca düğümler var. belge kökü en üst düzey düğüm ve belgenin kendisi ve belge parçalarını içerir  
  
-   Çoğu düğümleri düğümler doğrudan altında birden çok alt düğümleri bulunabilir. Alt düğümleri bulunabilir düğüm türleri listesi verilmiştir.  
  
    -   **Belge**  
  
    -   **DocumentFragment**  
  
    -   **EntityReference**  
  
    -   **Öğesi**  
  
    -   **Özniteliği**  
  
     **XmlDeclaration**, **gösterimi**, **varlık**, **CDATASection**, **metin**,  **Açıklama**, **instruction**, ve **DocumentType** düğümleri alt düğümleri sahip değil.  
  
-   Diyagram tarafından gösterilen aynı düzeyde olan düğümleri **defteri** ve **PubInfo** düğümleri, eşdüzey öğesi olan.  
  
 Bir DOM öznitelikleri nasıl işler özelliğidir. Öznitelikler üst, alt ve eşdüzey ilişkileri parçası olan düğümler değildir. Öznitelikler öğesi düğümünün bir özellik olarak kabul edilir ve bir ad ve değer çifti oluşur. XML verilerini oluşan varsa, örneğin, `format="dollar`"öğeyle ilişkili `price`, word `format` adı ve değeri `format` özniteliği `dollar`. Almak için `format="dollar"` özniteliği **fiyat** düğümü, çağrı **GetAttribute** imleci adresindedir yöntemi `price` öğe düğümü. Daha fazla bilgi için bkz: [DOM öznitelikleri erişme](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 XML belleğe okurken düğümleri oluşturulur. Ancak, tüm düğümler aynı türdeyse. Bir öğenin farklı kurallar ve işlem yönergesi sözdizimi vardır. Bu nedenle, çeşitli veri okuma gibi bir düğüm türü her düğüme atanır. Bu düğüm türü, özellikleri ve işlevleri düğümün belirler.  
  
 Bellekte oluşturulan düğüm türleri hakkında daha fazla bilgi için bkz: [XML düğümlerini türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Düğüm ağaçta oluşturulan nesneler hakkında daha fazla bilgi için bkz: [nesne hiyerarşisi XML verileri eşleştirmesi](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft World Wide Web Konsorsiyumu (W3C) DOM düzey 1 ve Düzey 2 XML belgesiyle çalışması kolay hale getirmek için kullanılabilen API'leri genişletmiştir. W3C standartlarını tam olarak desteklerken, ek sınıfları, yöntemleri ve özellikleri ekleme işlevselliği ne yapılabilir ötesine W3C XML DOM kullanma Yeni sınıflar, aynı anda XML olarak verilerin açığa ADO.NET verilerle eşitlemek için yöntem vermiş ilişkisel veri erişim sağlar. Daha fazla bilgi için bkz: [XmlDataDocument ile bir veri eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 DOM yapısını değiştirmek, ekleme veya düğümleri kaldırma veya bir öğenin bulunan metin olduğu gibi bir düğüm tarafından tutulan verileri değiştirmek için belleğe XML verileri okumak için kullanışlıdır. Bununla birlikte, diğer sınıflar kullanılabilir olan diğer senaryolarda DOM hızlıdır. XML için hızlı, önbelleğe alınmamış, yalnızca ileri akış erişimi için kullandığınız **XmlReader** ve **XmlWriter**. İmleç modeliyle rastgele erişmesi gerekiyorsa ve **XPath**, kullanın **XPathNavigator** sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Düğüm Türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [XML Verilerine Nesne Hiyerarşisi Eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
