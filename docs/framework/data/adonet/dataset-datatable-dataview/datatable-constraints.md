---
title: "DataTable kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 500dad1699843bae04aea6d5c16a1ccf53bb102a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-constraints"></a>DataTable kısıtlamaları
Kısıtlamaları verileri kısıtlamalar uygulamak için kullanabileceğiniz bir <xref:System.Data.DataTable>, veri bütünlüğünü korumak için. Uygulanan bir otomatik kuralı bir kısıtlamadır bir sütun veya ilgili sütunları için belirleyen eylem seyri bir satır değerinin şekilde değiştirildiğinde. Kısıtlamaları zorlanmaz zaman `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> olan **doğru**. Nasıl ayarlanacağı gösteren kod örneği için `EnforceConstraints` özelliği, bkz: <xref:System.Data.DataSet.EnforceConstraints%2A> başvuru konusu.  
  
 ADO.NET kısıtlamalarını iki tür vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint>. Ekleyerek en az iki tablo arasında bir ilişki oluşturduğunuzda varsayılan olarak, her iki kısıtlamaları otomatik olarak oluşturulmuş bir <xref:System.Data.DataRelation> için **DataSet**. Ancak, bu davranış belirterek devre dışı bırakabilirsiniz **createConstraints** = **false** ilişki oluştururken.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint** kuralları güncelleştirmeleri ve silme ilişkili tablolar için nasıl yayılır hakkında zorlar. Bir tablo satırının değerinde güncelleştirilmiş ya da silinmiş, aynı değeri de birinde kullanılır ve tablolar, ilgili daha fazla örneğin, bir **ForeignKeyConstraint** ne ilişkili tabloları olacağını belirler.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> Ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> özelliklerini **ForeignKeyConstraint** kullanıcı silin veya ilişkili bir tabloda bir satırı güncelleştirme girişiminde olduğunda gerçekleştirilecek eylem tanımlayın. Aşağıdaki tabloda kullanılabilir için farklı ayarlar açıklanır **DeleteRule** ve **UpdateRule** özelliklerini **ForeignKeyConstraint**.  
  
|Kuralı ayarı|Açıklama|  
|------------------|-----------------|  
|**CASCADE**|Silin veya ilişkili satırları güncelleştirin.|  
|**SetNull**|İlişkili satırların değerlerini ayarlayabilirsiniz **DBNull**.|  
|**SetDefault**|Varsayılan değer ilişkili satırların değerlerini ayarlayın.|  
|**Yok**|İlgili satırlarda eylem yok. Bu varsayılandır.|  
  
 A **ForeignKeyConstraint** kısıtlayabilirsiniz, yanı sıra yayılması, değişiklikler ilgili sütun. Özellikleri için ayarlanmış bağlı olarak **ForeignKeyConstraint** bir sütunun varsa **EnforceConstraints** özelliği **DataSet** olan **true**, belirli işlemleri üst satırda bir özel durum oluşur. Örneğin, varsa **DeleteRule** özelliği **ForeignKeyConstraint** olan **hiçbiri**, herhangi bir alt satır varsa, bir üst satır silinemiyor.  
  
 Bir yabancı anahtar kısıtlaması tek sütun veya sütunlar kullanarak bir dizi arasında oluşturabilirsiniz **ForeignKeyConstraint** Oluşturucusu. Elde edilen geçirmek **ForeignKeyConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** olan özellik bir **ConstraintCollection**. Oluşturucu bağımsız değişkenleri için birkaç aşırı geçebilen **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **ForeignKeyConstraint**.  
  
 Oluştururken bir **ForeignKeyConstraint**, geçirebilirsiniz **DeleteRule** ve **UpdateRule** oluşturucuya değerleri bağımsız değişken veya olarak ayarlayabilirsiniz özellikleri olarak olarak Örnek (burada **DeleteRule** değeri ayarı **hiçbiri**).  
  
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
 Satır değişiklikleri kullanarak kabul edilen **AcceptChanges** yöntemi veya iptal edilen kullanarak **RejectChanges** yöntemi **DataSet**, **DataTable**, veya **DataRow**. Zaman bir **DataSet** içeren **sağlayan**, çağıran **AcceptChanges** veya **RejectChanges** yöntemleri zorlar **AcceptRejectRule**. **AcceptRejectRule** özelliği **ForeignKeyConstraint** alt gerçekleştirilecek eylemi belirler ne zaman satırları **AcceptChanges** veya  **RejectChanges** üst satırındaki adı verilir.  
  
 Aşağıdaki tabloda kullanılabilir ayarlarını listeler **AcceptRejectRule**.  
  
|Kuralı ayarı|Açıklama|  
|------------------|-----------------|  
|**CASCADE**|Kabul edin veya alt satır reddedebilirsiniz.|  
|**Yok**|Alt satırlarda eylem yok. Bu varsayılandır.|  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Data.ForeignKeyConstraint>, özelliklerini de dahil olmak üzere çeşitli ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>ve ona ekler <xref:System.Data.ConstraintCollection> , bir <xref:System.Data.DataTable> nesnesi.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** tek bir sütun veya sütun bir dizi atanabilir nesnesi bir **DataTable**, belirtilen sütun veya sütunlar tüm verileri satır benzersiz olmasını sağlar. Kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz **UniqueConstraint** Oluşturucusu. Elde edilen geçirmek **UniqueConstraint** nesnesini **Ekle** tablonun yöntemi **kısıtlamaları** olan özellik bir **ConstraintCollection**. Oluşturucu bağımsız değişkenleri için birkaç aşırı geçebilen **Ekle** yöntemi bir **ConstraintCollection** oluşturmak için bir **UniqueConstraint**. Oluştururken bir **UniqueConstraint** bir sütun veya sütunlar için isteğe bağlı olarak sütun veya sütunlar birincil bir anahtar olup olmadığını belirtebilirsiniz.  
  
 Ayarlayarak bir sütun için benzersiz bir kısıtlama oluşturabilirsiniz **benzersiz** sütuna özelliğinin **doğru**. Alternatif olarak, ayarı **benzersiz** tek bir sütun özelliğinin **false** bulunabilecek herhangi benzersiz kısıtlamayı kaldırır. Bir tablonun birincil anahtarı olarak bir sütun veya sütunlar tanımlama belirtilen sütun veya sütunlar için benzersiz bir kısıtlama otomatik olarak oluşturur. Bir sütun kaldırırsanız **PrimaryKey** özelliği bir **DataTable**, **UniqueConstraint** kaldırılır.  
  
 Aşağıdaki örnekte bir **UniqueConstraint** iki sütunu için bir **DataTable**.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
