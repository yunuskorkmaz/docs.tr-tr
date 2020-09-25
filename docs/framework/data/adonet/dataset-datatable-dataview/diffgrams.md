---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: aff9c2347fab51d853e19bd9dc16666c4ed549b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172807"
---
# <a name="diffgrams"></a>DiffGrams

DiffGram, veri öğelerinin geçerli ve orijinal sürümlerini tanımlayan bir XML biçimidir. , <xref:System.Data.DataSet> İçeriğini yüklemek ve sürdürmek ve bir ağ bağlantısı üzerinden aktarım için içeriğini serileştirmek Için DiffGram biçimini kullanır. Bir <xref:System.Data.DataSet> DiffGram olarak yazıldığında, <xref:System.Data.DataSet> hem **özgün** hem de **geçerli** satır sürümlerinin, satır hata bilgilerinin ve satır sırasının sütun değerleri de dahil olmak üzere, Içeriğini doğru şekilde yeniden oluşturmak için DiffGram değerini tüm gerekli bilgilerle doldurur.  
  
 XML Web hizmetinden bir gönderme ve alma <xref:System.Data.DataSet> işlemi yaparken, DiffGram biçimi örtülü olarak kullanılır. Ayrıca, <xref:System.Data.DataSet> **ReadXml** YÖNTEMINI kullanarak bir XML 'in Içeriğini yüklerken veya <xref:System.Data.DataSet> **WriteXml** metodunu kullanarak XML Içindeki içeriğini yazarken, içeriğin bir DiffGram olarak okunacağını veya yazıldığını belirtebilirsiniz. Daha fazla bilgi için bkz. [XML 'Den veri kümesi yükleme](loading-a-dataset-from-xml.md) ve [XML verileri olarak veri kümesi içerikleri yazma](writing-dataset-contents-as-xml-data.md).  
  
 DiffGram biçimi öncelikle .NET Framework tarafından, içeriği için bir serileştirme biçimi olarak kullanıldığında <xref:System.Data.DataSet> , bir Microsoft SQL Server veritabanındaki tablolardaki verileri değiştirmek için de DiffGram kullanabilirsiniz.  
  
 Bir DiffGram, tüm tabloların içeriği bir öğeye yazılarak oluşturulur **\<diffgram>** .  
  
### <a name="to-generate-a-diffgram"></a>Bir DiffGram oluşturmak için  
  
1. Kök tablolarının bir listesini (diğer bir deyişle, herhangi bir üst öğeye sahip olmayan tabloları) oluşturun.  
  
2. Listedeki her tablo ve alt öğeleri için, ilk DiffGram bölümünde tüm satırların geçerli sürümünü yazın.  
  
3. İçindeki her tablo için, <xref:System.Data.DataSet> DiffGram bölümündeki tüm satırların orijinal sürümünü yazın **\<before>** .  
  
4. Hataları olan satırlarda, **\<errors>** DiffGram bölümünün bölümüne hata içeriğini yazın.  
  
 Bir DiffGram, XML dosyasının başından sonuna sırayla işlenir.  
  
### <a name="to-process-a-diffgram"></a>Bir DiffGram işlemek için  
  
1. DiffGram öğesinin geçerli sürümünü içeren ilk bölümünü işleyin.  
  
2. **\<before>** Değiştirilen ve silinen satırların orijinal satır sürümünü içeren ikinci veya bölümü işleyin.  
  
    > [!NOTE]
    > Bir satır silinmiş olarak işaretlenmişse, silme işlemi, geçerli özelliğin özelliğine bağlı olarak satırın alt öğelerini de silebilir `Cascade` <xref:System.Data.DataSet> .  
  
3. Bölümünü işleyin **\<errors>** . Bu bölümdeki her öğe için belirtilen satır ve sütun için hata bilgilerini ayarlayın.  
  
> [!NOTE]
> <xref:System.Data.XmlWriteMode>Öğesini DiffGram olarak ayarlarsanız, hedefin içeriği <xref:System.Data.DataSet> ve asıl <xref:System.Data.DataSet> farklı olabilir.  
  
## <a name="diffgram-format"></a>DiffGram biçimi  

 DiffGram biçimi üç bölüme ayrılmıştır: Şu örnekte gösterildiği gibi geçerli veriler, özgün (veya "önceki") veriler ve hatalar bölümü.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 DiffGram biçimi aşağıdaki veri bloklarından oluşur:  
  
 **\<**  ***DataInstance***  **>**  
 Bu öğenin adı, ***DataInstance***, bu belgede açıklama amacıyla kullanılır. ***DataInstance*** öğesi bir veya bir <xref:System.Data.DataSet> satırını temsil eder <xref:System.Data.DataTable> . *DataInstance*yerine, öğesi veya adını içerir <xref:System.Data.DataSet> <xref:System.Data.DataTable> . DiffGram biçimindeki bu blok, değiştirilmiş olup olmadığı geçerli verileri içerir. Değiştirilen bir öğe veya satır, **diffgr: hasChanges** ek açıklaması ile tanımlanır.  
  
 **\<diffgr:before>**  
 DiffGram biçimindeki bu blok, bir satırın özgün sürümünü içerir. Bu bloktaki öğeler, **diffgr: ID** ek açıklaması kullanılarak ***DataInstance*** bloğundaki öğelerle eşleştirilir.  
  
 **\<diffgr:errors>**  
 DiffGram biçimindeki bu blok, ***DataInstance*** bloğundaki belirli bir satır için hata bilgilerini içerir. Bu bloktaki öğeler, **diffgr: ID** ek açıklaması kullanılarak ***DataInstance*** bloğundaki öğelerle eşleştirilir.  
  
