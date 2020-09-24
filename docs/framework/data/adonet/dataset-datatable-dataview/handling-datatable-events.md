---
title: DataTable Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: c00e5e42508160a210d16f058c46afbf62ae0ee0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164733"
---
# <a name="handling-datatable-events"></a>DataTable Olaylarını İşleme

<xref:System.Data.DataTable>Nesnesi, bir uygulama tarafından işlenebilmesi için bir dizi olay sağlar. Aşağıdaki tabloda olayları açıklanmaktadır `DataTable` .  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|<xref:System.Data.DataTable.EndInit%2A>Bir a yöntemi çağrıldıktan sonra gerçekleşir `DataTable` . Bu olay öncelikle tasarım zamanı senaryolarını desteklemeye yöneliktir.|  
|<xref:System.Data.DataTable.ColumnChanged>|Bir değer bir içinde başarıyla değiştirildikten sonra gerçekleşir <xref:System.Data.DataColumn> .|  
|<xref:System.Data.DataTable.ColumnChanging>|İçin bir değer gönderildiğinde gerçekleşir `DataColumn` .|  
|<xref:System.Data.DataTable.RowChanged>|`DataColumn`İçindeki bir değer veya <xref:System.Data.DataRow.RowState%2A> öğesinin bir değeri <xref:System.Data.DataRow> `DataTable` başarıyla değiştirildikten sonra gerçekleşir.|  
|<xref:System.Data.DataTable.RowChanging>|`DataColumn`İçindeki bir değer veya bir değeri için bir değişiklik gönderildiğinde gerçekleşir `RowState` `DataRow` `DataTable` .|  
|<xref:System.Data.DataTable.RowDeleted>|İçindeki bir öğesinden sonra `DataRow` `DataTable` olarak işaretlendiğinde gerçekleşir `Deleted` .|  
|<xref:System.Data.DataTable.RowDeleting>|`DataRow`İçindeki bir, `DataTable` olarak işaretlenmeden önce gerçekleşir `Deleted` .|  
|<xref:System.Data.DataTable.TableCleared>|Bir yöntemine yapılan bir çağrı <xref:System.Data.DataTable.Clear%2A> `DataTable` başarıyla temizlendikten sonra gerçekleşir `DataRow` .|  
|<xref:System.Data.DataTable.TableClearing>|`Clear`Yöntem çağrıldıktan sonra, ancak işlem başlamadan önce oluşur `Clear` .|  
|<xref:System.Data.DataTable.TableNewRow>|`DataRow`Metodu için bir çağrısıyla yeni bir oluşturulduktan sonra gerçekleşir `NewRow` `DataTable` .|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Olduğunda gerçekleşir `DataTable` `Disposed` . Devralındığı yer <xref:System.ComponentModel.MarshalByValueComponent> .|  
  
> [!NOTE]
> Satırları ekleyen veya silen çoğu işlem `ColumnChanged` ve `ColumnChanging` olaylarını oluşturmaz. Ancak, `ReadXml` `ColumnChanged` veya, `ColumnChanging` `XmlReadMode` `DiffGram` `Auto` okunan xml belgesi bir olduğunda veya `DiffGram` olarak ayarlanmadığı takdirde yöntemi, ve olayları yükseltir.  
  
> [!WARNING]
> Veriler, olayın oluşturulduğu bir içinde değiştirilirse veri bozulması meydana gelebilir `DataSet` `RowChanged` . Böyle bir veri bozulması oluşursa, hiçbir özel durum oluşturulmaz.  
  
