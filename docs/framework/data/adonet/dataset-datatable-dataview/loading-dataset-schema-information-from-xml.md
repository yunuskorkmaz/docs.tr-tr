---
title: XML’den DataSet Schema Bilgilerini Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151058"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML’den DataSet Schema Bilgilerini Yükleme
Bir <xref:System.Data.DataSet> şema (tabloları, sütunları, ilişkileri ve kısıtlamaları) programlı olarak tanımlanabilir, bir <xref:System.Data.Common.DataAdapter>'nin **Dolgu** veya **FillSchema** yöntemleri tarafından oluşturulabilir veya bir XML belgesinden yüklenebilir. Bir XML belgesinden **DataSet** şema bilgilerini yüklemek için, **DataSet'in** **ReadXmlSchema** veya **InferXmlSchema** yöntemini kullanabilirsiniz. **ReadXmlSchema,** XML Şema tanım dili (XSD) şeması veya satır satır lı XML şeması içeren belgeden **DataSet** şema bilgilerini yüklemenize veya çıkaramanıza olanak tanır. **InferXmlSchema,** belirttiğiniz belirli XML ad alanlarını yoksayarak XML belgesinden şemayı çıkartmanızı sağlar.  
  
> [!NOTE]
> **DataSet'teki** tablo sıralama, XSD yapıları (iç içe ilişkiler gibi) kullanılarak bellekte oluşturulan bir **DataSet'i** aktarmak için Web hizmetlerini veya XML serileştirmeyi kullandığınızda korunmayabilir. Bu nedenle, **DataSet'in** alıcısı bu durumda tablo sıralamasına bağlı olmamalıdır. Ancak, aktarılan **DataSet** şeası bellekte oluşturulmak yerine XSD dosyalarından okunduysa, tablo sıralama her zaman korunur.  
  
## <a name="readxmlschema"></a>Readxmlschema  
 Herhangi bir veri yüklemeden bir XML belgesinden Bir **DataSet** şemasını yüklemek için, **DataSet'in** **ReadXmlSchema** yöntemini kullanabilirsiniz. **ReadXmlSchema,** XML Şema tanım dili (XSD) şeması kullanılarak tanımlanan **DataSet** şemasını oluşturur.  
  
 **ReadXmlSchema** yöntemi, yüklenecek XML belgesini içeren bir dosya adı, akış veya **XmlReader** tek bir bağımsız değişken alır. XML belgesi yalnızca şema içerebilir veya veri içeren XML öğeleriyle satır satır şema içerebilir. XML Şema olarak satır içinde şema yazma hakkında ayrıntılı bilgi için, [XML Schema (XSD) gelen Veri Seti İlişkisel Yapısı Türetilmesi](deriving-dataset-relational-structure-from-xml-schema-xsd.md)bölümüne bakın.  
  
 **ReadXmlSchema'ya** geçirilen XML belgesi satır içinde şema bilgisi içermezse, **ReadXmlSchema** şemayı XML belgesindeki öğelerden çıkaracaktır. **DataSet** zaten bir şema içeriyorsa, geçerli şema zaten yoksa yeni tablolar ekleyerek genişletilir. Varolan tablolara yeni sütunlar eklenmez. Eklenen bir sütun **DataSet'te** zaten varsa ancak XML'de bulunan sütunla uyumsuz bir türü varsa, bir özel durum atılır. **ReadXmlSchema'nın** bir XML belgesinden bir şema çıkartması hakkında ayrıntılı bilgi [için](inferring-dataset-relational-structure-from-xml.md)bkz.  
  
 **ReadXmlSchema** yalnızca bir **DataSet**şeasını yükler veya çıkarsa da, **DataSet'in** **ReadXml** yöntemi Hem şeayı hem de XML belgesinde yer alan verileri yükler veya çıkarır. Daha fazla bilgi için Bkz. [XML'den Veri Seti Yükleme.](loading-a-dataset-from-xml.md)  
  
 Aşağıdaki kod örnekleri, Bir **XML** belgesinden veya akışından bir DataSet şemasını nasıl yükleyeceğimi gösterir. İlk örnek, **ReadXmlSchema** yöntemine geçirilen bir XML Şema dosya adının olduğunu gösterir. İkinci örnek bir **System.IO.StreamReader**gösterir.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
 DataSet'in **InferXmlSchema** yöntemini kullanarak **DataSet'e** şemasını bir XML **DataSet**belgesinden çıkarmasını da öğretebilirsiniz. **InferXmlSchema,** **XmlReadMode** of **InferSchema** (verileri yükler ve şema yükler) ile **ReadXmlml'in** her ikisiyle aynı işlevi görür (veriler yükler ve okunan belge satır içinde şema içermese **ReadXmlSchema.** Ancak, **InferXmlSchema** şema çıkarıldığında göz ardı edilecek belirli XML ad boşluklarını belirtmenize izin veren ek bir yetenek sağlar. **InferXmlSchema** iki gerekli bağımsız değişkenalır: XML belgenin konumu, bir dosya adı, bir akış veya **XmlReader**tarafından belirtilen; ve işlem tarafından yoksayılacak bir dizi XML ad alanı.  
  
 Örneğin, aşağıdaki XML'yi göz önünde bulundurun:  
  
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
  
 Önceki XML belgesindeki öğeler için belirtilen öznitelikler nedeniyle, hem **ReadXmlSchema** yöntemi hem de **InferSchema** **xmlReadMode** ile **ReadXml** yöntemi belgede her öğe için tablolar oluşturacak: **Kategoriler**, **CategoryID**, **CategoryName**, **Açıklama**, **Ürünler**, **ProductID**, **ReorderLevel**, ve **Durdurulan**. (Daha fazla bilgi için [bkz.](inferring-dataset-relational-structure-from-xml.md) Ancak, daha uygun bir yapı yalnızca **Kategoriler** ve **Ürünler** tabloları oluşturmak ve daha sonra **Kategoriler** tablosunda **CategoryID**, **CategoryName**ve **Açıklama** sütunları oluşturmak ve **Ürünler** tablosunda **ProductID**, **ReorderLevel**ve **Durdurulan** sütunlar olacaktır. Çıkarılan şemaXML öğeleri belirtilen öznitelikleri yoksayılsa emin olmak için, **InferXmlSchema** yöntemini kullanın ve aşağıdaki örnekte gösterildiği **gibi, ofis verileri** için göz ardı edilecek XML ad alanını belirtin.  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
