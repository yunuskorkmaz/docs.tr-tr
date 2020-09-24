---
title: DataTable Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 1224518a9a16f48f770b6839317b9787da97377b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153280"
---
# <a name="datatable-constraints"></a>DataTable Kısıtlamaları

Verilerin bütünlüğünü sağlamak için, bir içindeki veriler üzerinde kısıtlama zorlamak üzere kısıtlamaları kullanabilirsiniz <xref:System.Data.DataTable> . Kısıtlama bir sütuna veya ilgili sütunlara uygulanan bir otomatik kuraldır ve bir satırın değeri bir değer değiştiğinde eylem kursu belirler. Özelliği true olduğunda kısıtlamalar uygulanır `System.Data.DataSet.EnforceConstraints` <xref:System.Data.DataSet> . **true** Özelliği ayarlamayı gösteren bir kod örneği için `EnforceConstraints` bkz <xref:System.Data.DataSet.EnforceConstraints%2A> . başvuru konusu.  
  
 ADO.NET içinde iki tür kısıtlama vardır: <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> . Varsayılan olarak, <xref:System.Data.DataRelation> **veri kümesine**bir ekleyerek iki veya daha fazla tablo arasında bir ilişki oluşturduğunuzda her iki kısıtlama otomatik olarak oluşturulur. Ancak, ilişki oluştururken yanlış **createkısıtlamalarını**belirterek bu davranışı devre dışı bırakabilirsiniz  =  **false** .  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  

 Bir **ForeignKeyConstraint** , ilgili tablolarda güncelleştirmelerin ve silinme işlemlerinin nasıl yayıldığı hakkında kurallara zorlar. Örneğin, bir tablonun bir satırındaki bir değer güncellenir veya silinirse ve aynı değer aynı zamanda bir veya daha fazla ilişkili tabloda kullanılıyorsa, **ForeignKeyConstraint** ilişkili tablolarda ne olduğunu belirler.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>ForeignKeyConstraint ve <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> Özellikleri, Kullanıcı **ForeignKeyConstraint** ilgili tablodaki bir satırı silmeye veya güncelleştirmeye çalıştığında gerçekleştirilecek eylemi tanımlar. Aşağıdaki tabloda, **ForeignKeyConstraint**'In **DeleteRule** ve **UpdateRule** özellikleri için kullanılabilen farklı ayarlar açıklanmaktadır.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Seçilemez**|İlişkili satırları silin veya güncelleştirin.|  
|**SetNull**|İlgili satırlardaki değerleri **DBNull**olarak ayarlayın.|  
|**SetDefault**|İlgili satırlardaki değerleri varsayılan değere ayarlayın.|  
|**Hiçbiri**|İlgili satırlarda hiçbir işlem yapın. Bu varsayılan seçenektir.|  
  
 Bir **ForeignKeyConstraint** , ilişkili sütunlardaki değişiklikleri kısıtlayabilir ve yayabilir. Bir sütunun **ForeignKeyConstraint** için ayarlanan özelliklere bağlı olarak, **veri kümesinin** **enforcekısıtlamalar** özelliği **true**ise, üst satırda belirli işlemleri gerçekleştirmek bir özel durumla sonuçlanır. Örneğin, **ForeignKeyConstraint** 'In **DeleteRule** özelliği **none**ise, bir üst satır alt satırları varsa silinemez.  
  
 **ForeignKeyConstraint** oluşturucusunu kullanarak, tek sütunlar arasında veya bir sütun dizisi arasında yabancı anahtar kısıtlaması oluşturabilirsiniz. Elde edilen **ForeignKeyConstraint** nesnesini tablonun **kısıtlamalar** özelliğinin **Add** yöntemine geçirin, bu bir **ConstraintCollection**. Ayrıca, bir **ForeignKeyConstraint**oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz.  
  
 Bir **ForeignKeyConstraint**oluştururken, **DeleteRule** ve **UpdateRule** değerlerini bağımsız değişken olarak oluşturucuya geçirebilir ya da aşağıdaki örnekte olduğu gibi bunları özellikler olarak ayarlayabilirsiniz (burada **DeleteRule** değeri **none**olarak ayarlanır).  
  
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

 Satırlarda yapılan değişiklikler **AcceptChanges** yöntemi kullanılarak kabul edilebilir veya **DataSet**, **DataTable**veya **DataRow**' ın **RejectChanges** yöntemi kullanılarak iptal edilebilir. Bir **veri kümesi** **ForeignKeyConstraints**Içerdiğinde, **AcceptChanges** veya **RejectChanges** yöntemlerini çağırmak **AcceptRejectRule**'yi zorlar. **ForeignKeyConstraint** 'ın **AcceptRejectRule** özelliği, üst satırda **AcceptChanges** veya **RejectChanges** çağrıldığında alt satırlarda hangi eylemin alınacağını belirler.  
  
 Aşağıdaki tabloda, **AcceptRejectRule**için kullanılabilir ayarlar listelenmektedir.  
  
|Kural ayarı|Açıklama|  
|------------------|-----------------|  
|**Seçilemez**|Alt satırlardaki değişiklikleri kabul edin veya reddedin.|  
|**Hiçbiri**|Alt satırlarda hiçbir işlem yapın. Bu varsayılan seçenektir.|  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek bir oluşturur, ve <xref:System.Data.ForeignKeyConstraint> dahil olmak üzere bazı özelliklerini ayarlar <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A> ve <xref:System.Data.ConstraintCollection> bir nesnesinin öğesine ekler <xref:System.Data.DataTable> .  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint kısıtlaması  

 Tek bir sütuna veya bir **DataTable**içindeki bir sütun dizisine atanabilecek **UniqueConstraint** nesnesi, belirtilen sütundaki veya sütunlardaki tüm verilerin her satır için benzersiz olmasını sağlar. **UniqueConstraint** oluşturucuyu kullanarak bir sütun veya sütun dizisi için benzersiz bir kısıtlama oluşturabilirsiniz. Elde edilen **UniqueConstraint** nesnesini, **ConstraintCollection**olan tablonun **kısıtlamalar** özelliğinin **Add** metoduna geçirin. Ayrıca, bir **UniqueConstraint kısıtlaması**oluşturmak için, Oluşturucu bağımsız değişkenlerini bir **ConstraintCollection** **Add** yönteminin çeşitli aşırı yüküne geçirebilirsiniz. Bir sütun veya sütun için bir **UniqueConstraint kısıtlaması** oluştururken, isteğe bağlı olarak sütun veya sütunların birincil anahtar olup olmadığını belirtebilirsiniz.  
  
 Ayrıca, sütunun **Unique** özelliğini **true**olarak ayarlayarak bir sütun için benzersiz bir kısıtlama oluşturabilirsiniz. Alternatif olarak, tek bir sütunun **Unique** özelliğinin **false** olarak ayarlanması, var olabilecek herhangi bir benzersiz kısıtlamayı kaldırır. Bir tablo için birincil anahtar olarak bir sütun veya sütun tanımlamak, belirtilen sütun veya sütunlar için otomatik olarak benzersiz bir kısıtlama oluşturur. **DataTable**'ın **PrimaryKey** özelliğinden bir sütunu kaldırırsanız, **UniqueConstraint kısıtlaması** kaldırılır.  
  
 Aşağıdaki örnek, bir **DataTable**'ın iki sütunu Için bir **UniqueConstraint kısıtlaması** oluşturur.  
  
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