## <a name="additional-related-events"></a>Diğer Ilgili olaylar  

 <xref:System.Data.DataTable.Constraints%2A>Özelliği bir örneği barındırır <xref:System.Data.ConstraintCollection> . <xref:System.Data.ConstraintCollection>Sınıfı bir olay gösterir <xref:System.Data.ConstraintCollection.CollectionChanged> . Bu olay, bir kısıtlama eklendiğinde, değiştirildiğinde veya öğesinden kaldırıldığında ateşlenir `ConstraintCollection` .  
  
 <xref:System.Data.DataTable.Columns%2A>Özelliği bir örneği barındırır <xref:System.Data.DataColumnCollection> . `DataColumnCollection`Sınıfı bir olay gösterir <xref:System.Data.DataColumnCollection.CollectionChanged> . Bu olay `DataColumn` , ' den eklendiğinde, değiştirildiğinde veya kaldırıldığında ateşlenir `DataColumnCollection` . Etkinliğin tetiklenmesine neden olan değişiklikler, bir sütunun ad, tür, ifade veya sıra konumunda değişiklikler içerir.  
  
 <xref:System.Data.DataSet.Tables%2A>Öğesinin özelliği <xref:System.Data.DataSet> bir <xref:System.Data.DataTableCollection> örneği barındırır. `DataTableCollection`Sınıfı hem a hem de `CollectionChanged` bir `CollectionChanging` olay gösterir. Bu olaylar `DataTable` , öğesine eklendiğinde veya öğesine kaldırıldığında harekete geçolur `DataSet` .  
  
 ' De yapılan değişiklikler `DataRows` , ilişkili olan olayları da tetikleyebilir <xref:System.Data.DataView> . `DataView`Sınıfı, <xref:System.Data.DataView.ListChanged> bir `DataColumn` değer değiştiğinde veya görünümün kompozisyonu veya sıralama düzeni değiştiğinde tetiklenen bir olay gösterir. <xref:System.Data.DataRowView>Sınıfı, ilişkili bir <xref:System.Data.DataRowView.PropertyChanged> değer değiştiğinde harekete gelen bir olay gösterir `DataColumn` .  
  
## <a name="sequence-of-operations"></a>Işlem sırası  

 Eklendiğinde, değiştirildiğinde veya silindiğinde oluşan işlemlerin sırası aşağıda verilmiştir `DataRow` :  
  
1. Önerilen kaydı oluşturun ve tüm değişiklikleri uygulayın.  
  
2. İfade olmayan sütunlar için kısıtlamaları denetleyin.  
  
3. `RowChanging`Veya `RowDeleting` olaylarını uygun şekilde yükseltin.  
  
4. Önerilen kaydı geçerli kayıt olarak ayarlayın.  
  
5. İlişkili dizinleri güncelleştirin.  
  
6. İlişkili nesneler `ListChanged` için ilişkili `DataView` nesneler ve olaylar için olaylar oluştur `PropertyChanged` `DataRowView` .  
  
7. Tüm ifade sütunlarını değerlendirin, ancak bu sütunlardaki kısıtlamaların denetimini erteler.  
  
8. `ListChanged` `DataView` `PropertyChanged` İfade sütunu değerlendirmelerinin etkilediği ilişkili nesneler için ilişkili nesneler ve olaylar için olaylar oluştur `DataRowView` .  
  
9. `RowChanged`Veya `RowDeleted` olaylarını uygun şekilde yükseltir.  
  
10. İfade sütunlarındaki kısıtlamaları denetleyin.  
  
> [!NOTE]
> İfade sütunlarındaki değişiklikler hiçbir şekilde `DataTable` olay oluşturmaz. İfade sütunlarındaki değişiklikler yalnızca `DataView` ve olayları yükseltir `DataRowView` . İfade sütunlarının birden fazla sütuna bağımlılığı olabilir ve tek bir işlem sırasında birden çok kez değerlendirilebilirler `DataRow` . Her ifade değerlendirmesi olayları başlatır ve tek bir `DataRow` işlem, `ListChanged` `PropertyChanged` ifade sütunları etkileniyorsa, büyük olasılıkla aynı ifade sütunu için birden çok olay da dahil olmak üzere birden çok ve olay oluşturabilir.  
  
> [!WARNING]
> <xref:System.NullReferenceException> `RowChanged` Olay işleyicisi içinde oluşturma. Bir a <xref:System.NullReferenceException> olayı içinde oluşturulursa, `RowChanged` `DataTable` Bu durumda, `DataTable` bozuk olur.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek,,,,,,,, `RowChanged` `RowChanging` `RowDeleted` `RowDeleting` `ColumnChanged` `ColumnChanging` `TableNewRow` `TableCleared` ve `TableClearing` olayları için olay işleyicilerinin nasıl oluşturulacağını göstermektedir. Her olay işleyicisi, tetiklendiğinde konsol penceresinde çıktıyı görüntüler.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [DataAdapter Olaylarını İşleme](../handling-dataadapter-events.md)
- [DataSet Olaylarını İşleme](handling-dataset-events.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
