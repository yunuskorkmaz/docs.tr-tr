---
title: XML Belge Nesne Modeli (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b3a2432deb1e956060ab3615db01821658f8782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959256"
---
# <a name="xml-document-object-model-dom"></a>XML Belge Nesne Modeli (DOM)
XML belge nesne modeli (DOM) sınıfı, bir XML belgesi bir bellek içi gösterimidir. DOM programlı olarak okuma, işleme ve XML belgesi değiştirmenize olanak sağlar. **XmlReader** sınıfı ayrıca XML okur; ancak, önbelleğe alınmamış yalnızca iletme, salt okunur erişim sağlar. Bu özniteliğin değerini veya bir öğeyi veya özelliği ekleyin ve düğümleri kaldırma içeriği düzenlemek için hiçbir özellikleri olduğu anlamına gelir **XmlReader**. DOM sunucunun birincil işlevi olduğu düzenleme Gerçek XML verilerini bir dosya veya başka bir nesneden gelen doğrusal bir biçimde depolanır ancak ortak ve yapılandırılmış biçimde XML verilerini bellek içinde temsil edilen adıdır. XML veri verilmiştir.  
  
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
  
 Aşağıdaki çizim, DOM yapısına bu XML verileri okunurken, bellek nasıl yapılandırıldığını gösterir.  
  
 ![XML belge yapısı](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
XML belge yapısı  
  
 XML belge yapısı içinde bu çizimde gösterilen her bir daire olarak adlandırılan bir düğümü temsil eder. bir **XmlNode** nesne. **XmlNode** nesnesi DOM ağacında temel nesnedir. **XmlDocument** sınıfını **XmlNode**, (örneğin, belleğe yüklenirken veya XML dosya kaydediliyor. bir bütün olarak belge işlemlerini gerçekleştirmek için yöntemleri destekler. Ayrıca, **XmlDocument** görüntüleme ve tüm XML belgesindeki düğüm işlemek için bir yol sağlar. Her ikisi de **XmlNode** ve **XmlDocument** performans ve kullanılabilirlik geliştirmeleri mevcut olabilir ve yöntemleri ve özelliklerine sahiptir:  
  
- Erişim ve öğe düğümlerinin varlık başvurusu düğümleri ve benzeri gibi DOM için belirli düğümler değiştirin.  
  
- Gibi bir öğe düğümü metin düğümü içeren bilgilerine ek olarak tüm düğümleri alın.  
  
    > [!NOTE]
    >  Bir uygulama yapısı veya düzenleme DOM tarafından sağlanan özellikleri gerektirmiyorsa **XmlReader** ve **XmlWriter** sınıfları için XML önbelleğe alınmamış, yalnızca iletme akış erişim sağlar. Daha fazla bilgi için bkz. <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.  
  
 **Düğüm** nesnelerin yöntemleri ve özellikleri yanı sıra, temel ve iyi tanımlanmış özellikler kümesi vardır. Bu özelliklere bazıları şunlardır:  
  
- Düğümlerin tek üst düğümü, bir düğümü hemen üstüne olan üst düğümü vardır. Bir üst öğeye sahip olmayan tek düğümlerin, üst düzey düğüm ve belge parçalarını ve belgenin kendisini içeren belge kökü olur.  
  
- Çoğu düğümleri hemen altındaki düğümleri olan birden çok alt düğümleri olabilir. Alt düğümleri içeren düğüm türlerinin bir listesi verilmiştir.  
  
    - **Belge**  
  
    - **DocumentFragment**  
  
    - **EntityReference**  
  
    - **Öğe**  
  
    - **Öznitelik**  
  
     **XmlDeclaration**, **gösterimi**, **varlık**, **CDATASection**, **metin**,  **Yorum**, **instruction**, ve **DocumentType** düğümlerinin alt düğümleri sahip değil.  
  
- Aynı düzeyde diyagram tarafından temsil edilen düğümlerden **kitap** ve **PubInfo** düğümlerdir, eşdüzey öğesi.  
  
 Bir DOM öznitelikleri nasıl işler özelliğidir. Öznitelik, üst, alt ve eşdüzey ilişkileri parçası olan düğümleri değildir. Öznitelikleri bir öğe düğümü özelliği olarak kabul edilir ve bir ad ve değer çifti oluşur. Örneğin, XML veri oluşan varsa `format="dollar`"öğeyle ilişkili `price`, word `format` adını ve değerini `format` özniteliği `dollar`. Alınacak `format="dollar"` özniteliği **fiyat** düğümünü çağırmanızı **GetAttribute** imleç konumu olduğunda yöntemi `price` öğe düğümü. Daha fazla bilgi için [DOM özniteliklerine erişim](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 XML belleğe okurken düğümler oluşturulur. Ancak, tüm düğümler aynı türdedir. Bir öğenin farklı kuralları ve bir işlem yönergesi sözdizimi vardır. Bu nedenle, çeşitli veri okuma gibi bir düğüm türü için her düğüme atanır. Bu düğüm türü özellikleri ve işlevleri düğümünün belirler.  
  
 Bellekte oluşturulan düğüm türleri hakkında daha fazla bilgi için bkz. [XML düğüm türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Düğüm ağaçta oluşturulan nesneleri hakkında daha fazla bilgi için bkz. [XML verilerine nesne hiyerarşisi eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft, World Wide Web Consortium (W3C) DOM düzey 1 ve 2. düzey bir XML belgesi ile çalışmak daha kolay hale getirmek için kullanılabilen API'lerin genişletti. W3C standartları tam olarak desteklerken, ek sınıfları, yöntemleri ve özellikleri ekleme işlevselliği ne yapılabilir ötesine W3C XML DOM kullanma Yeni sınıflar eşzamanlı olarak XML verileri gösterme, ADO.NET veri ile eşitlemek için yöntem vererek ilişkisel verilere erişmek etkinleştirin. Daha fazla bilgi için [bir DataSet'i bir XmlDataDocument ile eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 DOM belleğe yapısını değiştirmek, ekleme veya düğümleri kaldırma veya bir öğe tarafından içerilen metin olduğu gibi bir düğüm tarafından tutulan verileri değiştirmek için XML verileri okumak için kullanışlıdır. Ancak, diğer sınıfların kullanılabilir olan diğer senaryolarda DOM hızlıdır. XML için hızlı, önbelleğe alınmamış, yalnızca iletme akış erişimi için kullandığınız **XmlReader** ve **XmlWriter**. Bir imleç modeliyle rastgele erişmeniz gerekiyorsa ve **XPath**, kullanın **XPathNavigator** sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Düğüm Türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md)
- [XML Verilerine Nesne Hiyerarşisi Eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
