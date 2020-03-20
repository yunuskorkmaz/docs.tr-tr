---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: 2c521ef33c98234dac5f4b819a800cd524218462
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151162"
---
# <a name="diffgrams"></a>DiffGrams
DiffGram, veri öğelerinin geçerli ve özgün sürümlerini tanımlayan bir XML biçimidir. İçeriklerini <xref:System.Data.DataSet> yüklemek ve kalıcı hale getirmek ve içeriğini ağ bağlantısı üzerinden aktamak üzere seri hale getirmek için DiffGram biçimini kullanır. A <xref:System.Data.DataSet> DiffGram olarak yazıldığında, DiffGram'ı, **hem Özgün** hem de **Geçerli** satır sürümlerindeki sütun değerleri, satır hata bilgileri ve satır sırası dahil olmak üzere, şema <xref:System.Data.DataSet>olmasa da içeriğini doğru bir şekilde yeniden oluşturmak için gerekli tüm bilgilerle doldurur.  
  
 Bir XML Web hizmetinden a <xref:System.Data.DataSet> gönderip alırken, DiffGram biçimi örtülü olarak kullanılır. Ayrıca, **ReadXml** yöntemini <xref:System.Data.DataSet> kullanarak XML'den bir XML'in içeriğini <xref:System.Data.DataSet> yüklerken veya **WriteXml** yöntemini kullanarak XML'deki bir içeriğiyazarken, içeriğin DiffGram olarak okunup yazılmasını belirtebilirsiniz. Daha fazla bilgi için bkz: [XML'den Veri Seti Yükleme](loading-a-dataset-from-xml.md) ve [DataSet İçeriklerini XML Verisi olarak yazma.](writing-dataset-contents-as-xml-data.md)  
  
 DiffGram biçimi öncelikle .NET Framework tarafından bir <xref:System.Data.DataSet>, Microsoft SQL Server veritabanındaki tablolardaki verileri değiştirmek için DiffGrams'ı kullanarak bir serileştirme biçimi olarak kullanılır.  
  
 Diffgram, tüm tabloların içeriğini bir ** \<diffgram>** öğesine yazarak oluşturulur.  
  
### <a name="to-generate-a-diffgram"></a>Diffgram oluşturmak için  
  
1. Kök tabloların bir listesini oluşturun (diğer bir süre, üst öğesi olmayan tablolar).  
  
2. Listedeki her tablo ve onun torunları için, ilk Diffgram bölümündeki tüm satırların geçerli sürümünü yazın.  
  
3. Her tablo <xref:System.Data.DataSet>için, Diffgram önceki bölümünde, varsa tüm ** \<** satırların özgün sürümünü yazın>.  
  
4. Hataları olan satırlar için, ** \<Hata**>bölümüne hata içeriğini yazın.  
  
 Bir Diffgram, XML dosyasının başından sonuna kadar sırayla işlenir.  
  
### <a name="to-process-a-diffgram"></a>Bir Diffgram'ı işlemek için  
  
1. Satırların geçerli sürümünü içeren Diffgram'ın ilk bölümünü işleyebilir.  
  
2. Değiştirilen ve silinen satırların özgün satır sürümünü içeren ikinci veya ** \<önceki>** bölümü işleme.  
  
    > [!NOTE]
    > Bir satır silinmiş olarak işaretlenirse, silme işlemi geçerli `Cascade` <xref:System.Data.DataSet>özelliğine bağlı olarak satırın torunlarını da silebilir.  
  
3. Bölümdeki ** \<hataları>.** Bu bölümdeki her öğe için belirtilen satır ve sütunun hata bilgilerini ayarlayın.  
  
> [!NOTE]
> <xref:System.Data.XmlWriteMode> Diffgram'ı ayarlarsanız, hedefin <xref:System.Data.DataSet> ve orijinalin <xref:System.Data.DataSet> içeriği farklı olabilir.  
  
## <a name="diffgram-format"></a>DiffGram Biçimi  
 DiffGram biçimi üç bölüme ayrılmıştır: aşağıdaki örnekte gösterildiği gibi geçerli veriler, özgün (veya "önce") veriler ve hatalar bölümü.  
  
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
 Bu öğenin adı, ***DataInstance***, bu belgede açıklama amacıyla kullanılır. ***DataInstance*** öğesi bir <xref:System.Data.DataSet> satırı veya <xref:System.Data.DataTable>bir satırını temsil eder. *DataInstance*yerine, öğe <xref:System.Data.DataSet> or <xref:System.Data.DataTable>adını içerecek. DiffGram biçiminin bu bloğu, değiştirilip değiştirilmediğine bakılmaksızın geçerli verileri içerir. Değiştirilen bir öğe veya satır **diffgr:hasChanges** ek açıklama ile tanımlanır.  
  
 **\<diffgr:>önce**  
 DiffGram biçiminin bu bloğu bir satırın özgün sürümünü içerir. Bu bloktaki **öğeler, diffgr:id** ek açıklamakullanılarak ***DataInstance*** bloğundaki öğelerle eşleşir.  
  
 **\<diffgr:hatalar>**  
 DiffGram biçiminin bu ***bloğu, DataInstance*** bloğundaki belirli bir satırın hata bilgilerini içerir. Bu bloktaki **öğeler, diffgr:id** ek açıklamakullanılarak ***DataInstance*** bloğundaki öğelerle eşleşir.  
  
