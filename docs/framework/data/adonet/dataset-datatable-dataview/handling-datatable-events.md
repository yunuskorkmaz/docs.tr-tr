---
title: DataTable olayları işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: e6779f7d8be1cf795aeb4956b0fc257c9cb7a482
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="handling-datatable-events"></a>DataTable olayları işleme
<xref:System.Data.DataTable> Nesnesi, bir uygulama tarafından işlenen olayların bir dizi sağlar. Aşağıdaki tabloda açıklanmaktadır `DataTable` olaylar.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Sonra oluşan <xref:System.Data.DataTable.EndInit%2A> yöntemi bir `DataTable` olarak adlandırılır. Bu olay, öncelikle tasarım zamanı senaryoları desteklemek için tasarlanmıştır.|  
|<xref:System.Data.DataTable.ColumnChanged>|Bir değer olarak başarıyla değiştirildikten sonra gerçekleşir bir <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Oluşur. bir değer için gönderilen bir `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Sonra oluşan bir `DataColumn` değeri veya <xref:System.Data.DataRow.RowState%2A> , bir <xref:System.Data.DataRow> içinde `DataTable` başarıyla değiştirildi.|  
|<xref:System.Data.DataTable.RowChanging>|Bir değişiklik için gönderilen oluşur bir `DataColumn` değeri veya `RowState` , bir `DataRow` içinde `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Sonra oluşan bir `DataRow` içinde `DataTable` olarak işaretlenmiş `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Önce oluşur bir `DataRow` içinde `DataTable` olarak işaretlenmiş `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Çağrı sonra oluşan <xref:System.Data.DataTable.Clear%2A> yöntemi `DataTable` başarıyla çözüldü her `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Sonra oluşan `Clear` yöntemi önce çağrılır `Clear` işlemi başlar.|  
|<xref:System.Data.DataTable.TableNewRow>|Yeni bir sonra gerçekleşir `DataRow` yapılan bir çağrı tarafından oluşturulan `NewRow` yöntemi `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Oluşur zaman `DataTable` olan `Disposed`. Devralınan <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Ekleme veya satırları silme işlemlerinin çoğu değil Yükselt `ColumnChanged` ve `ColumnChanging` olaylar. Ancak, `ReadXml` yöntemi Yükselt `ColumnChanged` ve `ColumnChanging` olayları sürece `XmlReadMode` ayarlanır `DiffGram` veya ayarlamak `Auto` okunan XML belgesi olduğunda bir `DiffGram`.  
  
> [!WARNING]
>  Veri bozulması meydana gelebilir veri değiştirilirse bir `DataSet` içinden `RowChanged` olayı oluşturulur. Bu tür veri bozulması meydana gelirse, hiçbir özel durum gerçekleştirilecektir.  
  
## <a name="additional-related-events"></a>Ek ilgili olaylar  
 <xref:System.Data.DataTable.Constraints%2A> Özelliği ayrı tutma bir <xref:System.Data.ConstraintCollection> örneği. <xref:System.Data.ConstraintCollection> Sınıf düzenlemenizi sağlayan bir <xref:System.Data.ConstraintCollection.CollectionChanged> olay. Bu olay bir kısıtlama eklendiğinde, değiştiren veya kaldırılmasını harekete `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Özelliği ayrı tutma bir <xref:System.Data.DataColumnCollection> örneği. `DataColumnCollection` Sınıf düzenlemenizi sağlayan bir <xref:System.Data.DataColumnCollection.CollectionChanged> olay. Bu olay tetiklenen bir `DataColumn` olduğundan, eklenen, değiştirilen veya kaldırılmasını `DataColumnCollection`. Olay harekete neden değişiklikleri ad, tür, ifade veya sıralı bir sütun konumunu değişiklikleri içerir.  
  
 <xref:System.Data.DataSet.Tables%2A> Özelliği bir <xref:System.Data.DataSet> tutan bir <xref:System.Data.DataTableCollection> örneği. `DataTableCollection` Sınıfı, her ikisi de kullanıma sunan bir `CollectionChanged` ve `CollectionChanging` olay. Bu olayların ne zaman yangın bir `DataTable` eklenecek veya kaldırılmasını `DataSet`.  
  
 Değişikliklerini `DataRows` olaylarını ilişkili bir de tetikleyebilirsiniz <xref:System.Data.DataView>. `DataView` Sınıf düzenlemenizi sağlayan bir <xref:System.Data.DataView.ListChanged> tetiklenen olay bir `DataColumn` değer değişikliklerini veya görünümün birleşim ya da sıralama düzenini değiştiğinde. <xref:System.Data.DataRowView> Sınıf çıkarır bir <xref:System.Data.DataRowView.PropertyChanged> ilişkili bir zaman harekete olay `DataColumn` değer değişiklikleri.  
  
## <a name="sequence-of-operations"></a>İşlem dizisi  
 Gerçekleşen işlem dizisini İşte olduğunda bir `DataRow` eklenen, değiştirilen veya silinen:  
  
1.  Önerilen kaydı oluşturun ve değişiklikleri uygulayın.  
  
2.  İfade olmayan sütunları kısıtlamalarını denetleyin.  
  
3.  Yükselt `RowChanging` veya `RowDeleting` olayları olarak uygulanabilir.  
  
4.  Geçerli kayıt olması için önerilen kayıt ayarlayın.  
  
5.  İlişkili tüm dizinlerin güncelleştirin.  
  
6.  Yükselt `ListChanged` olaylar için ilişkili `DataView` nesneleri ve `PropertyChanged` olaylar için ilişkili `DataRowView` nesneleri.  
  
7.  Bu sütunlarda kısıtlamalar denetimi gecikme ancak tüm ifade sütunları değerlendirin.  
  
8.  Yükselt `ListChanged` olaylar için ilişkili `DataView` nesneleri ve `PropertyChanged` olaylar için ilişkili `DataRowView` ifade sütun değerlendirmeleri tarafından etkilenen nesneler.  
  
9. Yükselt `RowChanged` veya `RowDeleted` olayları olarak uygulanabilir.  
  
10. İfade sütunları kısıtlamalar denetleyin.  
  
> [!NOTE]
>  İfade sütunları değişiklikler hiçbir zaman Yükselt `DataTable` olaylar. İfade sütunları yapılan değişiklikler yalnızca Yükselt `DataView` ve `DataRowView` olaylar. İfade sütunları bağımlılıkları diğer birden çok sütuna sahip olabilir ve birden çok kez sırasında tek bir değerlendirilebilir `DataRow` işlemi. Olaylar ve tek bir her ifade değerlendirmesi başlatır `DataRow` işlemi birden çok Yükselt `ListChanged` ve `PropertyChanged` da dahil ederek aynı ifade sütunu için birden fazla olay ifade sütunları etkilenen olduğunda olayları.  
  
> [!WARNING]
>  Değil throw bir <xref:System.NullReferenceException> içinde `RowChanged` olay işleyicisi. Varsa bir <xref:System.NullReferenceException> içinde oluşturulan `RowChanged` olayı bir `DataTable`, sonra `DataTable` bozuk olur.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek olay işleyicileri oluşturma gösterilmektedir `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, ve `TableClearing` olaylar. Bunu başlatıldığında her olay işleyicisi çıkış konsol penceresinde görüntüler.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [DataAdapter Olaylarını İşleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [DataSet Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
