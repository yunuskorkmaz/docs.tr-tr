---
title: DataSet İçeriklerini Birleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: e5a8040a803fbc9b098fc1b56e0f5d837c4cdb94
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203367"
---
# <a name="merging-dataset-contents"></a>DataSet İçeriklerini Birleştirme

<xref:System.Data.DataSet.Merge%2A> Bir <xref:System.Data.DataRow> ,veya<xref:System.Data.DataTable>dizisinin içeriğini varolan`DataSet`bir, veya dizisinin içeriğine birleştirmek için yöntemini kullanabilirsiniz. <xref:System.Data.DataSet> Birçok etken ve seçenek, yeni verilerin mevcut `DataSet`bir ile nasıl birleştirildiğini etkiler.

## <a name="primary-keys"></a>Birincil anahtarlar

Bir birleştirmeden yeni veri ve şema alan tablonun birincil anahtarı varsa, gelen verilerdeki yeni satırlar, gelen verilerdeki aynı <xref:System.Data.DataRowVersion.Original> birincil anahtar değerlerine sahip varolan satırlarla eşleştirilir. Gelen şemadaki sütunlar var olan şemadan eşleşiyorsa, varolan satırlardaki veriler değiştirilir. Varolan şemayla eşleşmeyen sütunlar yok sayılır veya <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametreye göre eklenir. Varolan satırlarla eşleşmeyen birincil anahtar değerleri olan yeni satırlar varolan tabloya eklenir.

Gelen veya mevcut satırlarda <xref:System.Data.DataRowState.Added>satır durumu varsa, `Original` satır sürümü mevcut olmadığından birincil anahtar değerleri `Added` satırın <xref:System.Data.DataRowVersion.Current> birincil anahtar değeri kullanılarak eşleştirilir.

Gelen bir tablo ve varolan bir tablo, aynı ada ancak farklı veri türlerine sahip bir sütun içeriyorsa, bir özel durum oluşturulur ve <xref:System.Data.DataSet.MergeFailed> olay `DataSet` tetiklenir. Bir gelen tablo ve var olan bir tabloda hem tanımlanmış anahtarlar varsa, ancak birincil anahtarlar farklı sütunlara ait ise, bir özel durum oluşturulur ve `MergeFailed` olay `DataSet` tetiklenir.

Bir birleştirmeden yeni veri alan tablonun birincil anahtarı yoksa, gelen verilerden yeni satırlar tablodaki varolan satırlarla eşleştirilemez ve bunun yerine var olan tabloya eklenir.

## <a name="table-names-and-namespaces"></a>Tablo adları ve ad alanları

<xref:System.Data.DataTable>isteğe bağlı olarak, nesnelere bir <xref:System.Data.DataTable.Namespace%2A> Özellik değeri atanabilir. Değerler atandığında, bir <xref:System.Data.DataSet> , <xref:System.Data.DataTable> aynı<xref:System.Data.DataTable.TableName%2A> değere sahip birden fazla nesne içerebilir. <xref:System.Data.DataTable.Namespace%2A> Birleştirme işlemleri sırasında, <xref:System.Data.DataTable.TableName%2A> ve <xref:System.Data.DataTable.Namespace%2A> birleştirmenin hedefini belirlemek için kullanılır. Hiçbiri <xref:System.Data.DataTable.Namespace%2A> atanmamışsa, <xref:System.Data.DataTable.TableName%2A> yalnızca bir birleştirmenin hedefini tanımlamak için kullanılır.

> [!NOTE]
> Bu davranış .NET Framework sürüm 2,0 ' de değiştirildi. Sürüm 1,1 ' de, ad alanları desteklenmiş ancak birleştirme işlemleri sırasında yok sayıldı. Bu nedenle, özellik değerlerini <xref:System.Data.DataSet> kullanan <xref:System.Data.DataTable.Namespace%2A> bir, çalıştırdığınız .NET Framework sürümüne bağlı olarak farklı davranışlara sahip olacaktır. Örneğin, aynı `DataSets` <xref:System.Data.DataTable.Namespace%2A> `DataTables` özellik<xref:System.Data.DataTable.TableName%2A> değerlerinin ancak farklı özellik değerlerinin bulunduğu iki içeren bir sahip olduğunuzu varsayalım. .NET Framework sürüm 1,1 ' de, iki <xref:System.Data.DataTable.Namespace%2A> <xref:System.Data.DataSet> nesne birleştirilirken farklı adlar yok sayılır. Ancak, sürüm 2,0 ' den itibaren birleştirme, hedefte `DataTables` <xref:System.Data.DataSet>iki yeni oluşturulmasına neden olur. Özgün `DataTables` , birleştirme tarafından etkilenmeyecektir.

## <a name="preservechanges"></a>PreserveChanges

`DataSet` `DataTable`Yöntemine bir, `DataSet`veya `DataRow` dizisi geçirdiğinizde, var olan değişikliklerin korunup korunmayacağını ve yeni şema öğelerinin nasıl işleneceğini belirten isteğe bağlı parametreleri ekleyebilirsiniz `Merge` gelen verilerde. Gelen veriler sonrasında bu parametrelerin ilki, var olan <xref:System.Data.LoadOption.PreserveChanges> `DataSet`değişikliklerin korunup korunmayacağını belirten bir Boole bayrağıdır. Bayrak olarak `true`ayarlandıysa, gelen değerler varolan satırın `Current` satır sürümünde varolan değerlerin üzerine yazmaz. `PreserveChanges` Bayrak olarak `false`ayarlandıysa, gelen değerler varolan satırın `Current` satır sürümünde varolan değerlerin üzerine yazar. `PreserveChanges` Bayrak belirtilmemişse, varsayılan olarak olarak `false` ayarlanır. `PreserveChanges` Satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).

