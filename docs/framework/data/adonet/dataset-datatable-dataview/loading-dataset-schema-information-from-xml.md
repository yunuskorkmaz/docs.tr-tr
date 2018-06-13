---
title: XML'den veri kümesi şema bilgileri yükleniyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760251"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML'den veri kümesi şema bilgileri yükleniyor
Şeması bir <xref:System.Data.DataSet> (kendi tablolar, sütunlar, ilişkileri ve kısıtlamalar) programlı olarak tarafından oluşturulan tanımlanabilir **doldurun** veya **FillSchema** yöntemlerinin bir <xref:System.Data.Common.DataAdapter>, veya gelen yüklenen bir XML belgesi. Yüklemek için **DataSet** şema bilgileri bir XML belgesinden kullanabilirsiniz **ReadXmlSchema** veya **InferXmlSchema** yöntemi **DataSet**. **ReadXmlSchema** yüklemek veya Infer sağlayan **DataSet** XML Şeması Tanım Dili (XSD) şeması veya satır içi XML Şeması XML belgesiyle içeren belgedeki şema bilgileri. **InferXmlSchema** belirttiğiniz belirli XML ad alanları yoksayılıyor sırasında şemasını XML belgesinden olanak tanır.  
  
> [!NOTE]
>  Tablo içinde sıralama bir **DataSet** aktarmak için Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir bir **DataSet** XSD yapıları (örneğin, iç içe geçmiş ilişkileri) kullanarak bellek içi oluşturulmuş. Bu nedenle, alıcısı **DataSet** tablo bu durumda sırasını bağlı olmaması gerekir. Ancak, tablo sıralama her zaman korunur ve şema **DataSet** aktarılan bellek içi oluşturulan yerine XSD dosyalarından okundu.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Şeması yüklemek için bir **DataSet** herhangi bir veri yükleme olmadan bir XML belgesinden, kullandığınız **ReadXmlSchema** yöntemi **DataSet**. **ReadXmlSchema** oluşturur **DataSet** XML Şeması Tanım Dili (XSD) şeması kullanılarak tanımlanan şema.  
  
 **ReadXmlSchema** yöntemi alır, bir akış bir dosya adı, tek bir bağımsız değişken veya bir **XmlReader** yüklenecek XML belgesi içeren. XML belgesi yalnızca şema içerebilir veya şema satır içi ile verileri içeren XML öğeleri içerebilir. Satır içi şeması XML şeması olarak yazma hakkında daha fazla bilgi için bkz [türetme DataSet ilişkisel yapısı XML Şeması'ndan (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 XML belgesi için aktarılırsa **ReadXmlSchema** hiçbir satır içi şema bilgileri içeriyor **ReadXmlSchema** XML belgedeki öğelerden şemasını gösterir. Varsa **DataSet** zaten bir şema içeriyor geçerli şema zaten mevcut değilse yeni tablolar ekleyerek uzatılır. Yeni sütunlar için var olan tablolara eklenen eklenmez. Eklenmekte olan bir sütun varsa **DataSet** ancak sütun türü uyumsuz buldu XML'de, bir özel durum oluşur. Hakkında ayrıntılar için **ReadXmlSchema** bir şema oluşturur bir XML belgesinden bkz [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).  
  
 Ancak **ReadXmlSchema** yükler veya yalnızca şeması oluşturur bir **DataSet**, **ReadXml** yöntemi **DataSet** yükler veya her ikisini de oluşturur Şema ve XML belgesinde bulunan verileri. Daha fazla bilgi için bkz: [bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).  
  
 Aşağıdaki kodu nasıl yükleneceğini örnekler bir **DataSet** bir XML belgesi veya akış şeması. İlk örnek için geçirilen bir XML Şeması dosya adı gösterir **ReadXmlSchema** yöntemi. İkinci örnekteki bir **System.IO.StreamReader**.  
  
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
 Ayrıca söyleyebilirsiniz **DataSet** bir XML belgesi kullanarak şemasına gerçekleştirip **InferXmlSchema** yöntemi **DataSet**. **InferXmlSchema** gibi her ikisi de aynı işlevleri **ReadXml** ile bir **XmlReadMode** , **InferSchema** (verileri yükler yanı sıra şema oluşturur) ve **ReadXmlSchema** okunan belge hiçbir satır içi şema içeriyorsa. Ancak, **InferXmlSchema** şema çıkarıldığında yok sayılacak belirli XML ad alanları belirtmek için sağlayarak ek özelliği sağlar. **InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir akış bir dosya adıyla belirtilen XML belgesinin konumu veya bir **XmlReader**; ve işlem tarafından yoksayılacak XML ad alanları bir dize dizisi.  
  
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
  
 Önceki XML belgesindeki öğeleri için belirtilen öznitelikler nedeniyle hem **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi ile bir **XmlReadMode** , **InferSchema** her öğe için tabloları belgede oluşturursunuz: **kategorileri**, **adlı kullanıcı, Categoryıd'si**, **CategoryName**, **Açıklama**, **ürünleri**, **ProductID**, **türünde**, ve **dönüştürülmesine**. (Daha fazla bilgi için bkz: [çıkarımını yapma DataSet ilişkisel yapısından XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) Ancak, yalnızca oluşturmak için daha uygun bir yapı olacaktır **kategorileri** ve **ürünleri** tabloları, ardından oluşturmak için **adlı kullanıcı, Categoryıd'si**, **CategoryName** , ve **açıklama** sütunlarında **kategorileri** tablo ve **ProductID**, **türünde**, ve **Üretimi Durdurulmuş** sütunlarında **ürünleri** tablo. Çıkarsanan şemanın XML öğeleri belirtilen öznitelikler yoksaymasını sağlamak için kullanmak **InferXmlSchema** yöntemi için XML ad alanı belirtin **officedata** gösterildiği gibi yoksayılacak Aşağıdaki örnek.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
