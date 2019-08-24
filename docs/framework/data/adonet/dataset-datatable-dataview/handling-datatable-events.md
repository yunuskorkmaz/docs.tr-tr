---
title: DataTable Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 210d15187cd539cdae6e38fdcb708b4b9f81c073
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988303"
---
# <a name="handling-datatable-events"></a>DataTable Olaylarını İşleme
Nesnesi <xref:System.Data.DataTable> , bir uygulama tarafından işlenebilmesi için bir dizi olay sağlar. Aşağıdaki tabloda olayları açıklanmaktadır `DataTable` .  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Bir a <xref:System.Data.DataTable.EndInit%2A> `DataTable` yöntemi çağrıldıktan sonra gerçekleşir. Bu olay öncelikle tasarım zamanı senaryolarını desteklemeye yöneliktir.|  
|<xref:System.Data.DataTable.ColumnChanged>|Bir değer bir <xref:System.Data.DataColumn>içinde başarıyla değiştirildikten sonra gerçekleşir.|  
|<xref:System.Data.DataTable.ColumnChanging>|İçin bir değer gönderildiğinde gerçekleşir `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|İçindeki `DataColumn` <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRow> bir değer veya öğesinin bir değeri başarıyla değiştirildikten sonra gerçekleşir. `DataTable`|  
|<xref:System.Data.DataTable.RowChanging>|İçindeki `DataColumn` `RowState` birdeğer`DataRow` veya bir değeri için bir değişiklik gönderildiğinde gerçekleşir. `DataTable`|  
|<xref:System.Data.DataTable.RowDeleted>|`DataRow` İçindeki bir öğesinden sonra olarak `Deleted`işaretlendiğinde gerçekleşir. `DataTable`|  
|<xref:System.Data.DataTable.RowDeleting>|İçindeki bir `DataRow` , `DataTable` olarak `Deleted`işaretlenmeden önce gerçekleşir.|  
|<xref:System.Data.DataTable.TableCleared>|Bir <xref:System.Data.DataTable.Clear%2A> `DataRow`yöntemine `DataTable` yapılan bir çağrı başarıyla temizlendikten sonra gerçekleşir.|  
|<xref:System.Data.DataTable.TableClearing>|`Clear` Yöntem çağrıldıktan sonra, ancak `Clear` işlem başlamadan önce oluşur.|  
|<xref:System.Data.DataTable.TableNewRow>|Metodu içinbir`DataRow` çağrısıyla yeni bir oluşturulduktan sonra gerçekleşir. `DataTable` `NewRow`|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|`DataTable` Olduğunda`Disposed`gerçekleşir. Devralındığı <xref:System.ComponentModel.MarshalByValueComponent>yer.|  
  
> [!NOTE]
> Satırları ekleyen veya silen çoğu işlem `ColumnChanged` ve `ColumnChanging` olaylarını oluşturmaz. `DiffGram` `ColumnChanged` `ColumnChanging` `XmlReadMode` `ReadXml` Ancak, veya, okunan xml belgesi bir`Auto` olduğunda veya olarak ayarlanmadığı takdirde yöntemi, ve olayları yükseltir. `DiffGram`  
  
> [!WARNING]
> Veriler, `DataSet` `RowChanged` olayın oluşturulduğu bir içinde değiştirilirse veri bozulması meydana gelebilir. Böyle bir veri bozulması oluşursa, hiçbir özel durum oluşturulmaz.  
  
## <a name="additional-related-events"></a>Diğer Ilgili olaylar  
 <xref:System.Data.DataTable.Constraints%2A> Özelliği bir<xref:System.Data.ConstraintCollection> örneği barındırır. <xref:System.Data.ConstraintCollection> Sınıfı bir<xref:System.Data.ConstraintCollection.CollectionChanged> olay gösterir. Bu olay, `ConstraintCollection`bir kısıtlama eklendiğinde, değiştirildiğinde veya öğesinden kaldırıldığında ateşlenir.  
  
 <xref:System.Data.DataTable.Columns%2A> Özelliği bir<xref:System.Data.DataColumnCollection> örneği barındırır. `DataColumnCollection` Sınıfı bir<xref:System.Data.DataColumnCollection.CollectionChanged> olay gösterir. Bu olay, `DataColumnCollection`' den `DataColumn` eklendiğinde, değiştirildiğinde veya kaldırıldığında ateşlenir. Etkinliğin tetiklenmesine neden olan değişiklikler, bir sütunun ad, tür, ifade veya sıra konumunda değişiklikler içerir.  
  
 <xref:System.Data.DataSet.Tables%2A> Öğesinin özelliği bir<xref:System.Data.DataTableCollection> örneği barındırır. <xref:System.Data.DataSet> Sınıfı hem a `CollectionChanged` hem de bir `CollectionChanging` olay gösterir. `DataTableCollection` Bu olaylar, `DataSet`öğesine eklendiğinde `DataTable` veya öğesine kaldırıldığında harekete geçolur.  
  
 ' De yapılan değişiklikler <xref:System.Data.DataView> ,ilişkiliolanolaylarıdatetikleyebilir.`DataRows` Sınıfı, <xref:System.Data.DataView.ListChanged> bir`DataColumn` değer değiştiğinde veya görünümün kompozisyonu veya sıralama düzeni değiştiğinde tetiklenen bir olay gösterir. `DataView` Sınıfı <xref:System.Data.DataRowView> , <xref:System.Data.DataRowView.PropertyChanged> ilişkili`DataColumn` bir değer değiştiğinde harekete gelen bir olay gösterir.  
  
## <a name="sequence-of-operations"></a>Işlem sırası  
 Eklendiğinde, değiştirildiğinde veya silindiğinde oluşan `DataRow` işlemlerin sırası aşağıda verilmiştir:  
  
1. Önerilen kaydı oluşturun ve tüm değişiklikleri uygulayın.  
  
2. İfade olmayan sütunlar için kısıtlamaları denetleyin.  
  
3. `RowChanging` Veya`RowDeleting` olaylarını uygun şekilde yükseltin.  
  
4. Önerilen kaydı geçerli kayıt olarak ayarlayın.  
  
5. İlişkili dizinleri güncelleştirin.  
  
6. İlişkili `ListChanged` nesneler için `DataView` ilişkili`DataRowView` nesneler ve `PropertyChanged` olaylar için olaylar oluştur.  
  
7. Tüm ifade sütunlarını değerlendirin, ancak bu sütunlardaki kısıtlamaların denetimini erteler.  
  
8. İfade `ListChanged` sütunu değerlendirmelerinin `DataView` etkilediği ilişkili `PropertyChanged` `DataRowView` nesneler için ilişkili nesneler ve olaylar için olaylar oluştur.  
  
9. `RowChanged` Veya`RowDeleted` olaylarını uygun şekilde yükseltir.  
  
10. İfade sütunlarındaki kısıtlamaları denetleyin.  
  
> [!NOTE]
> İfade sütunlarındaki değişiklikler hiçbir şekilde olay `DataTable` oluşturmaz. İfade sütunlarındaki değişiklikler yalnızca ve `DataView` `DataRowView` olayları yükseltir. İfade sütunlarının birden fazla sütuna bağımlılığı olabilir ve tek `DataRow` bir işlem sırasında birden çok kez değerlendirilebilirler. Her ifade değerlendirmesi olayları başlatır ve tek `DataRow` bir işlem, ifade sütunları etkileniyorsa, büyük olasılıkla aynı ifade sütunu için birden çok olay da dahil olmak üzere birden çok `ListChanged` ve `PropertyChanged` olay oluşturabilir.  
  
> [!WARNING]
> Olay`RowChanged` işleyicisi içinde oluşturma <xref:System.NullReferenceException> . Bir a `RowChanged` olayı `DataTable` <xref:System.NullReferenceException> içindeoluşturulursa,budurumda`DataTable`, bozuk olur.  
  
### <a name="example"></a>Örnek  
 `RowChanged`Aşağıdaki örnek ,`ColumnChanged` `RowChanging` ,,`TableCleared`,,,,, ve`TableClearing` olayları için olay işleyicilerinin nasıl oluşturulacağını göstermektedir. `RowDeleted` `RowDeleting` `ColumnChanging` `TableNewRow` Her olay işleyicisi, tetiklendiğinde konsol penceresinde çıktıyı görüntüler.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [DataAdapter Olaylarını İşleme](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [DataSet Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
