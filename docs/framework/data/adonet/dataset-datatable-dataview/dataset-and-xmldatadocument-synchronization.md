---
title: DataSet ve XmlDataDocument Eşitlemesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: ea597d7caca3174b17ce16a1e9d70c022e3e75c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879820"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>DataSet ve XmlDataDocument Eşitlemesi
ADO.NET <xref:System.Data.DataSet> verilerin ilişkisel bir gösterimini sağlar. Hiyerarşik veri erişimi için .NET Framework XML sınıfları kullanabilirsiniz. Tarihsel olarak, bu iki verilerini sunumu ayrı olarak kullanılmış. Ancak, .NET Framework verilerine ilişkisel ve hiyerarşik temsillerini gerçek zamanlı, zaman uyumlu erişiminizi sağlar **veri kümesi** nesne ve <xref:System.Xml.XmlDataDocument> nesne, sırasıyla.  
  
 Olduğunda bir **veri kümesi** ile eşitlenen bir **XmlDataDocument**, her iki nesne tek bir veri kümesiyle çalıştığınız. Bunun anlamı bir değişiklik yapılırsa **veri kümesi**, değişiklik yansıtılır **XmlDataDocument**ve bunun tersi de geçerlidir. Arasındaki ilişkiyi **veri kümesi** ve **XmlDataDocument** büyük esneklik yerleşik hizmetler tüm paketini erişmek için tek bir veri kümesini kullanarak tek bir uygulama vererek oluşturur. geçici bir çözüm **veri kümesi** (örneğin, Web Forms ve Windows Forms denetimleri ve Visual Studio .NET tasarımcıları), Genişletilebilir Stil Sayfası Dili (XSL), XSLT Dönüşümleri (XSLT) ve XML Path gibi XML Hizmetleri paketi yanı sıra Dil (XPath). Hedef uygulama ile Hizmetleri ayarladığı vermeyeceklerini yoktur; her ikisi de kullanılabilir.  
  
 Eşitleyebilirsiniz birkaç şekilde bir **veri kümesi** ile bir **XmlDataDocument**. Şunları yapabilirsiniz:  
  
- Doldurma bir **veri kümesi** şeması (diğer bir deyişle, ilişkisel bir yapısı) ve verilerle ve ardından yeni bir eşitleme **XmlDataDocument**. Bu, hiyerarşik bir görünümü var olan ilişkisel veri sağlar. Örneğin:  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- Doldurma bir **veri kümesi** yalnızca şema ile (bir türü kesin belirlenmiş gibi **veri kümesi**), ile eşitlemek bir **XmlDataDocument**ve ardından Yük  **XmlDataDocument** XML belgesinden. Bu, var olan hiyerarşik verilerin ilişkisel bir görünümünü sağlar. Sütun adlarının ve tablo adları, **veri kümesi** şema ile eşitlenme istediğiniz XML öğeleri adları aynı olmalıdır. Bu eşleştirme büyük küçük harfe duyarlı değildir.  
  
     Unutmayın, şema **veri kümesi** yalnızca ilişkisel görünümünüzde kullanıma sunmak istiyorsanız XML öğeleri ile eşleşmesi gerekir. Bu şekilde, çok büyük bir XML belgesi ve oldukça küçük bir ilişkisel "Pencere" Bu belge üzerinde olabilir. **XmlDataDocument** tüm XML belgesi olsa bile korur **veri kümesi** yalnızca küçük bir kısmını kullanıma sunar. (Bu ayrıntılı bir örnek için bkz. [bir DataSet'i bir XmlDataDocument ile eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Aşağıdaki kod örneği oluşturma adımlarını gösteren bir **veri kümesi** ve şeması doldurma, ardından ile eşitleme bir **XmlDataDocument**. Unutmayın **veri kümesi** şema yalnızca gerekli öğeleri eşleştirilecek **XmlDataDocument** kullanarak kullanıma sunmak istediğiniz **veri kümesi**.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Yüklenemiyor bir **XmlDataDocument** ile eşitlenmişse bir **veri kümesi** verilerini içeren. bir özel durum oluşturulur.  
  
- Yeni bir **XmlDataDocument** XML belgesinden yükleyin ve ardından ilişkisel görünümünü kullanarak veri erişim **veri kümesi** özelliği **XmlDataDocument**. Şemasını ayarlamanız gerekir **veri kümesi** veri görmeden önce **XmlDataDocument** kullanarak **veri kümesi**. Tablo adlarının, sütun yeniden adları, **veri kümesi** şema ile eşitlenme istediğiniz XML öğeleri adları aynı olmalıdır. Bu eşleştirme büyük küçük harfe duyarlı değildir.  
  
     Aşağıdaki kod örneği, verilerin ilişkisel görünümüne erişime izin gösterilmiştir bir **XmlDataDocument**.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 Başka bir avantajı, eşitleme bir **XmlDataDocument** ile bir **veri kümesi** bir XML belgesi kalitesini korunmasıdır. Varsa **veri kümesi** kullanarak bir XML belgesi doldurulur **ReadXml**, verileri kullanarak bir XML belgesi olarak geri yazıldığında **WriteXml** , önemli ölçüde farklı olabilir Orijinal XML belgesi. Bunun nedeni, **veri kümesi** boşluk veya, XML belgesi öğe sırası gibi hiyerarşik bilgileri gibi biçimlendirme korumaz. **Veri kümesi** ayrıca şemasını eşleşmediğinden yoksayıldı öğeleri XML belgesindeki içermiyor **veri kümesi**. Eşitleme bir **XmlDataDocument** ile bir **veri kümesi** içinde tutulması için özgün XML belgesi hiyerarşik ve biçimlendirme öğesi yapısını sağlayan **XmlDataDocument**, ancak **veri kümesi** sadece veri ve şema bilgilerini uygun içeren **veri kümesi**.  
  
 Eşitlerken bir **veri kümesi** ile bir **XmlDataDocument**, sonuçları alınıp alınmayacağını bağlı olarak farklı olabilir, <xref:System.Data.DataRelation> nesneler iç içe. Daha fazla bilgi için [iç içe DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet’i bir XmlDataDocument ile Eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Türü kesin belirlenmiş eşitleme gösterir **veri kümesi**, en az şeması ile bir **XmlDataDocument**.  
  
 [DataSet Üzerinde XPath Sorgusu Gerçekleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 Bir XPath sorgusu gerçekleştirme içeriğine gösterir bir **veri kümesi**.  
  
 [DataSet’e XSLT Dönüşümü Uygulama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 XSLT dönüşümü uygulama içeriğini gösteren bir **veri kümesi**.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklayan nasıl **veri kümesi** yükleniyor ve içeriğini kalıcı dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir **veri kümesi** XML verileri olarak.  
  
 [DataRelations’ı İç İçe Yerleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Önemini açıklar iç içe geçmiş **DataRelation** nesneleri içeriğini temsil eden, bir **veri kümesi** XML verileri olarak ve bu ilişkileri nasıl oluşturulacağını açıklar.  
  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Açıklar **veri kümesi** ve uygulama verilerini yönetmek ve ilişkisel veritabanları ve XML gibi veri kaynaklarıyla etkileşim kurmak için kullanma.  
  
 <xref:System.Xml.XmlDataDocument>  
 Hakkında başvuru bilgileri içerir **XmlDataDocument** sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
