---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: fd452efff2a26b66c06a7762b215df140047286d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085906"
---
# <a name="diffgrams"></a>DiffGrams
Bir DiffGram veri öğelerinin geçerli ve orijinal sürümler tanımlayan bir XML biçimidir. <xref:System.Data.DataSet> Yüklemek ve içeriğini kalıcı hale getirmek ve ağ bağlantısı üzerinden aktarım için içeriği seri hale getirmek için biçimini kullanır. Olduğunda bir <xref:System.Data.DataSet> yazılmış bir DiffGram doğru içeriği, ancak şeması değil, yeniden oluşturmak için gerekli tüm bilgileri DiffGram doldurur <xref:System.Data.DataSet>, hem sütun değerleri dahil olmak üzere **özgün** ve **geçerli** satır sürümleri, satır hatası bilgileri ve satır sırası.  
  
 Gönderme ve alma, bir <xref:System.Data.DataSet> bir XML Web hizmetinden biçimini örtük olarak kullanılır. Ayrıca, içeriği yüklerken bir <xref:System.Data.DataSet> XML kullanarak **ReadXml** yöntemi veya içeriği yazarken bir <xref:System.Data.DataSet> XML kullanarak **WriteXml** belirtebileceğiniz yöntemi içeriği okuma veya bir DiffGram yazılmış olduğunu. Daha fazla bilgi için [XML'den DataSet yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML verileri olarak DataSet içeriği yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Biçimini öncelikle .NET Framework tarafından seri hale getirme biçimi olarak içeriği için kullanılırken bir <xref:System.Data.DataSet>, Microsoft SQL Server veritabanında tablolardaki verileri değiştirmek için DiffGrams de kullanabilirsiniz.  
  
 Tüm tablolara içeriğini yazarak bir Diffgram oluşturulan bir  **\<diffgram >** öğesi.  
  
### <a name="to-generate-a-diffgram"></a>Bir Diffgram oluşturmak için  
  
1.  Kök tablo (diğer bir deyişle, herhangi bir üst olmayan tablolar) listesini oluşturun.  
  
2.  Her tablo ve alt öğeleri listesinde, tüm satırların ilk Diffgram bölümünde geçerli sürüm kullanıma yazın.  
  
3.  Her tablo için <xref:System.Data.DataSet>, varsa özgün sürümü tüm satırların yazma,  **\<önce >** Diffgram bölümü.  
  
4.  Hata içeren satırları yazmak için olan içerik, hata  **\<hataları >** Diffgram bölümü.  
  
 Bir Diffgram sonuna XML dosyasının başından sırayla işlenir.  
  
### <a name="to-process-a-diffgram"></a>Bir Diffgram işlemek için  
  
1.  Satırları geçerli sürümünü içeren Diffgram ilk bölümünü işler.  
  
2.  İkinci işlem veya  **\<önce >** özgün satır sürümü içeren bölümü değiştirilen ve silinen satır.  
  
    > [!NOTE]
    >  Bir satır silindi olarak işaretlenmişse silme işlemini bağlı olarak sıranın alt öğeleri de silebilirsiniz `Cascade` özelliği geçerli <xref:System.Data.DataSet>.  
  
3.  İşlem  **\<hataları >** bölümü. Bu bölümde belirtilen satır ve sütunları her öğe için hata bilgilerini ayarlayın.  
  
> [!NOTE]
>  Ayarlarsanız <xref:System.Data.XmlWriteMode> Diffgram, hedef içeriği için <xref:System.Data.DataSet> ve özgün <xref:System.Data.DataSet> farklı olabilir.  
  
## <a name="diffgram-format"></a>Biçimini  
 Biçimini üç bölümlere ayrılmıştır: geçerli veriyi, özgün (veya "önce") veri ve aşağıdaki örnekte gösterildiği gibi bir hata bölümü.  
  
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
  
 Aşağıdaki veri bloklarını biçimini oluşur:  
  
 **\<**  ***DataInstance***  **>**  
 Bu öğe adı ***DataInstance***, bu belgede açıklama amacıyla kullanılır. A ***DataInstance*** öğesi temsil eder bir <xref:System.Data.DataSet> veya bir satır bir <xref:System.Data.DataTable>. Yerine *DataInstance*, öğe adı içerecektir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>. Veya değiştirilmiş olup bu biçimini bloğu geçerli verileri içerir. Bir öğe veya değiştirilmiş bir satır ile tanımlanır **diffgr:hasChanges** ek açıklama.  
  
 **\<diffgr: önce >**  
 Bu bloğu biçimini satır özgün sürümünü içerir. Öğeleri bu bloktaki öğelere eşleştirilir ***DataInstance*** kullanarak block **diffgr:id** ek açıklama.  
  
 **\<diffgr:Errors >**  
 Bu bloğu biçimini belirli bir satırda hata bilgilerini içeren ***DataInstance*** blok. Öğeleri bu bloktaki öğelere eşleştirilir ***DataInstance*** kullanarak block **diffgr:id** ek açıklama.  
  
## <a name="diffgram-annotations"></a>DiffGram ek açıklamaları  
 DiffGrams farklı satır sürümlerini veya hata bilgilerini temsil eden farklı DiffGram taşlarından öğelerini ilişkilendirmek için birkaç ek açıklamaları kullanmak <xref:System.Data.DataSet>.  
  
 Aşağıdaki tabloda açıklanmıştır DiffGram ad alanında tanımlanan DiffGram ek açıklamalar **urn: schemas-microsoft-com: XML-diffgram-v1**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**id**|Öğeleri eşleştirmiş  **\<diffgr: önce >** ve  **\<diffgr:errors >** blokları öğelere **\<** ***DataInstance*** **>** blok. İle değerleri **diffgr:id** ek açıklama biçiminde olan *[TableName] [RowIdentifier]*. Örneğin: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Hangi öğeyi tanımlayan **\<** ***DataInstance*** **>** blok, geçerli öğenin üst öğesidir. İle değerleri **diffgr:parentId** ek açıklama biçiminde olan *[TableName] [RowIdentifier]*. Örneğin: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Bir satır tanımlayan **\<** ***DataInstance*** **>** değiştirilmiş olarak engelleyin. **HasChanges** ek açıklama aşağıdaki iki değerden birine sahip olabilir:<br /><br /> **eklenen**<br /> Tanımlayan bir **eklenen** satır.<br /><br /> **Değiştiren**<br /> Tanımlayan bir **değiştirilen** içeren satır bir **özgün** satır sürümünde  **\<diffgr: önce >** blok. Unutmayın **silinmiş** satırları sahip olacak bir **özgün** satır sürümünde  **\<diffgr: önce >** blok, ancak hiçbir ek açıklamalı öğesindeolmasıbulunmaz**\<** ***DataInstance*** **>** blok.|  
|**hasErrors**|Bir satır tanımlayan **\<** ***DataInstance*** **>** ile engelleyecek bir **RowError**. Hata yerleştirilmemiş  **\<diffgr:errors >** blok.|  
|**Hata:**|Metni içeren **RowError** belirli bir öğe için  **\<diffgr:errors >** blok.|  
  
 <xref:System.Data.DataSet> Okunurken ya da bir DiffGram içeriğini yazma ilave ek açıklamaların içerir. Aşağıdaki tabloda ad uzayında tanımlanan bu ek açıklama açıklanmaktadır **urn: schemas-microsoft-schemas-msdata**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**RowOrder**|Özgün veriler satır sıralamasını korur ve belirli bir satır dizini tanımlayan <xref:System.Data.DataTable>.|  
|**Gizli**|Sahip olarak bir sütun tanımlayan bir **Columnmapping'in** özelliğini **MappingType.Hidden**. Öznitelik bir biçimde yazılmış **msdata: gizli** *[ColumnName]*= "*değer*". Örneğin: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Veri içeren, gizli sütunlarda yalnızca DiffGram özniteliği olarak yazıldığını unutmayın. Aksi takdirde, bunlar yoksayılır.|  
  
## <a name="sample-diffgram"></a>Örnek DiffGram  
 Biçimini örneği aşağıda gösterilmiştir. Değişiklikleri işlendikten önce bu örnek bir tabloda bir satır için bir güncelleştirme sonucunu gösterir. "ALFKI" satırının bir CustomerID ile değiştirilmiş, ancak güncelleştirilmez. Sonuç olarak, var olan bir **geçerli** ile satırın bir **diffgr:id** "Customers1", **\<** ***DataInstance*** **>** bloğu ve **özgün** ile satırın bir **diffgr:id** "Customers1",  **\<diffgr: önce >** blok. "ANATR" ile bir CustomerID satırını içeren bir **RowError**, ile açıklanıyor `diffgr:hasErrors="true"` ve ilgili bir öğe içinde  **\<diffgr:errors >** blok.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML Verileri Olarak DataSet İçeriği Yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
