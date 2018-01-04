---
title: "Veri kümesi içeriği birleştirme"
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
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 44d171cab4099436d7daea26def831f149b75b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="merging-dataset-contents"></a>Veri kümesi içeriği birleştirme
Kullanabileceğiniz <xref:System.Data.DataSet.Merge%2A> içeriğini birleştirmek için yöntemi bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> içine var olan bir dizi `DataSet`. Çeşitli Etkenler ve seçenekleri yeni verilerin nasıl etkiler varolan içine birleştirilir `DataSet`.  
  
## <a name="primary-keys"></a>Birincil anahtarlar  
 Yeni veri ve şema birleştirmenin dışında alma tablonun birincil anahtarı varsa, yeni satırlar gelen verileri aynı varolan satırları ile eşleştirilir <xref:System.Data.DataRowVersion.Original> birincil anahtar değerleri gelen verileri de olarak. Gelen şema sütunlarından varolan şema eşleşen, var olan satırları değiştirilir. Varolan şema eşleşmiyor sütunları göz ardı ya da temel alınarak eklenen <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametresi. Var olan herhangi bir satır ile eşleşmiyor birincil anahtar değerleriyle yeni satırlar için var olan tablo eklenir.  
  
 Gelen veya var olan satır satır durumunu varsa <xref:System.Data.DataRowState.Added>, birincil anahtar değerlerine kullanılarak eşleştirilir <xref:System.Data.DataRowVersion.Current> birincil anahtar değeri `Added` çünkü satır hiçbir `Original` satır sürümü bulunmaktadır.  
  
 Gelen tablo ve var olan bir tabloyu aynı adlı ancak farklı veri türlerine sahip bir sütun içeriyorsa, özel durum oluşur ve <xref:System.Data.DataSet.MergeFailed> olayı `DataSet` tetiklenir. Gelen tablo ve var olan bir tabloyu anahtarları tanımladığınız, ancak birincil anahtarları farklı sütunlar için bir özel durum oluşur ve `MergeFailed` olayı `DataSet` tetiklenir.  
  
 Birleştirmenin dışında yeni veri alma tablosunda birincil anahtar yok, gelen veri yeni satırları tabloda varolan satırları eşleştirilemiyor ve bunun yerine var olan tabloya eklenir.  
  
## <a name="table-names-and-namespaces"></a>Tablo adları ve ad alanları  
 <xref:System.Data.DataTable>nesneleri isteğe bağlı olarak atanabilir bir <xref:System.Data.DataTable.Namespace%2A> özellik değeri. Zaman <xref:System.Data.DataTable.Namespace%2A> değerler atanır, bir <xref:System.Data.DataSet> birden çok içerebilir <xref:System.Data.DataTable> aynı nesneleriyle <xref:System.Data.DataTable.TableName%2A> değeri. Birleştirme işlemleri sırasında hem de <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataTable.Namespace%2A> bir birleştirme işleminin hedefi tanımlamak için kullanılır. Öyle değilse <xref:System.Data.DataTable.Namespace%2A> , yalnızca atanmış olan <xref:System.Data.DataTable.TableName%2A> bir birleştirme işleminin hedefi tanımlamak için kullanılır.  
  
> [!NOTE]
>  Bu davranış, .NET Framework 2.0 sürümünde değiştirildi. Sürüm 1.1, ad alanları desteklenen ancak birleştirme işlemleri sırasında yoksayıldı. Bu nedenle, bir <xref:System.Data.DataSet> kullanan <xref:System.Data.DataTable.Namespace%2A> özellik değerlerini çalıştırdığınız .NET Framework sürümüne bağlı olarak farklı davranışlar olacaktır. Örneğin, iki olduğunu varsayalım `DataSets` içeren `DataTables` aynı <xref:System.Data.DataTable.TableName%2A> özellik değerlerinin ancak farklı <xref:System.Data.DataTable.Namespace%2A> özellik değerleri. Farklı .NET Framework 1.1 sürümünde <xref:System.Data.DataTable.Namespace%2A> iki birleştirilirken adları yoksayılacak <xref:System.Data.DataSet> nesneleri. Ancak, nedenleri iki yeni birleştirme sürüm 2.0, ile başlayan `DataTables` hedef oluşturulacak <xref:System.Data.DataSet>. Özgün `DataTables` birleştirme ile etkilenmeyecek.  
  
## <a name="preservechanges"></a>PreserveChanges  
 Geçirdiğiniz zaman bir `DataSet`, `DataTable`, veya `DataRow` için dizi `Merge` yöntemi, var olan değişiklikleri koruma gerekip gerekmediğini belirten isteğe bağlı parametreler dahil edebileceğiniz `DataSet`ve bulunan yeni şema öğeleri nasıl ele alınacağını gelen veri. Bu parametre bir Boole bayrağı gelen veri tamamlandıktan sonra ilk <xref:System.Data.LoadOption.PreserveChanges>, var olan değişiklikleri koruma gerekip gerekmediğini belirten `DataSet`. Varsa `PreserveChanges` bayrağı ayarlanmış `true`, gelen değerleri varolan değerlerle üzerine `Current` varolan bir satır satır sürümü. Varsa `PreserveChanges` bayrağı ayarlanmış `false`, gelen değerleri, var olan değerlerin üzerine `Current` varolan bir satır satır sürümü. Varsa `PreserveChanges` bayrak belirtilmezse, ayarlanır `false` varsayılan olarak. Satır sürümleri hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Zaman `PreserveChanges` olan `true`, varolan bir satır verileri de korunur <xref:System.Data.DataRowVersion.Current> verilerden sırasında varolan bir satır satır sürümü <xref:System.Data.DataRowVersion.Original> satır sürümü mevcut satırın üzerine verilerle `Original` satır gelen satır sürümü. <xref:System.Data.DataRow.RowState%2A> Varolan satırının kümesine <xref:System.Data.DataRowState.Modified>. Aşağıdaki özel durumlar geçerlidir:  
  
