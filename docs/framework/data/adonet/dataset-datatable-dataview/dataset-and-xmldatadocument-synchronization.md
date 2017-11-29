---
title: "Veri kümesi ve XmlDataDocument eşitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 923a6b6cf1523c8a11cb509679443b9658e07ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>Veri kümesi ve XmlDataDocument eşitleme
ADO.NET <xref:System.Data.DataSet> ile ilişkisel bir veri gösterimini sağlar. Hiyerarşik veri erişimi için .NET Framework kullanılabilen XML sınıfları kullanabilirsiniz. Tarihsel olarak, bu iki veri sunumu ayrı olarak kullanıldı. Ancak, .NET Framework verilerine ilişkisel ve hiyerarşik gösterimlerini gerçek zamanlı, zaman uyumlu erişimini etkinleştirir **DataSet** nesne ve <xref:System.Xml.XmlDataDocument> nesnesi, sırasıyla.  
  
 Zaman bir **DataSet** ile eşitlenen bir **XmlDataDocument**, hem nesnelerini tek bir veri kümesi ile çalışma. Bunun anlamı bir değişiklik yapılırsa **DataSet**, değişiklik yansıtılır **XmlDataDocument**, bunun tam tersi. Arasındaki ilişkiyi **DataSet** ve **XmlDataDocument** büyük esneklik yerleşik hizmetlerin tüm suite erişimi için tek bir veri kümesi kullanarak tek bir uygulama vererek oluşturur geçici **DataSet** (örneğin, Web formları ve Windows Forms denetimleri ve Visual Studio .NET tasarımcıları), Genişletilebilir Stil sayfası Dili'nin (XML), XSL Dönüşümleri (XSLT) ve XML Path dahil olmak üzere XML hizmetlerinin paketinin yanı sıra Dili (XPath). Hangi hizmetlerin hedef uygulamayla kümesini seçin gerekmez; her ikisi de kullanılabilir.  
  
 Eşitleyebilirsiniz birkaç yolu vardır bir **DataSet** ile bir **XmlDataDocument**. Şunları yapabilirsiniz:  
  
-   Doldurmak bir **DataSet** şeması (diğer bir deyişle, ilişkisel bir yapısı) ve verilerle ve ardından yeni bir eşitleme **XmlDataDocument**. Bu, varolan ilişkisel veri hiyerarşik bir görünümünü sağlar. Örneğin:  
  
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
  
-   Doldurmak bir **DataSet** yalnızca şemasıyla (kesin türü belirtilmiş gibi **DataSet**), ile eşitlemek bir **XmlDataDocument**ve ardından Yük  **XmlDataDocument** bir XML belgesinden. Bu, mevcut hiyerarşik verileri ilişkisel bir görünümünü sağlar. Sütun adlarının ve tablo adlarının, **DataSet** şema ile eşitlenme istediğiniz XML öğelerinin adlarını eşleşmesi gerekir. Bu eşleştirme büyük küçük harfe duyarlı değildir.  
  
     Unutmayın şeması **DataSet** yalnızca ilişkisel görünümünüzde kullanıma sunmak istediğiniz XML öğeleri ile eşleşmesi gerekir. Bu şekilde, çok büyük bir XML belgesi ve çok küçük bir ilişkisel "Pencere" Bu belge üzerinde olabilir. **XmlDataDocument** tüm XML belgesi rağmen korur **DataSet** yalnızca küçük bir kısmı kullanıma sunar. (Bu ayrıntılı bir örnek için bkz: [XmlDataDocument ile bir veri eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Aşağıdaki kod örneği oluşturmak için gereken adımları gösterir bir **DataSet** ve şemasına doldurma ardından ile eşitleme bir **XmlDataDocument**. Unutmayın **DataSet** şema yalnızca gereken öğeleri eşleşecek şekilde **XmlDataDocument** kullanarak kullanıma sunmak istediğiniz **DataSet**.  
  
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
  
     Yüklenemiyor bir **XmlDataDocument** ile eşitlenmişse bir **DataSet** veri içeren. Bir özel durum oluşturulur.  
  
-   Yeni bir **XmlDataDocument** bir XML belgesinden yük ve verileri kullanarak ilişkisel görünümünü erişim **DataSet** özelliği **XmlDataDocument**. Şeması ayarlamak gereken **DataSet** verileri görüntüleyebilmeniz **XmlDataDocument** kullanarak **DataSet**. Tablo adlarının, sütun yeniden adları, **DataSet** şema ile eşitlenme istediğiniz XML öğelerinin adlarını eşleşmesi gerekir. Bu eşleştirme büyük küçük harfe duyarlı değildir.  
  
     Aşağıdaki kod örneği, verileri ilişkisel görünümünü erişmek gösterilmiştir bir **XmlDataDocument**.  
  
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
  
 Eşitleme başka bir avantajı bir **XmlDataDocument** ile bir **DataSet** bir XML belgesi kalitesini korunur. Varsa **DataSet** kullanarak bir XML belgesi doldurulur **ReadXml**, verileri kullanarak bir XML belgesi olarak geri yazıldığında **WriteXml** , önemli ölçüde farklı olabilir Özgün XML belgesi. Bunun nedeni, **DataSet** , boşluk veya XML belgesinden öğe sırası gibi hiyerarşik bilgileri gibi biçimlendirme korumaz. **DataSet** de şeması eşleşmediğinden yoksayıldı öğeleri XML belgesinden içermiyor **Dataset**. Eşitleme bir **XmlDataDocument** ile bir **DataSet** içinde korunmasını özgün XML belgesi biçimlendirme ve hiyerarşik öğesi yapısını sağlayan **XmlDataDocument**, sırada **DataSet** yalnızca veri ve şema bilgilerini uygun içeren **DataSet**.  
  
 Eşitleme yaparken bir **DataSet** ile bir **XmlDataDocument**, sonuçları olup olmadığını bağlı olarak değişebilir, <xref:System.Data.DataRelation> nesneleri iç içe geçmiş. Daha fazla bilgi için bkz: [iç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir veri kümesi XmlDataDocument ile eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Kesin türü belirtilmiş eşitleme gösteren **DataSet**, en az şemasıyla ile bir **XmlDataDocument**.  
  
 [Bir veri kümesine XPath sorgusunu gerçekleştirme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 İçeriğine XPath sorgusunu gerçekleştirme gösteren bir **DataSet**.  
  
 [Bir veri kümesine bir XSLT dönüşümü uygulanarak](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 İçeriği için bir XSLT dönüşümü uygulanarak gösteren bir **DataSet**.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bir veri kümesini XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Açıklar nasıl **DataSet** yükleme ve içeriği kalıcı yapma dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir **DataSet** XML verileri olarak.  
  
 [İç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 Önem düzeyi açıklanmaktadır iç içe geçmiş **DataRelation** nesneleri içeriğini temsil eden olduğunda bir **DataSet** XML verileri olarak ve bu ilişkileri oluşturmayı açıklar.  
  
 [Veri kümeleri, DataTable ve DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Açıklar **DataSet** ve uygulama verilerini yönetmek ve ilişkisel veritabanları ve XML gibi veri kaynakları ile etkileşim kurmak için kullanma.  
  
 <xref:System.Xml.XmlDataDocument>  
 Hakkında başvuru bilgileri içerir **XmlDataDocument** sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
