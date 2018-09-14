---
title: DataSet içeriklerini birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: 38d716552c4a52e01ef803ce197e4d588ed562c3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560876"
---
# <a name="merging-dataset-contents"></a>DataSet içeriklerini birleştirme
Kullanabileceğiniz <xref:System.Data.DataSet.Merge%2A> içeriğini birleştirmek için yöntemi bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> içine var olan bir dizi `DataSet`. Yeni verilerin nasıl çeşitli Etkenler ve seçeneklerini etkileyen varolan içine birleştirilir `DataSet`.  
  
## <a name="primary-keys"></a>Birincil anahtarlar  
 Yeni veri ve şema bir birleştirmeden alma tabloda birincil anahtar varsa, yeni satır, gelen veri aynı olan mevcut satırlarla eşleştirilir <xref:System.Data.DataRowVersion.Original> birincil anahtar değerleri gelen verilerdeki gideriyor. Gelen şema sütunlarından mevcut şema eşleşen, var olan satırlardaki verileri değiştirildi. Varolan şema eşleşmeyen sütun göz ardı veya temel alınarak eklenen <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametresi. Var olan tüm satırları eşleşmeyen birincil anahtar değerlerine sahip yeni satırlar için var olan tablo eklenir.  
  
 Gelen veya var olan satır satır durumunu varsa <xref:System.Data.DataRowState.Added>, birincil anahtar değerlerini kullanarak eşleştirilir <xref:System.Data.DataRowVersion.Current> birincil anahtar değeri `Added` çünkü satır hiçbir `Original` satır sürümü yok.  
  
 Gelen bir tablo ve mevcut bir tabloyu bir sütunla aynı ada ancak farklı veri türleri içeriyorsa, özel durum oluşur ve <xref:System.Data.DataSet.MergeFailed> olayı `DataSet` tetiklenir. Gelen bir tablo ve var olan bir tablo anahtarları tanımladığınız, ancak birincil anahtarları farklı sütunlar için bir özel durum oluşturulur ve `MergeFailed` olayı `DataSet` tetiklenir.  
  
 Bir birleştirmeden yeni veri alma tablosu birincil anahtar yoksa, yeni satır, gelen veri mevcut tablosundaki satırlara eşleştirilemiyor ve bunun yerine mevcut tablosuna eklenir.  
  
## <a name="table-names-and-namespaces"></a>Tablo adları ve ad alanları  
 <xref:System.Data.DataTable> nesneleri isteğe bağlı olarak atanabilir bir <xref:System.Data.DataTable.Namespace%2A> özellik değeri. Zaman <xref:System.Data.DataTable.Namespace%2A> değerler atanır, bir <xref:System.Data.DataSet> birden çok içerebilir <xref:System.Data.DataTable> nesnelerle aynı <xref:System.Data.DataTable.TableName%2A> değeri. Birleştirme işlemleri sırasında hem de <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataTable.Namespace%2A> birleştirme hedefi tanımlamak için kullanılır. Hayır ise <xref:System.Data.DataTable.Namespace%2A> , yalnızca atanmış <xref:System.Data.DataTable.TableName%2A> birleştirme hedefi tanımlamak için kullanılır.  
  
> [!NOTE]
>  Bu davranış, .NET Framework'ün 2.0 sürümünde değiştirildi. Sürüm 1.1, ad alanları desteklendi ancak birleştirme işlemleri sırasında yoksayıldı. Bu nedenle, bir <xref:System.Data.DataSet> kullanan <xref:System.Data.DataTable.Namespace%2A> özellik değerleri, çalıştırdığınız .NET Framework sürümüne bağlı olarak farklı davranışlar olacaktır. Örneğin, iki olduğunu varsayalım `DataSets` içeren `DataTables` aynı <xref:System.Data.DataTable.TableName%2A> özellik değerlerinin ancak farklı <xref:System.Data.DataTable.Namespace%2A> özellik değerleri. Farklı .NET Framework 1.1 sürümünde <xref:System.Data.DataTable.Namespace%2A> adları, iki birleştirilirken yoksayılacak <xref:System.Data.DataSet> nesneleri. Ancak, nedenleri iki yeni birleştirme sürüm 2.0 ile başlayarak `DataTables` hedef oluşturulacak <xref:System.Data.DataSet>. Özgün `DataTables` birleştirme tarafından etkilenmez.  
  
## <a name="preservechanges"></a>PreserveChanges  
 Gönderdiğinizde bir `DataSet`, `DataTable`, veya `DataRow` için dizi `Merge` yöntemi, var olan değişiklikleri koruma yazılıp yazılmayacağını belirten isteğe bağlı parametreler içerebilir `DataSet`ve bulunan yeni şema öğeleri nasıl ele alınacağını gelen veri. Bu parametre bir Boole bayrağı gelen veri olduktan sonra ilk <xref:System.Data.LoadOption.PreserveChanges>, var olan değişiklikler korumak gerekip gerekmediğini belirten `DataSet`. Varsa `PreserveChanges` bayrağı ayarlandığında `true`, gelen değerleri mevcut değerleri üzerine `Current` var olan satır satır sürümü. Varsa `PreserveChanges` bayrağı ayarlandığında `false`, gelen değerleri mevcut değerlerin üzerine `Current` var olan satır satır sürümü. Varsa `PreserveChanges` bayrak belirtilmezse, ayarlanır `false` varsayılan olarak. Satır sürümleri hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Zaman `PreserveChanges` olan `true`, var olan satır verileri saklanır <xref:System.Data.DataRowVersion.Current> verilerden sırasında var olan satır satır sürümü <xref:System.Data.DataRowVersion.Original> var olan satır satır sürümü verilerle yazılır `Original` satır sürümünü gelen satırın. <xref:System.Data.DataRow.RowState%2A> Var olan satır kümesine <xref:System.Data.DataRowState.Modified>. Aşağıdaki özel durumlarını uygulayın:  
  
