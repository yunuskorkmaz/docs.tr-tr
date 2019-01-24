---
title: XML'den DataSet Schema bilgilerini yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: bde264684eb4d36ae59e9ed966c88f379231ac73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596105"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML'den DataSet Schema bilgilerini yükleme
Şemasını bir <xref:System.Data.DataSet> (kendi tablolar, sütunlar, ilişkiler ve kısıtlamalar) programlı olarak tarafından oluşturulan tanımlanabilir **dolgu** veya **FillSchema** yöntemlerinin bir <xref:System.Data.Common.DataAdapter>, veya gelen yüklenen bir XML belgesi. Yüklenecek **veri kümesi** şema bilgileri bir XML belgesinden ya da kullanabilirsiniz **ReadXmlSchema** veya **InferXmlSchema** yöntemi **verikümesi**. **ReadXmlSchema** yüklemek veya tanım Çıkarsama sağlar **veri kümesi** belgesinden XML Şeması Tanım Dili (XSD) şemaya veya satır içi XML şeması bir XML belgesi içeren şema bilgileri. **InferXmlSchema** belirttiğiniz belirli XML ad alanları yoksayılıyor çalışırken XML belgesi şemanın çıkarsandığı olanak tanır.  
  
> [!NOTE]
>  Tablo, sıralama bir **veri kümesi** aktarmak için Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir bir **veri kümesi** XSD yapıları (örneğin, iç içe geçmiş ilişkileri) kullanarak bellek içi oluşturulmuş. Bu nedenle, alıcısı **veri kümesi** tablo bu durumda sıralamaya bağlı olmamalıdır. Ancak, tablo sıralama her zaman korunur şemasını **veri kümesi** aktarılan XSD dosyalarından, bellek içi oluşturulan yerine okundu.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Şeması'nı yüklemek için bir **veri kümesi** herhangi bir veri yükleme olmadan bir XML belgesinden, kullandığınız **ReadXmlSchema** yöntemi **veri kümesi**. **ReadXmlSchema** oluşturur **veri kümesi** şeması XML Şeması Tanım Dili (XSD) şemaya tanımlanmadı.  
  
 **ReadXmlSchema** yöntemi, bir dosyanın adında bir akış tek bir bağımsız değişken alır veya bir **XmlReader** yüklenecek XML belgesi içeren. XML belgesi, yalnızca şema içerebilir veya şema satır içi verilerini içeren XML öğeleri ile içerebilir. Satır içi şema XML şema olarak yazma hakkında daha fazla ayrıntı için bkz. [türetme DataSet ilişkisel yapısını XML Şeması (XSD) öğesinden](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 XML belgesi geçirilmiş **ReadXmlSchema** hiçbir satır içi şema bilgileri içeriyor **ReadXmlSchema** XML belgesi içindeki öğeleri şemanın çıkarsandığı. Varsa **veri kümesi** zaten bir şema içeriyor. Geçerli şema zaten mevcut değilse yeni tablolar ekleyerek genişletilir. Yeni sütunlar için var olan tablolara eklenen eklenmeyecek. Zaten eklenmiş bir sütun varsa **veri kümesi** ancak sütunu türü uyumsuz buldu XML'de özel durum harekete geçirilir. Hakkında ayrıntılar için **ReadXmlSchema** bir şema çıkarsar bir XML belgesinden bkz [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Ancak **ReadXmlSchema** yükler veya yalnızca şeması çıkarır bir **veri kümesi**, **ReadXml** yöntemi **veri kümesi** yükler veya her ikisi de algılar Şema ve XML belgesinde bulunan veriler. Daha fazla bilgi için [XML'den DataSet yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Aşağıdaki kod örneğinde nasıl yükleneceğini gösterir. bir **veri kümesi** şeması bir XML belgesi ya da akış. Gönderilmiş bir XML şema dosyası adı ilk örnekte gösterilmektedir **ReadXmlSchema** yöntemi. İkinci örnekte gösterildiği bir **System.IO.StreamReader**.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 Ayrıca bildirebilirsiniz **veri kümesi** kullanarak bir XML belgesi, şema çıkarsanacak **InferXmlSchema** yöntemi **veri kümesi**. **InferXmlSchema** gibi her ikisi de aynı işlevleri **ReadXml** ile bir **XmlReadMode** , **InferSchema** (verileri yükler hem de şemayı algılar) ve **ReadXmlSchema** belgenin okunan satır içi şema içeriyorsa. Ancak, **InferXmlSchema** şema çıkarıldığında yok sayılacak belirli XML ad alanları belirtmek için izin verme ek yeteneği sağlar. **InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir akışa bir dosya adıyla belirtilen XML belgesinin konumunu veya **XmlReader**; ve bir dize dizisi XML ad alanları, işlem tarafından yok sayılacak.  
  
 Örneğin, aşağıdaki XML göz önünde bulundurun:  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 Önceki XML belgesindeki öğeler için belirtilen öznitelikleri nedeniyle hem **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi ile bir **XmlReadMode** , **InferSchema** belgede her öğe için tablolar oluşturur: **Kategorileri**, **CategoryID**, **CategoryName**, **açıklama**, **ürünleri**, **ProductID**, **Türünde**, ve **kullanımdan**. (Daha fazla bilgi için [DataSet ilişkisel yapısını çıkarma XML'den](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Ancak, yalnızca oluşturmak için daha uygun bir yapı olacaktır **kategorileri** ve **ürünleri** tablolar oluşturmak için sonra da **CategoryID**, **CategoryName** , ve **açıklama** sütunlarında **kategorileri** tablosunu ve **ProductID**, **türünde**, ve **Artık Üretilmiyor** sütunlarında **ürünleri** tablo. Çıkarsanan şema XML öğeleri belirtilen öznitelikleri yoksayılmasını sağlamak için kullanın **InferXmlSchema** yöntemi ve XML ad alanı belirtin **officedata** gösterildiği yoksayılacak Aşağıdaki örnek.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
