---
title: XML Belge Nesne Modeli (DOM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
ms.openlocfilehash: dbc53d713d77cfdc9d0dbb8a201f2b5627a76921
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283396"
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

![XML belge yapısı](media/xml-to-domtree.gif "XML_To_DOMTree") XML belge yapısı

XML belge yapısında, bu çizimdeki her bir daire, **XMLNode** nesnesi olarak adlandırılan bir düğümü temsil eder. **XMLNode** NESNESI, Dom ağacındaki temel nesnedir. **XMLNode**'Yi genişleten **XmlDocument** sınıfı, belgede bir bütün olarak işlem gerçekleştirmeye yönelik yöntemleri destekler (örneğin, belleğe yükleme veya XML bir dosyaya kaydetme). Ayrıca, **XmlDocument** tüm XML belgesindeki düğümleri görüntülemek ve işlemek için bir yol sağlar. Hem **XMLNode** hem de **XmlDocument** performans ve Kullanılabilirlik geliştirmeleri içerir ve şunları yapmak için yöntemlere ve özelliklere sahiptir:

- Öğe düğümleri, varlık başvuru düğümleri vb. gibi DOM 'a özgü düğümlere erişin ve değiştirin.

- Bir öğe düğümündeki metin gibi, düğümün içerdiği bilgilere ek olarak tüm düğümleri alın.

  > [!NOTE]
  > Bir uygulama, DOM tarafından sağlanmış yapı veya Düzenle özelliklerine ihtiyaç sağlamazsa, **XmlReader** ve **XmlWriter** sınıfları önbelleğe alınmamış, salt iletme akışı xml 'e erişim sağlar. Daha fazla bilgi için <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> bölümlerine bakın.

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

DOM 'ın bir özelliği öznitelikleri nasıl işler. Öznitelikler üst, alt ve eşdüzey ilişkilerin parçası olan düğümler değildir. Öznitelikler, öğe düğümünün bir özelliği olarak değerlendirilir ve bir ad ve değer çiftinden oluşur. Örneğin, `format="dollar` "öğesiyle ilişkili" öğesinin bulunduğu XML veriniz varsa `price` , sözcük `format` addır ve `format` öznitelik değeri olur `dollar` . `format="dollar"` **Fiyat** düğümünün özniteliğini almak için, imleç öğe düğümünde bulunduğu zaman **GetAttribute** yöntemini çağırın `price` . Daha fazla bilgi için bkz. [Dom Içindeki özniteliklere erişme](accessing-attributes-in-the-dom.md).

XML belleğe okunduğu için düğümler oluşturulur. Ancak, tüm düğümler aynı türde değildir. XML içindeki bir öğe, işleme yönergesinden farklı kurallara ve sözdizimine sahiptir. Bu nedenle, çeşitli veriler okunabileceği için her düğüme bir düğüm türü atanır. Bu düğüm türü, düğümün özelliklerini ve işlevlerini belirler.

Bellekte oluşturulan düğümlerin türleri hakkında daha fazla bilgi için bkz. [XML düğümlerinin türleri](types-of-xml-nodes.md). Düğüm ağacında oluşturulan nesneler hakkında daha fazla bilgi için, bkz. [nesne HIYERARŞISINI XML verileriyle eşleme](mapping-the-object-hierarchy-to-xml-data.md).

Microsoft, bir XML belgesiyle çalışmayı kolaylaştırmak için World Wide Web Konsorsiyumu (W3C) DOM düzey 1 ve düzey 2 ' de bulunan API 'Leri genişletmiştir. W3C standartları tam olarak desteklenirken ek sınıflar, Yöntemler ve özellikler, W3C XML DOM kullanılarak yapılabilecekleri daha fazla işlevsellik ekler. Yeni sınıflar, ADO.NET verileriyle eşitleme yöntemleri sunarak, verileri aynı anda XML olarak açığa çıkaran, ilişkisel verilere erişmenizi sağlar. Daha fazla bilgi için bkz. [bir veri kümesini XmlDataDocument Ile eşitleme](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).

DOM, yapısını değiştirmek, düğüm eklemek veya kaldırmak ya da bir düğüm tarafından tutulan verileri bir öğe tarafından kapsanan metinde değiştirmek için, XML verilerini belleğe okumak için yararlıdır. Ancak diğer bazı sınıflar, diğer senaryolarda DOM 'dan daha hızlı bir şekilde kullanılabilir. XML 'e yönelik hızlı, önbelleğe alınmamış, salt ileri akış erişimi için **XmlReader** ve **XmlWriter**kullanın. İmleç modeli ve **XPath**ile rastgele erişime ihtiyacınız varsa, **XPathNavigator** sınıfını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düğüm Türleri](types-of-xml-nodes.md)
- [XML Verilerine Nesne Hiyerarşisi Eşleme](mapping-the-object-hierarchy-to-xml-data.md)
