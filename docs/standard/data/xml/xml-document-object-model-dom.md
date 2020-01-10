---
title: XML Belge Nesne Modeli (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
ms.openlocfilehash: 4faa481a6331863112b7dba65bdbccb69cd12b7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709965"
---
# <a name="xml-document-object-model-dom"></a>XML Belge Nesne Modeli (DOM)

XML Belge Nesne Modeli (DOM) sınıfı, bir XML belgesinin bellek içi gösterimidir. DOM bir XML belgesini programlı bir şekilde okumanıza, değiştirmenize ve değiştirmenize olanak sağlar. **XmlReader** sınıfı XML 'yi de okur; Ancak, önbelleğe alınmamış, salt iletme, salt okunurdur erişimi sağlar. Bu, bir özniteliğin veya bir öğenin içeriğinin veya **XmlReader**ile düğüm ekleme ve kaldırma yeteneğinin değerlerini düzenleme özelliği olmadığı anlamına gelir. Düzenlemeler, DOM 'ın birincil işlevidir. XML verilerinin bellekte temsil edildiği yaygın ve yapılandırılmış bir yoldur, ancak gerçek XML verileri bir dosya içinde veya başka bir nesneden geldiği sırada doğrusal bir biçimde depolanır. XML verileri aşağıda verilmiştir.

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

Aşağıdaki çizim, bu XML verileri DOM yapısına okurken belleğin nasıl yapılandırıldığını gösterir.

![XML belge yapısı](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree") XML belge yapısı

XML belge yapısında, bu çizimdeki her bir daire, **XMLNode** nesnesi olarak adlandırılan bir düğümü temsil eder. **XMLNode** NESNESI, Dom ağacındaki temel nesnedir. **XMLNode**'Yi genişleten **XmlDocument** sınıfı, belgede bir bütün olarak işlem gerçekleştirmeye yönelik yöntemleri destekler (örneğin, belleğe yükleme veya XML bir dosyaya kaydetme). Ayrıca, **XmlDocument** tüm XML belgesindeki düğümleri görüntülemek ve işlemek için bir yol sağlar. Hem **XMLNode** hem de **XmlDocument** performans ve Kullanılabilirlik geliştirmeleri içerir ve şunları yapmak için yöntemlere ve özelliklere sahiptir:

- Öğe düğümleri, varlık başvuru düğümleri vb. gibi DOM 'a özgü düğümlere erişin ve değiştirin.

- Bir öğe düğümündeki metin gibi, düğümün içerdiği bilgilere ek olarak tüm düğümleri alın.

  > [!NOTE]
  > Bir uygulama, DOM tarafından sağlanmış yapı veya Düzenle özelliklerine ihtiyaç sağlamazsa, **XmlReader** ve **XmlWriter** sınıfları önbelleğe alınmamış, salt iletme akışı xml 'e erişim sağlar. Daha fazla bilgi için bkz. <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter>.

**Düğüm** nesnelerinin bir dizi yöntem ve özellik yanı sıra temel ve iyi tanımlanmış özellikler vardır. Bu özelliklerden bazıları şunlardır:

- Düğümlerin tek bir üst düğümü vardır, üst düğüm, doğrudan üzerlerine düğüm. Üst düzey düğüm olduğu ve belgenin kendisini ve belge parçalarını içeren tek bir üst öğe olmayan tek düğümler belge köküdür.

- Çoğu düğüm, doğrudan düğümlerin altındaki düğümler olan birden çok alt düğüme sahip olabilir. Aşağıda alt düğümlere sahip olan düğüm türlerinin bir listesi verilmiştir.

  - **Belge**

  - **DocumentFragment**

  - **EntityReference**

  - **Öğe**

  - **Öznitelik**

  **XmlDeclaration**, **Gösterim**, **varlık**, **CDataSection**, **metin**, **Açıklama**, **processinginstruction**ve **DocumentType** düğümlerinin alt düğümleri yoktur.

- **Kitap** ve **PubInfo** düğümleri tarafından diyagramda temsil edilen aynı düzeydeki düğümler eşdüzey düzeydir.

DOM 'ın bir özelliği öznitelikleri nasıl işler. Öznitelikler üst, alt ve eşdüzey ilişkilerin parçası olan düğümler değildir. Öznitelikler, öğe düğümünün bir özelliği olarak değerlendirilir ve bir ad ve değer çiftinden oluşur. Örneğin, öğe `price`ilişkili `format="dollar`"içeren XML verileriniz varsa, `format` sözcüğü addır ve `format` özniteliğinin değeri `dollar`olur. **Fiyat** düğümünün `format="dollar"` özniteliğini almak için, imleç `price` öğesi düğümünde bulunduğu zaman **GetAttribute** yöntemini çağırın. Daha fazla bilgi için bkz. [Dom Içindeki özniteliklere erişme](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).

XML belleğe okunduğu için düğümler oluşturulur. Ancak, tüm düğümler aynı türde değildir. XML içindeki bir öğe, işleme yönergesinden farklı kurallara ve sözdizimine sahiptir. Bu nedenle, çeşitli veriler okunabileceği için her düğüme bir düğüm türü atanır. Bu düğüm türü, düğümün özelliklerini ve işlevlerini belirler.

Bellekte oluşturulan düğümlerin türleri hakkında daha fazla bilgi için bkz. [XML düğümlerinin türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Düğüm ağacında oluşturulan nesneler hakkında daha fazla bilgi için, bkz. [nesne HIYERARŞISINI XML verileriyle eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).

Microsoft, bir XML belgesiyle çalışmayı kolaylaştırmak için World Wide Web Konsorsiyumu (W3C) DOM düzey 1 ve düzey 2 ' de bulunan API 'Leri genişletmiştir. W3C standartları tam olarak desteklenirken ek sınıflar, Yöntemler ve özellikler, W3C XML DOM kullanılarak yapılabilecekleri daha fazla işlevsellik ekler. Yeni sınıflar, ADO.NET verileriyle eşitleme yöntemleri sunarak, verileri aynı anda XML olarak açığa çıkaran, ilişkisel verilere erişmenizi sağlar. Daha fazla bilgi için bkz. [bir veri kümesini XmlDataDocument Ile eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).

DOM, yapısını değiştirmek, düğüm eklemek veya kaldırmak ya da bir düğüm tarafından tutulan verileri bir öğe tarafından kapsanan metinde değiştirmek için, XML verilerini belleğe okumak için yararlıdır. Ancak diğer bazı sınıflar, diğer senaryolarda DOM 'dan daha hızlı bir şekilde kullanılabilir. XML 'e yönelik hızlı, önbelleğe alınmamış, salt ileri akış erişimi için **XmlReader** ve **XmlWriter**kullanın. İmleç modeli ve **XPath**ile rastgele erişime ihtiyacınız varsa, **XPathNavigator** sınıfını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düğüm Türleri](../../../../docs/standard/data/xml/types-of-xml-nodes.md)
- [XML Verilerine Nesne Hiyerarşisi Eşleme](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
