---
title: XML’den DataSet Schema Bilgilerini Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4eb211ed13b5f2fe066cd7570c97ae324b187b34
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203503"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML’den DataSet Schema Bilgilerini Yükleme
A <xref:System.Data.DataSet> (tablolarının, sütunlarının, ilişkilerin ve kısıtlamalarının) şeması programlı bir şekilde tanımlanabilir, bir veya bir <xref:System.Data.Common.DataAdapter>XML belgesinden **Fill** ya da **FillSchema** yöntemleriyle oluşturulur. Bir XML belgesinden **veri kümesi** şema bilgilerini yüklemek Için, **veri kümesinin** **ReadXmlSchema** veya **InferXmlSchema** yöntemini kullanabilirsiniz. **ReadXmlSchema** , XML şeması tanım DILI (xsd) şeması veya satır Içi XML şemasına sahıp bir XML belgesi Içeren belgeden **veri kümesi** şema bilgilerini yüklemenize veya çıkarmanıza olanak sağlar. **InferXmlSchema** , BELIRTTIĞINIZ belirli XML ad alanlarını YOKSAYARAK şemayı XML belgesinden çıkarmanızı sağlar.  
  
> [!NOTE]
> Bir **veri** kümesindeki tablo SıRALAMASı, xsd yapıları (iç içe geçmiş ilişkiler gibi) kullanılarak bellekte oluşturulmuş bir **veri kümesini** aktarmak IÇIN Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir. Bu nedenle, **veri kümesinin** alıcısının bu durumda tablo sıralamasına bağlı olmaması gerekir. Ancak, aktarılan **veri kümesinin** şeması, bellek içi OLUŞTURULMASı yerine xsd dosyalarından okunmadıysa tablo sıralaması her zaman korunur.  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 Bir veri **kümesinin** şemasını herhangi bir veri yüklemeden bir XML belgesinden yüklemek için, veri **kümesinin** **ReadXmlSchema** yöntemini kullanabilirsiniz. **READXMLSCHEMA** XML şeması tanım DILI (xsd) şeması kullanılarak tanımlanmış **veri kümesi** şeması oluşturur.  
  
 **ReadXmlSchema** yöntemi bir dosya adı, bir akış veya yüklenecek XML belgesini Içeren bir **XmlReader** değeri alır. XML belgesi yalnızca şemayı içerebilir veya veri içeren XML öğeleriyle birlikte satır içi şema içerebilir. Satır içi şemayı XML şeması olarak yazma hakkında daha fazla bilgi için bkz. [xml şemasından (xsd) DataSet Ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
 **ReadXmlSchema** ÖĞESINE geçirilen XML belgesi satır içi şema bilgisi Içermiyorsa, **ReadXmlSchema** şemayı XML belgesindeki öğelerden çıkaracaktır. **Veri kümesi** zaten bir şema içeriyorsa, geçerli şema zaten mevcut değilse yeni tablolar eklenerek genişletilir. Yeni sütunlar, var olan tablolara eklenmek üzere eklenmeyecek. Eklenmekte olan bir sütun, **veri kümesinde** zaten varsa ancak XML 'de bulunan sütunla uyumsuz bir türe sahipse, bir özel durum oluşturulur. **ReadXmlSchema** 'ın bir XML belgesinden bir şemayı nasıl kullandığını öğrenmek için bkz. [XML 'Den veri kümesi ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.  
  
 **ReadXmlSchema** yalnızca bir **veri kümesinin**şemasını yükler veya bu şemayı sağlasa da, **veri kümesinin** **ReadXml** yöntemi hem şemayı hem de XML belgesinde içerilen verileri yükler ya da bunları anlar. Daha fazla bilgi için bkz. [XML 'Den veri kümesi yükleme](loading-a-dataset-from-xml.md).  
  
 Aşağıdaki kod örnekleri, bir XML belgesinden veya akışından bir **veri kümesi** şemasının nasıl yükleneceğini göstermektedir. İlk örnek, **ReadXmlSchema** yöntemine GEÇIRILEN bir XML şema dosyası adını gösterir. İkinci örnekte bir **System. IO. StreamReader**gösterilmektedir.  
  
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
 Veri kümesinin, **veri kümesinin** **InferXmlSchema** yöntemini kullanarak bir XML belgesinden şemasını çıkarmasını da söyleyebilirsiniz. **InferXmlSchema** , her ikisi de de bir **XmlReadMode** for **InferSchema** (verileri ve KERS şeması yükler) ve okunan belge satır içi şema içermiyorsa, her ikisi de aynı şekilde çalışır. Ancak, **InferXmlSchema** , şema çıkarsandığınızda yok SAYıLACAK belirli XML ad alanlarını belirtmenize olanak tanıyan ek bir özellik sunar. **InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir dosya adı, akış veya **XMLREADER**ile belirtilen XML belgesinin konumu. ve işlem tarafından yok sayılacak XML ad alanlarının dize dizisi.  
  
 Örneğin, aşağıdaki XML 'i göz önünde bulundurun:  
  
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
  
 Önceki XML belgesindeki öğeler için belirtilen öznitelikler nedeniyle, **ınsecollection** 'ın bir **XmlReadMode** 'u olan **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi, içindeki her öğe için tablo oluşturur. belgedeki **Kategoriler**, **KategoriNo**, **CategoryName**, **Açıklama**, **Ürünler**, **ProductID**, **ReorderLevel**ve **Discontinued**. (Daha fazla bilgi için bkz. [XML 'Den veri kümesi Ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.) Ancak, daha uygun bir yapı yalnızca **Kategoriler** ve **Ürünler** tabloları oluşturmak ve ardından **Kategoriler** tablosunda **CategoryID**, **CategoryName**ve **Description** sütunları oluşturmak ve **Products** tablosundaki ProductID, **ReorderLevel**ve **Discontinued** sütunları. Çıkarılan şemanın XML öğelerinde belirtilen öznitelikleri yoksaymasını sağlamak için, **InferXmlSchema** yöntemini kullanın ve aşağıdaki örnekte gösterildiği gibi, **OFFICEVERILERININ** yok sayılacak XML ad alanını belirtin.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
