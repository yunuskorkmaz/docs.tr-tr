---
title: DiffGrams
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff43b9279130ed710d9d88cbf2ba5ead4a6f0ebc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="diffgrams"></a>DiffGrams
Bir DiffGram veri öğeleri geçerli ve özgün sürümleri tanımlayan bir XML biçimidir. <xref:System.Data.DataSet> Yükleme ve içeriği kalır ve içeriğini taşıma için bir ağ bağlantısı üzerinden serileştirmek için biçimini kullanır. Zaman bir <xref:System.Data.DataSet> yazılmış bir DiffGram doğru bir şekilde içeriği ancak şema değil, yeniden oluşturmak için gerekli tüm bilgileri DiffGram doldurur <xref:System.Data.DataSet>, hem sütun değerleri dahil olmak üzere **özgün** ve **geçerli** satır sürümleri, satır hata bilgilerini ve satır sırası.  
  
 Gönderme ve alma, bir <xref:System.Data.DataSet> bir XML Web hizmetinden biçimini örtük olarak kullanılır. Ayrıca, içeriği yüklerken bir <xref:System.Data.DataSet> XML kullanarak **ReadXml** yöntemi veya içeriği yazılırken bir <xref:System.Data.DataSet> XML kullanarak **WriteXml** yöntemi belirtebilirsiniz içeriği okumak veya DiffGram yazılmış olduğunu. Daha fazla bilgi için bkz: [bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML verileri olarak yazma DataSet içeriği](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Biçimini öncelikle .NET Framework tarafından seri hale getirme biçimi içeriği için kullanılırken bir <xref:System.Data.DataSet>, bir Microsoft SQL Server veritabanında tablolarındaki verileri değiştirmek için DiffGrams de kullanabilirsiniz.  
  
 Tüm tabloların içeriğini yazarak bir Diffgram oluşturulan bir  **\<diffgram >** öğesi.  
  
### <a name="to-generate-a-diffgram"></a>Bir Diffgram oluşturmak için  
  
1.  Kök tabloları (diğer bir deyişle, herhangi bir üst olmayan tablolar) listesini oluşturun.  
  
2.  Her bir tablo ve alt öğeleri listesinde, ilk Diffgram bölümdeki tüm satırları geçerli sürümü kullanıma yazma.  
  
3.  Her tablo için <xref:System.Data.DataSet>, varsa tüm satırları özgün sürümü yazma,  **\<önce >** Diffgram bölümü.  
  
4.  Hata, satır yazmak için içerik hata  **\<hataları >** Diffgram bölümü.  
  
 Bir Diffgram XML dosyasının başından sonuna sırada işlenir.  
  
### <a name="to-process-a-diffgram"></a>Bir Diffgram işlemek için  
  
1.  İşlem satırları geçerli sürümünü içeren Diffgram ilk bölümü.  
  
2.  İkinci işlem veya  **\<önce >** özgün satır sürümünü içeren bölüm değiştirilen ve silinen satır.  
  
    > [!NOTE]
    >  Bir satır silinmiş olarak işaretlenmişse, silme işlemi bağlı olarak sıranın alt öğeleri de silebilirsiniz `Cascade` özelliği geçerli <xref:System.Data.DataSet>.  
  
3.  İşlem  **\<hataları >** bölümü. Hata bilgileri için belirtilen satır ve sütun her öğe için bu bölümdeki ayarlayın.  
  
> [!NOTE]
>  Ayarlarsanız <xref:System.Data.XmlWriteMode> Diffgram, hedef içeriği için <xref:System.Data.DataSet> ve özgün <xref:System.Data.DataSet> farklı olabilir.  
  
## <a name="diffgram-format"></a>Biçimini  
 Biçimini üç bölümlere ayrılmıştır: geçerli verileri, özgün (veya "önce") verileri ve aşağıdaki örnekte gösterildiği gibi bir hatalar bölümü.  
  
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
  
 Biçimini veri aşağıdaki bloklarını oluşur:  
  
 **\<**  ***DataInstance***  **>**  
 Bu öğenin adını ***DataInstance***, bu belgede açıklama amacıyla kullanılır. A ***DataInstance*** öğesinin temsil ettiği bir <xref:System.Data.DataSet> veya bir satır bir <xref:System.Data.DataTable>. Yerine *DataInstance*, öğe adı içerecektir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>. Veya değiştirilmiş olup olmadığını biçimini bu bloğunu geçerli verileri içerir. Bir öğe veya değiştirilmiş olan satır ile tanımlanır **diffgr:hasChanges** ek açıklama.  
  
 **\<diffgr: önce >**  
 Bu biçimini bloğunu bir satır özgün sürümünü içerir. Bu bloğu öğelerinde öğelerine eşleştirilir ***DataInstance*** kullanarak engelleme **diffgr:id** ek açıklama.  
  
 **\<diffgr:Errors >**  
 Belirli bir satır için hata bilgilerini biçimini bu bloğunu içeren ***DataInstance*** bloğu. Bu bloğu öğelerinde öğelerine eşleştirilir ***DataInstance*** kullanarak engelleme **diffgr:id** ek açıklama.  
  
## <a name="diffgram-annotations"></a>DiffGram ek açıklamaları  
 DiffGrams farklı satır sürümleri veya hata bilgisini temsil eden farklı DiffGram taşlarından öğeleri ilişkilendirmek için birkaç ek açıklamalarını kullanma <xref:System.Data.DataSet>.  
  
 DiffGram ad alanında tanımlı DiffGram ek açıklamaları aşağıdaki tabloda açıklanmaktadır **urn: şemaları-microsoft-com: XML-diffgram-v1**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**Kimliği**|Öğeleri kullanmak üzere kullanılan  **\<diffgr: önce >** ve  **\<diffgr:errors >** öğelerine blokları  **\<**  ***DataInstance***  **>**  bloğu. İle değerleri **diffgr:id** ek açıklama biçiminde olan *[TableName] [RowIdentifier]*. Örneğin: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Hangi öğeyi tanımlayan  **\<**  ***DataInstance***  **>**  bloğu, geçerli öğenin üst öğesidir. İle değerleri **diffgr:parentId** ek açıklama biçiminde olan *[TableName] [RowIdentifier]*. Örneğin: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Bir satırda tanımlayan  **\<**  ***DataInstance***  **>**  değiştirilmiş olarak engelleyin. **HasChanges** ek açıklama aşağıdaki iki değerden biri olabilir:<br /><br /> **eklenen**<br /> Tanımlayan bir **eklenen** satır.<br /><br /> **değiştiren**<br /> Tanımlayan bir **değiştirilen** içeren satır bir **özgün** satır sürümünde  **\<diffgr: önce >** bloğu. Unutmayın **silinmiş** satırları sahip olacak bir **özgün** satır sürümünde  **\<diffgr: önce >** bloğu, ancak hiçbir ek açıklama öğesi içindeolmasıoradaolacaktır **\<**  ***DataInstance***  **>**  bloğu.|  
|**hasErrors**|Bir satırda tanımlayan  **\<**  ***DataInstance***  **>**  ile engelleme bir **RowError**. Hata yerleştirilmemiş  **\<diffgr:errors >** bloğu.|  
|**Hata:**|Metnini içeren **RowError** belirli bir öğe için  **\<diffgr:errors >** bloğu.|  
  
 <xref:System.Data.DataSet> Okunurken ya da bir DiffGram içeriğini yazma ek ek açıklamaları içerir. Aşağıdaki tabloda ad alanında tanımlı bu ek açıklama açıklanmaktadır **urn: şemaları-microsoft-com: xml-msdata**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**RowOrder**|Özgün veriler satır sırasını korur ve belirli bir satırın dizini tanımlayan <xref:System.Data.DataTable>.|  
|**Gizli**|Sahip olarak bir sütun tanımlayan bir **ColumnMapping** özelliğini **MappingType.Hidden**. Öznitelik biçiminde yazılır **msdata: gizli** *[ColumnName]*= "*değeri*". Örneğin: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Veri içeriyorsa, gizli sütunlar yalnızca DiffGram özniteliği olarak yazıldığını unutmayın. Aksi takdirde, bunlar yoksayılır.|  
  
## <a name="sample-diffgram"></a>Örnek DiffGram  
 Biçimini örneği aşağıda verilmiştir. Değişiklikler kaydedildi önce bu örnek bir tablodaki bir satır için bir güncelleştirme sonucunu gösterir. "ALFKI" ile bir CustomerID satırının değiştirildi, ancak güncelleştirilmez. Sonuç olarak, var olan bir **geçerli** ile satırın bir **diffgr:id** "Customers1",  **\<**  ***DataInstance***  **>**  bloğu ve bir **özgün** ile satırın bir **diffgr:id** "Customers1",  **\<diffgr: önce >**bloğu. "ANATR" ile bir CustomerID satırının içeren bir **RowError**, ile açıklanan şekilde `diffgr:hasErrors="true"` ve ilgili öğesinde  **\<diffgr:errors >** bloğu.  
  
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
 [Bir veri kümesini XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Bir veri kümesini XML dosyası şuradan yükleniyor](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML verileri olarak DataSet içeriğini yazma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