-   Varolan bir satır varsa bir `RowState` , `Deleted`, bu `RowState` kalır `Deleted` ve ayarlanmazsa `Modified`. Bu durumda, gelen satır verileri hala depolanır `Original` varolan bir satır satır sürümü üzerine `Original` varolan bir satır satır sürümü (gelen satır olmadıkça bir `RowState` , `Added`).  
  
-   Gelen satır varsa bir `RowState` , `Added`, verileri `Original` varolan bir satır satır sürümü yazılmaz gelen satır verilerle gelen satır sahip olmadığından bir `Original` satır sürümü.  
  
 Zaman `PreserveChanges` olan `false`, her iki `Current` ve `Original` varolan bir satır satır sürümlerde gelen satır verilerle yazılır ve `RowState` varolan satırının kümesine `RowState` gelen satır. Aşağıdaki özel durumlar geçerlidir:  
  
-   Gelen satır varsa bir `RowState` , `Unchanged` ve varolan bir satır sahip bir `RowState` , `Modified`, `Deleted`, veya `Added`, `RowState` varolan satırının kümesine `Modified`.  
  
-   Gelen satır varsa bir `RowState` , `Added`, ve varolan bir satır sahip bir `RowState` , `Unchanged`, `Modified`, veya `Deleted`, `RowState` varolan satırının kümesine `Modified`. Ayrıca, verileri `Original` varolan bir satır satır sürümü üzerine gelen satır verilerle gelen satır sahip olmadığından bir `Original` satır sürümü.  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 Kullanabileceğiniz isteğe bağlı <xref:System.Data.MissingSchemaAction> parametresinin `Merge` belirtmek için yöntemin nasıl `Merge` şema öğeleri varolan bir parçası olmayan gelen veri işleyecek `DataSet`.  
  
 Aşağıdaki tabloda ilgili seçenekleri açıklar `MissingSchemaAction`.  
  
|MissingSchemaAction seçeneği|Açıklama|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|Yeni şema bilgilerini ekleme `DataSet` ve yeni sütunlar gelen değerlerle doldurmak. Bu varsayılandır.|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Yeni şema ekleyip için birincil anahtar bilgilerini `DataSet` ve yeni sütunlar gelen değerlerle doldurmak.|  
|<xref:System.Data.MissingSchemaAction.Error>|Eşleşmeyen şema bilgileri karşılaşılırsa, bir özel durum.|  
|<xref:System.Data.MissingSchemaAction.Ignore>|Yeni şema bilgileri yoksay.|  
  
## <a name="constraints"></a>Kısıtlamalar  
 İle `Merge` yöntemi, tüm yeni verileri eklenene kadar varolan, kısıtlamalar işaretli değil `DataSet`. Veri eklendiğinde kısıtlamaları geçerli değerlere uygulanır `DataSet`. Kodunuzu kısıtlama ihlali nedeniyle atılan tüm özel durumları işler emin olmalısınız.  
  
 Var olan bir satır burada bir durum düşünün bir `DataSet` olan bir `Unchanged` birincil anahtar değerine sahip bir satır 1. Bir birleştirme işlemi sırasında bir `Modified` gelen satırla bir `Original` 2 birincil anahtar değerine ve bir `Current` birincil anahtar değerini 1, varolan bir satır ve gelen satır dikkate alınmaz çünkü eşleşen `Original` birincil anahtar değerlerinin farklı. Ancak birleştirme işlemi tamamlandıktan ve kısıtlamaları işaretli olduğunda, bir özel durum nedeniyle oluşturulacaktır `Current` birincil anahtar değerlerinin birincil anahtar sütunu için benzersiz kısıtlamayı ihlal ediyor.  
  
> [!NOTE]
>  Sütunu bir kimlik sütunu gibi artırma otomatik içeren bir veritabanı tablosuna satır eklendiğinde Ekle tarafından döndürülen kimlik sütunu değeri değeri eşleşmeyebilir `DataSet`, yerine eklenecek döndürülen satır neden birleştirilir. Daha fazla bilgi için bkz: [alma kimliği veya sayı değerlerini](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
 Aşağıdaki kod örneği iki birleştirir `DataSet` differents şemaları tek nesneleriyle `DataSet` iki gelen birleştirilmiş şemalarda `DataSet` nesneleri.  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 Aşağıdaki kod örneğinde mevcut bir alan `DataSet` güncelleştirmeleri ve güncelleştirmeler için geçiş ile bir `DataAdapter` veri kaynağında işlenecek. Sonuçları sonra özgün birleştirilir `DataSet`. Hatayla sonuçlandı değişiklikleri reddetme sonra birleştirilmiş değişikliklerin ile kaydedilmiş `AcceptChanges`.  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Satır Durumları ve Satır Sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [DataAdapters ve DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Kimliği veya Otomatik Sayı Değerlerini Alma](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