## <a name="diffgram-annotations"></a>DiffGram Ek Açıklamaları  
 DiffGrams farklı satır sürümleri veya hata bilgilerini temsil eden farklı DiffGram blokları <xref:System.Data.DataSet>öğeleri ilişkilendirmek için çeşitli ek açıklamalar kullanın.  
  
 Aşağıdaki tabloda DiffGram ad alanı vazosunda tanımlanan DiffGram ek açıklamaları **açıklanır:şemalar-microsoft-com:xml-diffgram-v1.**  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**Kimliği**|**\<** ve **>** ** \<diffgr:errors>** blokları ***DataInstance*** bloğundaki öğelerle **>önce diffgr:'deki öğeleri eşleştirmek için kullanılır. \<** **Diffgr:id** ek açıklamalı değerler *[TableName][RowIdentifier]* şeklindedir. Örneğin: `<Customers diffgr:id="Customers1">`.|  
|**Parentıd**|**\<** ***DataInstance*** **>** bloğundan hangi öğenin geçerli öğenin ana öğesi olduğunu tanımlar. **Diffgr:parentId** ek açıklamalı değerler *[TableName][RowIdentifier]* şeklindedir. Örneğin: `<Orders diffgr:parentId="Customers1">`.|  
|**Haschanges**|**\<** ***DataInstance*** **>** bloğundaki bir satırı değiştirilmiş olarak tanımlar. **hasChanges** ek açıklama aşağıdaki iki değerden biri olabilir:<br /><br /> **Eklenen**<br /> Bir **Ek satır** tanımlar.<br /><br /> **Değiştirilmiş**<br /> >engellemeden ** \<önce diffgr:'de** **Özgün** satır sürümü içeren **Değiştirilmiş** bir satır tanımlar. **Silinen** ** \<satırların diffgr:>** engellemeden önce **orijinal** satır sürümü olacağını, ancak ***DataInstance*** **>** bloğunda **\<** açıklamalı öğe olmayacağını unutmayın.|  
|**hasHatalar**|**\<** ***DataInstance*** **>** bloğundaki bir satırı **Satır Hatası**ile tanımlar. Hata öğesi ** \<diffgr:hatalar>** bloğuna yerleştirilir.|  
|**Hata**|** \<Diffgr:errors>** bloğundaki belirli bir öğe için **Satır Hatası** metnini içerir.|  
  
 İçeriğini <xref:System.Data.DataSet> DiffGram olarak okurken veya yazarken ek ek açıklamalar içerir. Aşağıdaki tabloda, ad alanı vazosunda tanımlanan bu ek ek ek açıklamalar **açıklanmaktadır:şemalar-microsoft-com:xml-msdata**.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**Satır Sırası**|Özgün verilerin satır sırasını korur ve belirli <xref:System.Data.DataTable>bir satırın dizinini tanımlar.|  
|**Gizli**|Bir **sütunu, MappingType.Hidden**olarak ayarlanmış bir **Sütun Eşleme** özelliğine sahip olarak tanımlar. Öznitelik msdata biçiminde **yazılır:hidden** *[ColumnName]*="*değeri*". Örneğin: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Gizli sütunların yalnızca veri içeriyorsa DiffGram özniteliği olarak yazıldığını unutmayın. Aksi takdirde, bunlar yoksayılır.|  
  
## <a name="sample-diffgram"></a>Örnek DiffGram  
 DiffGram biçiminin bir örneği aşağıda gösterilmiştir. Bu örnek, değişiklikler ayrılmadan önce bir tablodaki bir satıra güncelleştirmenin sonucunu gösterir. "ALFKI" CustomerID ile satır değiştirildi, ancak güncelleştirilmedi. Sonuç olarak, **\<** ***DataInstance*** **>** bloğunda "Müşteriler1" **diffgr:id** ve **diffgr:id** ** \<diffgr:id** ile **özgün** bir satır diffgr:id ile **>** bloğu vardır. "ANATR" customerid ile satır **rowerror**içerir, bu yüzden açıklamalı `diffgr:hasErrors="true"` ve ** \<diffgr** ilgili bir öğe var:hatalar>blok.  
  
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
