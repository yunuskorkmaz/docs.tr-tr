---
description: 'Daha fazla bilgi edinin: veri kümesi Içeriğini birleştirme'
title: DataSet İçeriklerini Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: bdd7184d2b3a46f8ee59a052239dcd472db5e404
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651879"
---
# <a name="merging-dataset-contents"></a>DataSet İçeriklerini Birleştirme

<xref:System.Data.DataSet.Merge%2A>Bir <xref:System.Data.DataSet> , <xref:System.Data.DataTable> veya <xref:System.Data.DataRow> dizisinin içeriğini varolan bir, veya dizisinin içeriğine birleştirmek için yöntemini kullanabilirsiniz `DataSet` . Birçok etken ve seçenek, yeni verilerin mevcut bir ile nasıl birleştirildiğini etkiler `DataSet` .

## <a name="primary-keys"></a>Birincil Anahtarlar

Bir birleştirmeden yeni veri ve şema alan tablonun birincil anahtarı varsa, gelen verilerdeki yeni satırlar, <xref:System.Data.DataRowVersion.Original> gelen verilerdeki aynı birincil anahtar değerlerine sahip varolan satırlarla eşleştirilir. Gelen şemadaki sütunlar var olan şemadan eşleşiyorsa, varolan satırlardaki veriler değiştirilir. Varolan şemayla eşleşmeyen sütunlar yok sayılır veya parametreye göre eklenir <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> . Varolan satırlarla eşleşmeyen birincil anahtar değerleri olan yeni satırlar varolan tabloya eklenir.

Gelen veya mevcut satırlarda satır durumu varsa <xref:System.Data.DataRowState.Added> , <xref:System.Data.DataRowVersion.Current> `Added` satır sürümü mevcut olmadığından birincil anahtar değerleri satırın birincil anahtar değeri kullanılarak eşleştirilir `Original` .

Gelen bir tablo ve varolan bir tablo, aynı ada ancak farklı veri türlerine sahip bir sütun içeriyorsa, bir özel durum oluşturulur ve <xref:System.Data.DataSet.MergeFailed> olay `DataSet` tetiklenir. Bir gelen tablo ve var olan bir tabloda hem tanımlanmış anahtarlar varsa, ancak birincil anahtarlar farklı sütunlara ait ise, bir özel durum oluşturulur ve `MergeFailed` olay `DataSet` tetiklenir.

Bir birleştirmeden yeni veri alan tablonun birincil anahtarı yoksa, gelen verilerden yeni satırlar tablodaki varolan satırlarla eşleştirilemez ve bunun yerine var olan tabloya eklenir.

## <a name="table-names-and-namespaces"></a>Tablo adları ve ad alanları

<xref:System.Data.DataTable> isteğe bağlı olarak, nesnelere bir <xref:System.Data.DataTable.Namespace%2A> özellik değeri atanabilir. <xref:System.Data.DataTable.Namespace%2A>Değerler atandığında, bir, <xref:System.Data.DataSet> <xref:System.Data.DataTable> aynı değere sahip birden fazla nesne içerebilir <xref:System.Data.DataTable.TableName%2A> . Birleştirme işlemleri sırasında, <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataTable.Namespace%2A> birleştirmenin hedefini belirlemek için kullanılır. Hiçbiri <xref:System.Data.DataTable.Namespace%2A> atanmamışsa, yalnızca <xref:System.Data.DataTable.TableName%2A> bir birleştirmenin hedefini tanımlamak için kullanılır.