`PreserveChanges` <xref:System.Data.DataRowVersion.Current> `Original` Ne zaman, mevcut satırdaki veriler<xref:System.Data.DataRowVersion.Original> Mevcut satırın satır sürümünde korunur, ancak mevcut satırın satır sürümünden alınan veriler, satırdaki verilerle birlikte yazılır `true` gelen satırın sürümü. Var olan satırın öğesine <xref:System.Data.DataRowState.Modified>ayarlanır. <xref:System.Data.DataRow.RowState%2A> Aşağıdaki özel durumlar geçerlidir:

- `RowState` Var olan satır `Deleted`' a sahipse, bu `RowState` kalır `Deleted` ve olarak `Modified`ayarlanır. Bu durumda, gelen `Original` satırdaki veriler mevcut satırın satır sürümünde depolanmaya devam eder, var olan satırın `Original` satır sürümünün üzerine yazılır ( `Added`gelen satır öğesine sahip `RowState` olmadığı müddetçe).

- `RowState` Gelen satırın `Added` 'a`Original` sahip olması durumunda, gelen satırda bir satır sürümü bulunmadığından, mevcut satırın satırsürümündekiverilerinüzerinegelensatırdakiverileriyazılmaz.`Original`

`PreserveChanges` `Original` `RowState` `RowState` Ne zaman, var olan `Current` satırdaki ve satır sürümlerinin her ikisi de gelen satırdaki verilerle üzerine yazılır ve var olan satır gelen satırın öğesine ayarlanır. `false` Aşağıdaki özel durumlar geçerlidir:

- `RowState` Gelen satır `Deleted` `RowState` `Unchanged` `Modified`' a sahipse ve `Added`var olan satır,, veya`RowState` ' a sahipse, var olan satırın öğesine ayarlanır. `Modified`

- `RowState` Gelen satır `Modified` `Deleted` `Modified`' a `RowState` sahipse ve var olan satır `Unchanged`,, veya`RowState` ' a sahipse, var olan satırın `Added`öğesine ayarlanır. Ayrıca, gelen satır bir `Original` `Original` satır sürümüne sahip olmadığından, mevcut satırın satır sürümündeki verilerin, gelen satırdaki verilerle üzerine yazılmaz.

## <a name="missingschemaaction"></a>MissingSchemaAction

Mevcut <xref:System.Data.MissingSchemaAction> `Merge` `Merge` bir parçasıolmayangelenverilerdekişemaöğelerininasılişleyeceğinizibelirtmekiçinyöntemininisteğebağlıparametresinikullanabilirsiniz.`DataSet`

Aşağıdaki tabloda seçeneklerini `MissingSchemaAction`açıklanmaktadır.

|MissingSchemaAction seçeneği|Açıklama|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Yeni şema bilgilerini öğesine `DataSet` ekleyin ve yeni sütunları gelen değerlerle doldurun. Bu varsayılandır.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Yeni şemayı ve birincil anahtar bilgilerini öğesine `DataSet` ekleyin ve yeni sütunları gelen değerlerle doldurun.|
|<xref:System.Data.MissingSchemaAction.Error>|Eşleşmeyen şema bilgileriyle karşılaşılırsa bir özel durum oluşturur.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Yeni şema bilgilerini yoksayın.|

## <a name="constraints"></a>Kısıtlamalar

Yöntemiyle, tüm yeni veriler mevcut `DataSet`olana kadar kısıtlamalar denetlenmez. `Merge` Veriler eklendikten sonra, içindeki `DataSet`geçerli değerler üzerinde kısıtlamalar zorlanır. Kodunuzun, kısıtlama ihlalleri nedeniyle oluşturulan tüm özel durumları işlediğinden emin olmanız gerekir.

İçindeki `DataSet` mevcut bir satırın `Unchanged` , birincil anahtar değeri 1 olan bir satır olduğu bir durum düşünün. `Modified` Birincil anahtar `Original` `Original` değeri 2 ve birincilanahtardeğeri1olangelensatırasahipbirbirleştirmeişlemisırasında,birincilanahtardeğerlerinedeniylemevcutsatırvegelensatıreşleşenkabuledilmez`Current` olduğu. Ancak, birleştirme tamamlandığında ve kısıtlamalar denetlendiğinde, `Current` birincil anahtar değerleri birincil anahtar sütunu için benzersiz kısıtlamayı ihlal ettiğinden bir özel durum oluşturulur.

> [!NOTE]
> Bir kimlik sütunu gibi bir otomatik artan sütun içeren bir veritabanı tablosuna satırlar yerleştirildiğinde, ekleme tarafından döndürülen kimlik sütunu değeri, içindeki değeriyle eşleşmeyebilir ve `DataSet`döndürülen satırların birleştirilme yerine eklenmesine neden olabilir. Daha fazla bilgi için bkz. [kimlik veya OtomatikSayı değerlerini alma](../retrieving-identity-or-autonumber-values.md).

Aşağıdaki kod örneği iki `DataSet` nesneyi, iki gelen `DataSet` nesnenin birleştirilmiş şemalarıyla `DataSet` farklı şemalarla birleştirir.

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

Aşağıdaki kod örneği, güncelleştirmeleriyle birlikte var `DataSet` olan bir güncelleştirme alır ve bu güncelleştirmeleri veri `DataAdapter` kaynağında işlenmek üzere öğesine geçirir. Sonuçlar bundan sonra orijinalde `DataSet`birleştirilir. Bir hatayla sonuçlanan değişiklikleri reddetmeden sonra, birleştirilmiş değişiklikler ile birlikte `AcceptChanges`kaydedilir.

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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