-   Var olan satır varsa bir `RowState` , `Deleted`bu `RowState` kalır `Deleted` ve ayarlı değil `Modified`. Bu durumda, gelen satırın verilerden hala barındırılacaktır `Original` satır sürümü mevcut satırın üzerine `Original` var olan satır satır sürümü (gelen satırın sahip olmadığı sürece bir `RowState` , `Added`).  
  
-   Gelen satırın varsa bir `RowState` , `Added`, verilerden `Original` satır sürümü mevcut satırın yazılmaz gelen satırın verilerle gelen satırın sahip olmadığından bir `Original` satır sürümü.  
  
 Zaman `PreserveChanges` olduğu `false`hem `Current` ve `Original` satır sürümleri mevcut sıradaki gelen satırın verilerle yazılır ve `RowState` var olan satır kümesine `RowState` gelen satırın. Aşağıdaki özel durumlarını uygulayın:  
  
-   Gelen satırın varsa bir `RowState` , `Unchanged` ve var olan bir satır sahip bir `RowState` , `Modified`, `Deleted`, veya `Added`, `RowState` var olan satır kümesine `Modified`.  
  
-   Gelen satırın varsa bir `RowState` , `Added`, ve var olan bir satır sahip bir `RowState` , `Unchanged`, `Modified`, veya `Deleted`, `RowState` var olan satır kümesine `Modified`. Ayrıca, verileri `Original` var olan satır satır sürümü üzerine gelen satırın verilerle gelen satırın sahip olmadığından bir `Original` satır sürümü.  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 Kullanabileceğiniz isteğe bağlı <xref:System.Data.MissingSchemaAction> parametresinin `Merge` yöntemi belirtmek için nasıl `Merge` var olan bir parçası olmayan gelen veri şeması öğeleri işleyecek `DataSet`.  
  
 Aşağıdaki tablo için seçenekleri açıklar `MissingSchemaAction`.  
  
|MissingSchemaAction seçeneği|Açıklama|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|Yeni şema ile ilgili bilgileri `DataSet` ve yeni sütunlar gelen değerlerle doldurmak. Bu varsayılandır.|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Yeni şema ve birincil anahtar bilgisini ekleme `DataSet` ve yeni sütunlar gelen değerlerle doldurmak.|  
|<xref:System.Data.MissingSchemaAction.Error>|Eşleşmeyen şema bilgileri mı yoksa bir özel durum.|  
|<xref:System.Data.MissingSchemaAction.Ignore>|Yeni şema bilgileri yoksayın.|  
  
## <a name="constraints"></a>Kısıtlamalar  
 İle `Merge` yöntemi kısıtlamalar değil tüm yeni veri eklendiğini kadar varolan kontrol `DataSet`. Veriler eklendikten sonra kısıtlamaları geçerli değerlere uygulanır `DataSet`. Kodunuzu kısıtlama ihlali nedeniyle atılan özel durumları işleme emin olmanız gerekir.  
  
 Varolan bir satırın içinde bir durum düşünün bir `DataSet` olduğu bir `Unchanged` 1 satır birincil bir anahtar değere sahip. Bir birleştirme işlemi sırasında bir `Modified` gelen satırı bir `Original` birincil anahtar değeri 2 ve `Current` 1, var olan satır ve gelen satırın birincil anahtarı değerini değil olarak kabul edilir çünkü eşleşen `Original` birincil anahtar değerlerini farklı. Ancak, birleştirme tamamlandı ve kısıtlamaları denetlenir, bir özel durum nedeniyle oluşturulur `Current` birincil anahtar değerlerini birincil anahtar sütunu için benzersizlik kısıtlamasını ihlal ediyor.  
  
> [!NOTE]
>  Sütun gibi bir kimlik sütunu artan otomatik içeren bir veritabanı tablosuna satır eklendiğinde, INSERT tarafından döndürülen kimlik sütunu değeri değeri eşleşmeyebilir `DataSet`, yerine eklenmesi döndürülen satırları neden birleştirilir. Daha fazla bilgi için [alınırken kimlik veya otomatik sayı değerlerini](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
 Aşağıdaki kod örneği iki birleştirir `DataSet` differents şemaları tek nesneleriyle `DataSet` iki gelen birleştirilmiş şemalarda `DataSet` nesneleri.  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 Aşağıdaki kod örneği, mevcut bir alan `DataSet` güncelleştirmeler ve bu güncelleştirmeleri geçişleri bir `DataAdapter` veri kaynağında işlenecek. Sonuçlar daha sonra özgün birleştirilmiş `DataSet`. Bir hata ile sonuçlandır değişiklikleri reddetme sonra birleştirilen değişiklikleri ile kaydedilmiş `AcceptChanges`.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