> [!NOTE]
> Bu davranış .NET Framework sürüm 2,0 ' de değiştirildi. Sürüm 1,1 ' de, ad alanları desteklenmiş ancak birleştirme işlemleri sırasında yok sayıldı. Bu nedenle, <xref:System.Data.DataSet> özellik değerlerini kullanan bir, <xref:System.Data.DataTable.Namespace%2A> çalıştırdığınız .NET Framework sürümüne bağlı olarak farklı davranışlara sahip olacaktır. Örneğin, `DataSets` `DataTables` aynı <xref:System.Data.DataTable.TableName%2A> özellik değerlerinin ancak farklı özellik değerlerinin bulunduğu iki içeren bir sahip olduğunuzu varsayalım <xref:System.Data.DataTable.Namespace%2A> . .NET Framework sürüm 1,1 ' de, <xref:System.Data.DataTable.Namespace%2A> iki nesne birleştirilirken farklı adlar yok sayılır <xref:System.Data.DataSet> . Ancak, sürüm 2,0 ' den itibaren birleştirme, hedefte iki yeni oluşturulmasına neden olur `DataTables` <xref:System.Data.DataSet> . Özgün, `DataTables` birleştirme tarafından etkilenmeyecektir.

## <a name="preservechanges"></a>PreserveChanges

`DataSet`Yöntemine bir, `DataTable` veya dizisi geçirdiğinizde, `DataRow` `Merge` var olan değişikliklerin korunup korunmayacağını `DataSet` ve gelen verilerde bulunan yeni şema öğelerinin nasıl işleneceğini belirten isteğe bağlı parametreleri ekleyebilirsiniz. Gelen veriler sonrasında bu parametrelerin ilki, <xref:System.Data.LoadOption.PreserveChanges> var olan değişikliklerin korunup korunmayacağını belirten bir Boole bayrağıdır `DataSet` . `PreserveChanges`Bayrak olarak ayarlandıysa `true` , gelen değerler `Current` varolan satırın satır sürümünde varolan değerlerin üzerine yazmaz. `PreserveChanges`Bayrak olarak ayarlandıysa `false` , gelen değerler `Current` varolan satırın satır sürümünde varolan değerlerin üzerine yazar. `PreserveChanges`Bayrak belirtilmemişse, `false` Varsayılan olarak olarak ayarlanır. Satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).

Ne zaman, var olan satırdaki `PreserveChanges` `true` veriler <xref:System.Data.DataRowVersion.Current> Mevcut satırın satır sürümünde tutulur, ancak <xref:System.Data.DataRowVersion.Original> Mevcut satırın satır sürümündeki verilerin, `Original` gelen satırın satır sürümündeki verilerle üzerine yazılır. <xref:System.Data.DataRow.RowState%2A>Var olan satırın öğesine ayarlanır <xref:System.Data.DataRowState.Modified> . Aşağıdaki özel durumlar geçerlidir:

- Var olan satır ' a sahipse `RowState` `Deleted` , bu `RowState` kalır `Deleted` ve olarak ayarlanır `Modified` . Bu durumda, gelen satırdaki veriler `Original` Mevcut satırın satır sürümünde depolanmaya devam eder, `Original` var olan satırın satır sürümünün üzerine yazılır (gelen satır öğesine sahip olmadığı müddetçe `RowState` `Added` ).

- Gelen satırın ' a sahip olması durumunda, gelen satırda `RowState` `Added` `Original` bir satır sürümü bulunmadığından, mevcut satırın satır sürümündeki verilerin üzerine gelen satırdaki verileri yazılmaz `Original` .

Ne zaman, `PreserveChanges` `false` `Current` `Original` var olan satırdaki ve satır sürümlerinin her ikisi de gelen satırdaki verilerle üzerine yazılır ve `RowState` var olan satır `RowState` gelen satırın öğesine ayarlanır. Aşağıdaki özel durumlar geçerlidir:

- Gelen satır ' a sahipse `RowState` `Unchanged` ve var olan satır,, veya ' a sahipse, `RowState` `Modified` `Deleted` `Added` `RowState` var olan satırın öğesine ayarlanır `Modified` .

- Gelen satır ' a sahipse `RowState` `Added` ve var olan satır,, veya ' a sahipse, `RowState` `Unchanged` `Modified` `Deleted` `RowState` var olan satırın öğesine ayarlanır `Modified` . Ayrıca, `Original` gelen satır bir satır sürümüne sahip olmadığından, mevcut satırın satır sürümündeki verilerin, gelen satırdaki verilerle üzerine yazılmaz `Original` .

