---
title: DataTable olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: ef9fcd31253283248dfe773ac4dde4fcbb358a2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660989"
---
# <a name="handling-datatable-events"></a>DataTable olaylarını işleme
<xref:System.Data.DataTable> Nesnesi, bir uygulama tarafından işlenebilen bir olay serisi olarak sağlar. Aşağıdaki tabloda açıklanmıştır `DataTable` olayları.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Sonra oluşan <xref:System.Data.DataTable.EndInit%2A> yöntemi bir `DataTable` çağrılır. Bu olay, öncelikle tasarım zamanı senaryoları desteklemek üzere tasarlanmıştır.|  
|<xref:System.Data.DataTable.ColumnChanged>|Bir değer olarak başarıyla değiştirildikten sonra gerçekleşir bir <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|İçin bir değer gönderildi oluşur bir `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Sonra oluşan bir `DataColumn` değeri veya <xref:System.Data.DataRow.RowState%2A> , bir <xref:System.Data.DataRow> içinde `DataTable` başarıyla değiştirildi.|  
|<xref:System.Data.DataTable.RowChanging>|İçin bir değişiklik gönderildiğinde gerçekleşir bir `DataColumn` değeri veya `RowState` , bir `DataRow` içinde `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Sonra oluşan bir `DataRow` içinde `DataTable` işaretlendi `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Öncesinde gerçekleşir bir `DataRow` içinde `DataTable` olarak işaretlenmiş `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Çağrısı yapıldıktan sonra gerçekleşir <xref:System.Data.DataTable.Clear%2A> yöntemi `DataTable` başarıyla çözüldü her `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Sonra oluşan `Clear` yöntemi önce çağrılır `Clear` işlemi başlar.|  
|<xref:System.Data.DataTable.TableNewRow>|Yeni bir sonra gerçekleşir `DataRow` bir çağrı tarafından oluşturulan `NewRow` yöntemi `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Gerçekleşir, `DataTable` olduğu `Disposed`. Devralınan <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Ekleme veya satırları silmek işlemlerinin çoğu değil yükseltmek `ColumnChanged` ve `ColumnChanging` olayları. Ancak, `ReadXml` başlatma yöntemi `ColumnChanged` ve `ColumnChanging` olayları sürece `XmlReadMode` ayarlanır `DiffGram` veya `Auto` okunan XML belgesi olduğunda bir `DiffGram`.  
  
> [!WARNING]
>  Veri bozulması meydana gelebilir veri değiştirilirse bir `DataSet` içinden `RowChanged` olayı oluşturulur. Bu tür veri bozulması meydana gelirse hiçbir özel durum oluşturulur.  
  
## <a name="additional-related-events"></a>Ek ilgili olaylar  
 <xref:System.Data.DataTable.Constraints%2A> Özelliği içeren bir <xref:System.Data.ConstraintCollection> örneği. <xref:System.Data.ConstraintCollection> Sınıfı kullanıma sunan bir <xref:System.Data.ConstraintCollection.CollectionChanged> olay. Kısıtlama eklendiğinde, değiştirildiğinde veya kaldırıldığında, bu olay harekete `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Özelliği içeren bir <xref:System.Data.DataColumnCollection> örneği. `DataColumnCollection` Sınıfı kullanıma sunan bir <xref:System.Data.DataColumnCollection.CollectionChanged> olay. Bu olay tetiklenen bir `DataColumn` eklendiğinde, değiştirildiğinde veya kaldırıldığında `DataColumnCollection`. Olayın ateşlenmesine neden olan değişiklikleri, ad, tür, ifade veya sıralı bir sütun konumunu değişiklikleri içerir.  
  
 <xref:System.Data.DataSet.Tables%2A> Özelliği bir <xref:System.Data.DataSet> tutan bir <xref:System.Data.DataTableCollection> örneği. `DataTableCollection` Sınıfı gösterir hem de bir `CollectionChanged` ve `CollectionChanging` olay. Bu olaylar olduğunda harekete bir `DataTable` eklendiğinde veya kaldırıldığında `DataSet`.  
  
 Değişikliklerini `DataRows` Ayrıca ilişkili olayları tetikleyebilir <xref:System.Data.DataView>. `DataView` Sınıfı kullanıma sunan bir <xref:System.Data.DataView.ListChanged> tetiklenen olayı bir `DataColumn` değer değişiklikleri ya da görünümün oluşturma veya sıralama düzeni değiştiğinde. <xref:System.Data.DataRowView> Sınıfı kullanıma sunan bir <xref:System.Data.DataRowView.PropertyChanged> ilişkili bir kıldığında tetikler olay `DataColumn` değişiklikleri değeri.  
  
## <a name="sequence-of-operations"></a>İşlem dizisi  
 Ortaya çıkan işlemlerin sırasını İşte olduğunda bir `DataRow` eklenen, değiştirilecek veya silinecek:  
  
1.  Önerilen kayıt oluşturmak ve değişiklikleri uygulayın.  
  
2.  Denetim kısıtlamaları ifade olmayan sütunları için.  
  
3.  Raise `RowChanging` veya `RowDeleting` olaylar olarak uygulanabilir.  
  
4.  Önerilen kayıt geçerli kayıt olacak şekilde ayarlayın.  
  
5.  İlişkili tüm dizinlerin güncelleştirin.  
  
6.  Raise `ListChanged` olayları ilişkili `DataView` nesneleri ve `PropertyChanged` olayları ilişkili `DataRowView` nesneleri.  
  
7.  Ancak bu sütunlarda kısıtlama denetimi gecikme tüm ifade sütunları değerlendirin.  
  
8.  Raise `ListChanged` olayları ilişkili `DataView` nesneleri ve `PropertyChanged` olayları ilişkili `DataRowView` ifade sütunu değerlendirmeleri tarafından etkilenen nesneler.  
  
9. Raise `RowChanged` veya `RowDeleted` olaylar olarak uygulanabilir.  
  
10. İfade sütunları kısıtlamalar kontrol edin.  
  
> [!NOTE]
>  İfade sütunları değişiklikler hiçbir zaman yükseltmek `DataTable` olayları. İfade sütunları değişiklikler yalnızca yükseltmek `DataView` ve `DataRowView` olayları. İfade sütunları bağımlılıkları diğer birden çok sütuna sahip olabilir ve tek bir sırasında birden çok kez değerlendirilebilir `DataRow` işlemi. Olayları ve tek bir her ifade değerlendirmesi başlatır `DataRow` işlemi birden çok yükseltmek `ListChanged` ve `PropertyChanged` ifade sütunları etkilendiğinde büyük olasılıkla aynı ifade sütunu için birden çok olayı dahil olmak üzere olayları.  
  
> [!WARNING]
>  Throw değil bir <xref:System.NullReferenceException> içinde `RowChanged` olay işleyicisi. Varsa bir <xref:System.NullReferenceException> içinde oluşturulan `RowChanged` olayı bir `DataTable`, ardından `DataTable` bozulacaktır.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, için olay işleyicilerini oluşturma gösterilmektedir `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, ve `TableClearing` olayları. Bu başlatıldığında her olay işleyicisi çıkış konsol penceresinde görüntüler.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [DataAdapter Olaylarını İşleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [DataSet Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
