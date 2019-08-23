---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2bf736445a041ec678ab30474da51fddfba1773b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934474"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram, veri öğelerinin geçerli ve orijinal sürümlerini tanımlayan bir XML biçimidir. , <xref:System.Data.DataSet> İçeriğini yüklemek ve sürdürmek ve bir ağ bağlantısı üzerinden aktarım için içeriğini serileştirmek için DiffGram biçimini kullanır. Bir <xref:System.Data.DataSet> DiffGram olarak yazıldığında, hem <xref:System.Data.DataSet> **özgün** **hem de sütun değerleri dahil olmak üzere içeriği doğru şekilde yeniden oluşturmak için, DiffGram değerini tüm gerekli bilgilerle doldurur. Geçerli** satır sürümleri, satır hata bilgileri ve satır sırası.  
  
 XML Web hizmetinden bir <xref:System.Data.DataSet> gönderme ve alma işlemi yaparken, DiffGram biçimi örtülü olarak kullanılır. Ayrıca, <xref:System.Data.DataSet> **ReadXml** yöntemini kullanarak bir XML 'in içeriğini yüklerken veya <xref:System.Data.DataSet> **WriteXml** metodunu kullanarak XML içindeki içeriğini yazarken, içeriğin bir DiffGram olarak okunacağını veya yazıldığını belirtebilirsiniz. Daha fazla bilgi için bkz. [XML 'Den veri kümesi yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML verileri olarak veri kümesi içerikleri yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 DiffGram biçimi öncelikle .NET Framework tarafından, içeriği için bir <xref:System.Data.DataSet>serileştirme biçimi olarak kullanıldığında, bir Microsoft SQL Server veritabanındaki tablolardaki verileri değiştirmek için de DiffGram kullanabilirsiniz.  
  
 Bir DiffGram, tüm tabloların içeriği bir  **\<DiffGram >** öğesine yazılarak oluşturulur.  
  
### <a name="to-generate-a-diffgram"></a>Bir DiffGram oluşturmak için  
  
1. Kök tablolarının bir listesini (diğer bir deyişle, herhangi bir üst öğeye sahip olmayan tabloları) oluşturun.  
  
2. Listedeki her tablo ve alt öğeleri için, ilk DiffGram bölümünde tüm satırların geçerli sürümünü yazın.  
  
3. İçindeki <xref:System.Data.DataSet>her tablo için, DiffGram öğesinin  **\<önce >** bölümünde tüm satırların özgün sürümünü yazın.  
  
4. Hataları olan satırlarda hata içeriğini  **\<** DiffGram ' nin hatalar > bölümüne yazın.  
  
 Bir DiffGram, XML dosyasının başından sonuna sırayla işlenir.  
  
### <a name="to-process-a-diffgram"></a>Bir DiffGram işlemek için  
  
1. DiffGram öğesinin geçerli sürümünü içeren ilk bölümünü işleyin.  
  
2. Değiştirilen ve silinen satırların orijinal satır sürümünü içeren ikinci veya  **\<önceki >** bölümünü işleyin.  
  
    > [!NOTE]
    > Bir satır silinmiş olarak işaretlenmişse, silme işlemi, geçerli `Cascade` <xref:System.Data.DataSet>özelliğin özelliğine bağlı olarak satırın alt öğelerini de silebilir.  
  
3. Hata > bölümünü işleyin.  **\<** Bu bölümdeki her öğe için belirtilen satır ve sütun için hata bilgilerini ayarlayın.  
  
> [!NOTE]
> Öğesini DiffGram <xref:System.Data.XmlWriteMode> olarak ayarlarsanız, hedefin <xref:System.Data.DataSet> içeriği ve asıl <xref:System.Data.DataSet> farklı olabilir.  
  
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
 Bu öğenin adı, ***DataInstance***, bu belgede açıklama amacıyla kullanılır. ***DataInstance*** öğesi bir <xref:System.Data.DataSet> veya bir satırını <xref:System.Data.DataTable>temsil eder. *DataInstance*yerine, öğesi <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>adını içerir. DiffGram biçimindeki bu blok, değiştirilmiş olup olmadığı geçerli verileri içerir. Değiştirilen bir öğe veya satır, **diffgr: hasChanges** ek açıklaması ile tanımlanır.  
  
 **\<diffgr: > önce**  
 DiffGram biçimindeki bu blok, bir satırın özgün sürümünü içerir. Bu bloktaki öğeler, **diffgr: ID** ek açıklaması kullanılarak ***DataInstance*** bloğundaki öğelerle eşleştirilir.  
  
 **\<diffgr: hatalar >**  
 DiffGram biçimindeki bu blok, ***DataInstance*** bloğundaki belirli bir satır için hata bilgilerini içerir. Bu bloktaki öğeler, **diffgr: ID** ek açıklaması kullanılarak ***DataInstance*** bloğundaki öğelerle eşleştirilir.  
  