## <a name="missingschemaaction"></a>MissingSchemaAction

<xref:System.Data.MissingSchemaAction> `Merge` `Merge` Mevcut bir parçası olmayan gelen verilerdeki şema öğelerini nasıl işleyeceğinizi belirtmek için yönteminin isteğe bağlı parametresini kullanabilirsiniz `DataSet` .

Aşağıdaki tabloda seçeneklerini açıklanmaktadır `MissingSchemaAction` .

|MissingSchemaAction seçeneği|Description|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Yeni şema bilgilerini öğesine ekleyin `DataSet` ve yeni sütunları gelen değerlerle doldurun. Bu varsayılan seçenektir.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Yeni şemayı ve birincil anahtar bilgilerini öğesine ekleyin `DataSet` ve yeni sütunları gelen değerlerle doldurun.|
|<xref:System.Data.MissingSchemaAction.Error>|Eşleşmeyen şema bilgileriyle karşılaşılırsa bir özel durum oluşturur.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Yeni şema bilgilerini yoksayın.|

## <a name="constraints"></a>Kısıtlamalar

`Merge`Yöntemiyle, tüm yeni veriler mevcut olana kadar kısıtlamalar denetlenmez `DataSet` . Veriler eklendikten sonra, içindeki geçerli değerler üzerinde kısıtlamalar zorlanır `DataSet` . Kodunuzun, kısıtlama ihlalleri nedeniyle oluşturulan tüm özel durumları işlediğinden emin olmanız gerekir.

İçindeki mevcut bir satırın `DataSet` , `Unchanged` birincil anahtar değeri 1 olan bir satır olduğu bir durum düşünün. Birincil anahtar `Modified` değeri 2 ve birincil anahtar değeri 1 olan gelen bir satır içeren bir birleştirme işlemi sırasında `Original` `Current` , `Original` birincil anahtar değerleri farklı olduğundan mevcut satır ve gelen satır eşleşen kabul edilmez. Ancak, birleştirme tamamlandığında ve kısıtlamalar denetlendiğinde, `Current` birincil anahtar değerleri birincil anahtar sütunu için benzersiz kısıtlamayı ihlal ettiğinden bir özel durum oluşturulur.

> [!NOTE]
> Bir kimlik sütunu gibi bir otomatik artan sütun içeren bir veritabanı tablosuna satırlar yerleştirildiğinde, ekleme tarafından döndürülen kimlik sütunu değeri, içindeki değeriyle eşleşmeyebilir ve `DataSet` döndürülen satırların birleştirilme yerine eklenmesine neden olabilir. Daha fazla bilgi için bkz. [kimlik veya OtomatikSayı değerlerini alma](../retrieving-identity-or-autonumber-values.md).

Aşağıdaki kod örneği iki `DataSet` nesneyi `DataSet` , iki gelen nesnenin birleştirilmiş şemalarıyla farklı şemalarla birleştirir `DataSet` .

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

Aşağıdaki kod örneği, güncelleştirmeleriyle birlikte var olan bir güncelleştirme alır `DataSet` ve bu güncelleştirmeleri `DataAdapter` veri kaynağında işlenmek üzere öğesine geçirir. Sonuçlar bundan sonra orijinalde birleştirilir `DataSet` . Bir hatayla sonuçlanan değişiklikleri reddetmeden sonra, birleştirilmiş değişiklikler ile birlikte kaydedilir `AcceptChanges` .

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [Satır Durumları ve Satır Sürümleri](row-states-and-row-versions.md)
- [DataAdapters ve DataReaders](../dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Alma ve Değiştirme](../retrieving-and-modifying-data.md)
- [Kimliği veya Otomatik Sayı Değerlerini Alma](../retrieving-identity-or-autonumber-values.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
