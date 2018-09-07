---
title: DataTable kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: fa70af311d6b4fa4e17bb3ba6110e4cea420c34c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079496"
---
# <a name="datatable-constraints"></a>DataTable kısıtlamaları
Kısıtlamaları verileri kısıtlamalarını uygulamak için kullanabileceğiniz bir <xref:System.Data.DataTable>, veri bütünlüğünü korumak için. Bir sınırlamadır uygulanan otomatik bir kural, bir sütun veya ilgili sütunlar için belirleyen kursu eyleminin bir satırın değerini şekilde değiştirildiğinde. Kısıtlamaları zorunlu olduğunda `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> olduğu **true**. Nasıl ayarlanacağı gösteren kod örneği için `EnforceConstraints` özelliği bkz <xref:System.Data.DataSet.EnforceConstraints%2A> başvuru konusu.  
  
 ADO.NET'te kısıtlamaları iki tür vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint>. Ekleyerek en az iki tablo arasında bir ilişki oluşturduğunuzda varsayılan olarak, her iki kısıtlamalar otomatik olarak oluşturulan bir <xref:System.Data.DataRelation> için **veri kümesi**. Ancak, bu davranışı belirtilerek devre dışı bırakabilirsiniz **createConstraints** = **false** ilişki oluştururken.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint** hakkında güncelleştirme ve silme ilişkili tablolar için nasıl yayılır kuralları zorunlu kılar. Örneğin, bir değer, bir tablonun satır güncelleştirilemiyor veya silinemiyor ve aynı değeri de birinde kullanılır veya tabloları, ilgili daha fazla bir **ForeignKeyConstraint** ilişkili tabloların ne olacağını belirler.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> özelliklerini **ForeignKeyConstraint** silin veya ilgili bir tabloda bir satırı güncelleştirmek kullanıcının çalışır olduğunda gerçekleştirilecek eylem tanımlayın. Aşağıdaki tablo kullanılabilecek farklı ayarlar açıklanır **DeleteRule** ve **UpdateRule** özelliklerini **ForeignKeyConstraint**.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Basamakla**|Silin veya ilişkili satırları güncelleştirin.|  
|**SetNull**|İlişkili satırların değerleri ayarlayın **DBNull**.|  
|**SetDefault**|Değerleri ilişkili satırları için varsayılan değer olarak ayarlayın.|  
|**Yok**|İlgili satır eylem yok. Bu varsayılandır.|  
  
 A **ForeignKeyConstraint** yaymak olarak değişiklikleriyle ilgili sütunları, kısıtlayabilirsiniz. Özellikleri için bağlı olarak **ForeignKeyConstraint** bir sütunun varsa **EnforceConstraints** özelliği **veri kümesi** olduğu **true**, belirli işlemleri üst satırda bir özel durum neden olur. Örneğin, varsa **DeleteRule** özelliği **ForeignKeyConstraint** olduğu **hiçbiri**, herhangi bir alt satır varsa, bir üst satır silinemiyor.  
  
 Bir yabancı anahtar kısıtlaması bir dizi kullanarak sütunları arasında veya tek bir sütun oluşturabilirsiniz **ForeignKeyConstraint** Oluşturucusu. Ortaya çıkan geçirmek **ForeignKeyConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** özelliğinin bir **ConstraintCollection**. Oluşturucu bağımsız ilişkin çeşitli aşırı yükler için de geçirebilirsiniz **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **ForeignKeyConstraint**.  
  
 Oluştururken bir **ForeignKeyConstraint**, geçirebilirsiniz **DeleteRule** ve **UpdateRule** değerleri oluşturucusu için bağımsız değişkenler veya olarak ayarlayabilirsiniz gibi özellikleri Örnek (burada **DeleteRule** değeri ayarı **hiçbiri**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 Satırlara değişiklikler kullanarak kabul edilen **AcceptChanges** yöntemi veya iptal edilmiş kullanarak **RejectChanges** yöntemi **veri kümesi**, **DataTable**, veya **DataRow**. Olduğunda bir **veri kümesi** içeren **sağlayan**, çağrılıyor **AcceptChanges** veya **RejectChanges** yöntemleriniuygular **AcceptRejectRule**. **AcceptRejectRule** özelliği **ForeignKeyConstraint** alt gerçekleştirilecek eylemi belirler ne zaman satırları **AcceptChanges** veya  **RejectChanges** üst satırda çağrılır.  
  
 Aşağıdaki tabloda kullanılabilir ayarlarını listeler **AcceptRejectRule**.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Basamakla**|Veya alt satırlara değişiklikler reddedebilirsiniz.|  
|**Yok**|Alt satırlar üzerinde eylem yok. Bu varsayılandır.|  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, oluşturur bir <xref:System.Data.ForeignKeyConstraint>, birkaç dahil olmak üzere özellikleri ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>ve bu gruba ekler <xref:System.Data.ConstraintCollection> , bir <xref:System.Data.DataTable> nesne.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** tek bir sütun veya sütun bir dizi atanan nesne, bir **DataTable**, tüm verilerini belirtilen sütun veya sütunlar satır benzersiz olmasını sağlar. Bir sütun veya sütun dizisi için benzersiz bir Kısıt kullanarak oluşturabileceğiniz **UniqueConstraint** Oluşturucusu. Ortaya çıkan geçirmek **UniqueConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** özelliğinin bir **ConstraintCollection**. Oluşturucu bağımsız ilişkin çeşitli aşırı yükler için de geçirebilirsiniz **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **UniqueConstraint**. Oluştururken bir **UniqueConstraint** bir sütun veya sütunlar için isteğe bağlı olarak bir birincil anahtar sütun veya sütunlar olup olmadığını belirtebilirsiniz.  
  
 Ayarlayarak bir sütun için benzersiz bir Kısıt oluşturabilirsiniz **benzersiz** sütununun özellik **true**. Alternatif olarak, ayarı **benzersiz** özelliğini tek bir sütuna **false** oluşabilecek herhangi bir benzersiz kısıtlamayı kaldırır. Bir sütun veya sütunlar bir tablo için birincil anahtar olarak tanımlayan benzersiz bir kısıtlaması belirtilen sütun veya sütunlar için otomatik olarak oluşturur. Bir sütun kaldırırsanız **PrimaryKey** özelliği bir **DataTable**, **UniqueConstraint** kaldırılır.  
  
 Aşağıdaki örnek, oluşturur bir **UniqueConstraint** iki sütunu için bir **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