## <a name="diffgram-annotations"></a>DiffGram ek açıklamaları  
 DiffGram, <xref:System.Data.DataSet>içindeki farklı satır sürümlerini veya hata bilgilerini temsil eden farklı DiffGram bloklarından öğeleri ilişkilendirmek için birkaç ek açıklama kullanır.  
  
 Aşağıdaki tablo, DiffGram ad alanında tanımlanan DiffGram açıklamalarını açıklar **urn: schemas-microsoft-com: XML-DiffGram-v1**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**id**|**\<** **>**  **\<Diffgr: Before >** ve  **\<diffgr: Errors >** blokları DataInstance bloğundaki öğelere eşleştirmek için kullanılır. **Diffgr: ID** ek açıklamasına sahip değerler *[TableName] [RowIdentifier]* biçiminde. Örneğin: `<Customers diffgr:id="Customers1">`|  
|**parentId**|***Veri örneği*** **\<** **bloğundan>** hangi öğenin geçerli öğenin üst öğesi olduğunu tanımlar. **Diffgr: parentID** ek açıklamasına sahip değerler *[TableName] [RowIdentifier]* biçiminde. Örneğin: `<Orders diffgr:parentId="Customers1">`|  
|**hasChanges**|***Veri örneği*** **\<** **bloğundaki>** bir satırı değiştirildiği şekilde tanımlar. **HasChanges** ek açıklaması aşağıdaki iki değerden birine sahip olabilir:<br /><br /> **takılmamış**<br /> **Eklenen** bir satırı tanımlar.<br /><br /> **değiştirilmelidir**<br /> **Diffgr: Before > bloğundan önce orijinal bir satır sürümü içeren değiştirilmiş bir satırı tanımlar. \<** **Silinen** satırların **\<** **>**  **\<diffgr: Before > bloğundan önce** orijinal bir satır sürümü olacağını unutmayın, ancak ***DataInstance*** bloğunda hiçbir açıklamalı öğe olmayacaktır.|  
|**hasErrors**|***DataInstance*** **\<** **bloğunda>** **RowError**içeren bir satırı tanımlar. Hata öğesi  **\<diffgr: Errors >** bloğuna yerleştirildi.|  
|**Hata:**|Diffgr: Errors > bloğundaki belirli bir öğe **için RowError** metnini içerir.  **\<**|  
  
 , <xref:System.Data.DataSet> İçeriğini bir DiffGram olarak okurken veya yazarken ek açıklamalar içerir. Aşağıdaki tabloda, **urn: schemas-microsoft-com: XML-msdata**ad alanında tanımlanan bu ek açıklamalar açıklanmaktadır.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**RowOrder**|Orijinal verilerin satır sırasını korur ve belirli <xref:System.Data.DataTable>bir satırın dizinini tanımlar.|  
|**Lene**|Bir sütunu, bir **ColumnMapping** özelliği **MappingType. Hidden**olarak ayarlanmış olacak şekilde tanımlar. Özniteliği **msdata: Hidden** *[ColumnName]* = "*Value*" biçiminde yazılır. Örneğin: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`<br /><br /> Gizli sütunların yalnızca veri içerdikleri bir DiffGram özniteliği olarak yazıldığını unutmayın. Aksi takdirde, bunlar yok sayılır.|  
  
## <a name="sample-diffgram"></a>Örnek DiffGram  
 DiffGram biçimine bir örnek aşağıda gösterilmiştir. Bu örnek, değişiklikler kaydedilmeden önce tablodaki bir satırdaki bir güncelleştirmenin sonucunu gösterir. "ALFKI" CustomerID içeren satır değiştirilmiş, ancak güncelleştirilmedi. Sonuç olarak, **\<** ***veri*** **örneği>** bloğunda "Customers1" adlı bir **diffgr: kimliğine** sahip **geçerli** bir satır ve içinde  **\< "Customers1" diffgr: ID değerine sahip orijinal bir satır var diffgr: > bloğundan önce** . "ANATR" CustomerID içeren satır bir **RowError**içerir, bu nedenle ile `diffgr:hasErrors="true"` açıklanmalıdır ve  **\<diffgr: Errors >** bloğunda ilgili bir öğe vardır.  
  
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

- [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML Verileri Olarak DataSet İçeriği Yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