## <a name="diffgram-annotations"></a>DiffGram ek açıklamaları  

 DiffGram, içindeki farklı satır sürümlerini veya hata bilgilerini temsil eden farklı DiffGram bloklarından öğeleri ilişkilendirmek için birkaç ek açıklama kullanır <xref:System.Data.DataSet> .  
  
 Aşağıdaki tablo, DiffGram ad alanında tanımlanan DiffGram açıklamalarını açıklar **urn: schemas-microsoft-com: XML-DiffGram-v1**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**id**|**\<diffgr:before>** Ve **\<diffgr:errors>** blokdaki öğeleri bloktaki öğelere eşleştirmek için kullanılır **\<** ***DataInstance*** **>** . **Diffgr: ID** ek açıklamasına sahip değerler *[TableName] [RowIdentifier]* biçiminde. Örneğin: `<Customers diffgr:id="Customers1">`.|  
|**parentID**|Bloğundan hangi öğenin **\<** ***DataInstance*** **>** geçerli öğenin üst öğesi olduğunu tanımlar. **Diffgr: parentID** ek açıklamasına sahip değerler *[TableName] [RowIdentifier]* biçiminde. Örneğin: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Bloktaki bir satırı **\<** ***DataInstance*** **>** değiştirildiği şekilde tanımlar. **HasChanges** ek açıklaması aşağıdaki iki değerden birine sahip olabilir:<br /><br /> **takılmamış**<br /> **Eklenen** bir satırı tanımlar.<br /><br /> **değiştirdi**<br /> Blokta **orijinal** bir satır sürümü içeren **değiştirilmiş** bir satırı tanımlar **\<diffgr:before>** . **Silinen** satırların bloğunda **orijinal** bir satır sürümü olacağını unutmayın **\<diffgr:before>** , ancak blokta hiçbir açıklamalı öğe olmayacaktır **\<** ***DataInstance*** **>** .|  
|**hasErrors**|Blok içindeki bir satırı **\<** ***DataInstance*** **>** **RowError**ile tanımlar. Hata öğesi **\<diffgr:errors>** bloğa yerleştirildi.|  
|**Hata**|Bloktaki belirli bir öğe için **RowError** metnini içerir **\<diffgr:errors>** .|  
  
 , <xref:System.Data.DataSet> İçeriğini bir DiffGram olarak okurken veya yazarken ek açıklamalar içerir. Aşağıdaki tabloda, **urn: schemas-microsoft-com: XML-msdata**ad alanında tanımlanan bu ek açıklamalar açıklanmaktadır.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**RowOrder**|Orijinal verilerin satır sırasını korur ve belirli bir satırın dizinini tanımlar <xref:System.Data.DataTable> .|  
|**Lene**|Bir sütunu, bir **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanmış olacak şekilde tanımlar. Özniteliği **msdata: Hidden** *[ColumnName]*= "*Value*" biçiminde yazılır. Örneğin: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Gizli sütunların yalnızca veri içerdikleri bir DiffGram özniteliği olarak yazıldığını unutmayın. Aksi takdirde, bunlar yok sayılır.|  
  
## <a name="sample-diffgram"></a>Örnek DiffGram  

 DiffGram biçimine bir örnek aşağıda gösterilmiştir. Bu örnek, değişiklikler kaydedilmeden önce tablodaki bir satırdaki bir güncelleştirmenin sonucunu gösterir. "ALFKI" CustomerID içeren satır değiştirilmiş, ancak güncelleştirilmedi. Sonuç olarak, bloğunda "Customers1" adlı bir **diffgr: ID** 'Si olan **geçerli** bir satır vardır **\<** ***DataInstance*** **>** ve bloğunda "Customers1" **diffgr: ID değerine** sahip **orijinal** bir satır vardır **\<diffgr:before>** . "ANATR" CustomerID içeren satır bir **RowError**içerir, bu nedenle ile açıklanmakta `diffgr:hasErrors="true"` ve bloğunda ilgili bir öğe vardır **\<diffgr:errors>** .  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML Verileri Olarak DataSet İçeriği Yazma](writing-dataset-contents-as-xml-data.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
