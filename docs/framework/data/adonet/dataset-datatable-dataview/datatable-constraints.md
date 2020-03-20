---
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151292"
---
# <a name="datatable-constraints"></a>DataTable Kısıtlamaları
Verilerin bütünlüğünü korumak için, bir 'deki <xref:System.Data.DataTable>veriler üzerindeki kısıtlamaları zorlamak için kısıtlamalar kullanabilirsiniz. Kısıtlama, bir satırın değeri bir şekilde değiştirildiğinde eylem seyrini belirleyen bir sütuna veya ilgili sütunlara uygulanan otomatik bir kuraldır. Kısıtlamalar, `System.Data.DataSet.EnforceConstraints` özelliği <xref:System.Data.DataSet> **doğru**olduğunda uygulanır. `EnforceConstraints` Özelliğin nasıl ayarlandığını gösteren bir kod <xref:System.Data.DataSet.EnforceConstraints%2A> örneği için başvuru konusuna bakın.  
  
 ADO.NET'da iki tür kısıtlama vardır: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>ve . Varsayılan olarak, <xref:System.Data.DataRelation> **DataSet'e**bir tane ekleyerek iki veya daha fazla tablo arasında ilişki oluşturduğunuzda her iki kısıtlama da otomatik olarak oluşturulur. Ancak, ilişki oluştururken **createConstraints** = **yanlış** belirterek bu davranışı devre dışı bırakabilirsiniz.  
  
## <a name="foreignkeyconstraint"></a>Foreignkeyconstraint  
 **ForeignKeyConstraint,** ilgili tablolara güncelleştirmelerin ve silmelerin nasıl yayLılacak olduğuna ilişkin kurallar uygular. Örneğin, bir tablonun satırındaki bir değer güncelleştirilir veya silinirse ve aynı değer bir veya daha fazla ilgili tabloda da kullanılırsa, ilgili tablolarda neler olacağını **ForeignKeyConstraint** belirler.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> **ForeignKeyConstraint'in** özellikleri ve özellikleri, kullanıcı ilgili tablodaki bir satırı silmeye veya güncelleştirmeye çalıştığında yapılacak eylemi tanımlar. Aşağıdaki tabloda **ForeignKeyConstraint'in** **DeleteRule** ve **UpdateRule** özellikleri için kullanılabilen farklı ayarlar açıklanmaktadır.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Cascade**|İlgili satırları silin veya güncelleyin.|  
|**Setnull**|İlgili satırlarda değerleri **DBNull'a**ayarlayın.|  
|**Setdefault**|İlgili satırlarda değerleri varsayılan değere ayarlayın.|  
|**Yok**|İlgili satırlarda hiçbir işlem de bulunmayın. Bu varsayılandır.|  
  
 **ForeignKeyConstraint,** ilgili sütundeğişiklikleri kısıtlamanın yanı sıra çoğaltabilir. Bir sütunun **ForeignKeyConstraint** için ayarlanan özelliklerine bağlı olarak, **DataSet'in** **EnforceConstraints** özelliği **doğruysa,** ana satırda belirli işlemler gerçekleştirmek bir özel durumla sonuçlanır. Örneğin, **ForeignKeyConstraint'in** **DeleteRule** özelliği **Yok**ise, alt satırı varsa bir üst satır silinemez.  
  
 **ForeignKeyConstraint** oluşturucusunu kullanarak tek sütunlar arasında veya bir dizi sütun arasında yabancı anahtar kısıtlaması oluşturabilirsiniz. Ortaya çıkan **ForeignKeyConstraint** nesnesini, bir **ConstraintCollection**olan tablonun **Kısıtlamalar** özelliğinin **Ekle** yöntemine geçirin. Ayrıca, bir **ForeignKeyConstraint**oluşturmak için **constraintcollection'ın Ekle** yönteminin birkaç aşırı yüklemesine oluşturucu bağımsız değişkenler geçirebilirsiniz. **ConstraintCollection**  
  
 **ForeignKeyConstraint**oluştururken, **DeleteRule** ve **UpdateRule** değerlerini bağımsız değişken olarak oluşturucuya geçirebilir veya bunları aşağıdaki örnekte olduğu gibi **(DeleteRule** değerinin **None**olarak ayarlandığı) özellikleri olarak ayarlayabilirsiniz.  
  
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
 Satırdeğişiklikleri **AcceptChanges** yöntemi kullanılarak kabul edilebilir veya **DataSet,** **DataTable**veya **DataRow'un** **Reddet** değişiklikleri yöntemi kullanılarak iptal edilebilir. Bir **DataSet** **ForeignKeyConstraints**içeriyorsa , **AcceptChanges** veya **RejectChanges** yöntemlerini çağırarak **AcceptRejectRule'i**zorlar. **ForeignKeyConstraint'in** **AcceptRejectRule** özelliği, üst satırda **Değişiklikleri Kabul** veya **Reddet** çağrıldığında alt satırlarda hangi eylemin alınacağını belirler.  
  
 Aşağıdaki tabloda **AcceptRejectRule**için kullanılabilir ayarlar listelenir.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Cascade**|Alt satırlarda yapılan değişiklikleri kabul edin veya reddedin.|  
|**Yok**|Alt satırlar üzerinde hiçbir işlem de bulunmayın. Bu varsayılandır.|  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, özellikleri, dahil olmak üzere birkaç tane <xref:System.Data.ConstraintCollection> ayarlar <xref:System.Data.DataTable> ve bir nesnenin ekler.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>Uniqueconstraint  
 Tek bir sütuna veya **DataTable'daki**bir sütun dizisine atanabilen **Benzersiz Kısıtlama** nesnesi, belirtilen sütun veya sütunlarda bulunan tüm verilerin satır başına benzersiz olmasını sağlar. **UniqueConstraint** oluşturucusunu kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz. Ortaya çıkan **UniqueConstraint** nesnesini, bir **ConstraintCollection**olan tablonun **Kısıtlamalar** özelliğinin **Ekle** yöntemine geçirin. Ayrıca, **bir UniqueConstraint**oluşturmak için **constraintcollection'ın** **Ekle** yönteminin birkaç aşırı yüklemesine oluşturucu bağımsız değişkenler geçirebilirsiniz. Bir sütun veya sütun için **Benzersiz Kısıtlama** oluştururken, isteğe bağlı olarak sütun veya sütunların birincil anahtar olup olmadığını belirtebilirsiniz.  
  
 Ayrıca, sütunun **Benzersiz** özelliğini **doğru**olarak ayarlayarak sütun için benzersiz bir kısıtlama da oluşturabilirsiniz. Alternatif olarak, tek bir sütunun **Benzersiz** özelliğini **false** olarak ayarlamak, var olabilecek benzersiz kısıtlamaları kaldırır. Bir sütun veya sütunu tabloiçin birincil anahtar olarak tanımlamak, belirtilen sütun veya sütunlar için otomatik olarak benzersiz bir kısıtlama oluşturur. **Bir sütunu DataTable'ın** **PrimaryKey** özelliğinden kaldırırsanız, **UniqueConstraint** kaldırılır.  
  
 Aşağıdaki örnek, Bir **DataTable'ın**iki sütunu için **Benzersiz Kısıtlama** oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [DataTable Şema Tanımı](datatable-schema-definition.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
