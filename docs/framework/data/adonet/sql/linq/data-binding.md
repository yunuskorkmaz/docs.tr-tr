---
title: Veri Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: c7048d292bdf5c1372d5f8f174f7f0e84efa7593
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634722"
---
# <a name="data-binding"></a>Veri Bağlama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], kılavuz denetimleri gibi ortak denetimlere bağlamayı destekler. Özellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veri kılavuzuna bağlama ve Master-Detail bağlamasını işleme için temel desenleri tanımlar ve bunların her ikisi de görüntüleme ve güncelleştirme ' ye göre yapılır.

## <a name="underlying-principle"></a>Temel Ilke

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanında yürütmek üzere LINQ sorgularını SQL 'e çevirir. Sonuçların türü kesin olarak belirlenmiş `IEnumerable`. Bu nesneler sıradan ortak dil çalışma zamanı (CLR) nesneleri olduğundan, sonuçları göstermek için sıradan nesne veri bağlama kullanılabilir. Diğer taraftan, değiştirme işlemleri (ekler, güncelleştirmeler ve silmeler) ek adımlar gerektirir.

## <a name="operation"></a>Çalışma

Windows Forms denetimlerine örtük olarak bağlama, <xref:System.ComponentModel.IListSource>uygulayarak gerçekleştirilir. Veri kaynakları genel <xref:System.Data.Linq.Table%601> (Visual Basic içinde C#`Table<T>` veya `Table(Of T)`) ve genel `DataQuery`, <xref:System.ComponentModel.IListSource>uygulamak üzere güncelleştirilmiştir. Kullanıcı arabirimi (UI) veri bağlama motorları (Windows Forms ve Windows Presentation Foundation) her ikisi de, veri kaynağının <xref:System.ComponentModel.IListSource>uygulayıp uygulamadığını test edin. Bu nedenle, bir denetimin veri kaynağına bir sorgunun doğrudan affectation yazmak, aşağıdaki örnekte olduğu gibi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koleksiyon oluşturmayı dolaylı olarak çağırır:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Aynı durum Windows Presentation Foundation oluşur:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Koleksiyon oluşturmaları, <xref:System.ComponentModel.IListSource.GetList%2A>genel <xref:System.Data.Linq.Table%601> ve genel `DataQuery` tarafından uygulanır.

## <a name="ilistsource-implementation"></a>ISource uygulama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iki konumda <xref:System.ComponentModel.IListSource> uygular:

- Veri kaynağı bir <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tablo üzerinde bir başvuru tutan bir `DataBindingList` koleksiyonunu dolduracak şekilde tabloya göz atar.

- Veri kaynağı bir <xref:System.Linq.IQueryable%601>. İki senaryo vardır:

  - [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel <xref:System.Data.Linq.Table%601> <xref:System.Linq.IQueryable%601>bulursa, kaynak sürüme izin verir ve durum ilk madde işareti noktasıyla aynı olur.

  - [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel <xref:System.Data.Linq.Table%601>bulamazsa, kaynak sürüme izin vermez (örneğin, `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], belirli bir özellik için T varlıklarının sıralama özelliğini uygulayan basit bir <xref:System.ComponentModel.BindingList%601> olan genel bir `SortableBindingList`dolduracak şekilde sorguya göz atar.

## <a name="specialized-collections"></a>Özelleştirilmiş Koleksiyonlar

Bu belgede daha önce açıklanan birçok özellik için <xref:System.ComponentModel.BindingList%601> bazı farklı sınıflara göre özelleştirilmiştir. Bu sınıflar genel `SortableBindingList` ve genel `DataBindingList`. Her ikisi de iç olarak bildirilmiştir.

### <a name="generic-sortablebindinglist"></a>Genel SortableBindingList

Bu sınıf <xref:System.ComponentModel.BindingList%601>devralır ve <xref:System.ComponentModel.BindingList%601>sıralanabilir bir sürümdür. Sıralama, bellek içi bir çözümdür ve veritabanının kendisiyle hiçbir şekilde iletişim kurar. <xref:System.ComponentModel.BindingList%601> <xref:System.ComponentModel.IBindingList> uygular, ancak sıralamayı varsayılan olarak desteklemez. Ancak, <xref:System.ComponentModel.BindingList%601> sanal *çekirdek* yöntemleriyle <xref:System.ComponentModel.IBindingList> uygular. Bu yöntemleri kolayca geçersiz kılabilirsiniz. Genel `SortableBindingList` <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>ve <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>geçersiz kılar. `ApplySortCore`, <xref:System.ComponentModel.IBindingList.ApplySort%2A> tarafından çağrılır ve belirli bir özellik için T öğelerinin listesini sıralar.

Özellik T 'ye ait değilse bir özel durum tetiklenir.

Sıralama gerçekleştirmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], genel <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> devralan genel bir `SortableBindingList.PropertyComparer` sınıfı oluşturur ve verili bir tür T, `PropertyDescriptor`ve Direction için varsayılan bir karşılaştırıcı uygular. Bu sınıf, t 'in `PropertyDescriptor``PropertyType` t `Comparer` dinamik olarak oluşturur. Ardından, varsayılan karşılaştırıcı statik genel `Comparer`alınır. Varsayılan örnek yansıma kullanılarak elde edilir.

Genel `SortableBindingList` Ayrıca `DataBindingList`için temel sınıftır. Genel `SortableBindingList`, öğe ekleme/kaldırma izleme için iki sanal yöntem sunar. Bu iki yöntem sıralama gibi temel özellikler için kullanılabilir ancak gerçekten genel `DataBindingList`gibi üst sınıflar tarafından uygulanır.

### <a name="generic-databindinglist"></a>Genel DataBindingList

Bu sınıf genel `SortableBindingLIst`devralır. Genel `DataBindingList`, koleksiyonun ilk doldurulmasıyla kullanılan genel `IQueryable` temel alınan genel `Table` bir başvuruyu tutar. Genel `DatabindingList`, `InsertItem`() ve `RemoveItem`() üzerine yazarak koleksiyona ekleme/kaldırma öğesi için izleme ekler. Ayrıca, izleme koşullu yapmak için soyut askıya alma/yeniden başlatma izleme özelliğini uygular. Bu özellik genel `DataBindingList`, üst sınıfların izleme özelliğinin tüm polimoral kullanımından yararlanmasını sağlar.

## <a name="binding-to-entitysets"></a>EntitySets 'lere bağlama

`EntitySet` zaten <xref:System.ComponentModel.IBindingList>uygulayan bir koleksiyon olduğundan `EntitySet` bağlama işlemi özel bir durumdur. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sıralama ve iptal etme (<xref:System.ComponentModel.ICancelAddNew>) desteği ekler. `EntitySet` bir sınıf varlıkları depolamak için iç liste kullanır. Bu liste genel bir diziyi, genel `ItemList` sınıfını temel alan alt düzey bir koleksiyondur.

### <a name="adding-a-sorting-feature"></a>Sıralama özelliği ekleme

Diziler, T `Comparer` birlikte kullanabileceğiniz bir sıralama yöntemi (`Array.Sort()`) sağlar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bu `Comparer` özellik için bu elde etmek üzere bu konunun önceki kısımlarında açıklanan genel `SortableBindingList.PropertyComparer` sınıfını kullanır. Bu özelliği çağırmak için genel `ItemList` bir `ApplySort` yöntemi eklenmiştir.

`EntitySet` tarafında, artık sıralama desteği bildirmeniz gerekir:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> `true`döndürür.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> `entities.ApplySort()` çağırır ve `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> ve <xref:System.ComponentModel.IBindingList.SortProperty%2A> özellikleri, yerel üyelerde depolanan geçerli sıralama tanımını kullanıma sunar.

System. Windows. Forms. BindingSource 'u kullandığınızda ve System. Windows. Forms. BindingSource. DataSource 'a bir EntitySet\<TEntity > bağladığınızda, EntitySet\<TEntity > çağırmanız gerekir. BindingSource. List öğesini güncelleştirmek için GetNewBindingList.

System. Windows. Forms. BindingSource kullanın ve BindingSource. DataMember özelliğini ve BindingSource. DataSource ' u\<TEntity > 'yi kullanıma sunan BindingSource. DataMember içinde adlı bir sınıfa ayarladıysanız, EntitySet\<TEntity > çağırmanız gerekmez. BindingSource. List öğesini güncelleştirmek için GetNewBindingList. ancak sıralama özelliğini kaybedersiniz.

## <a name="caching"></a>Önbelleğe Alma

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları <xref:System.ComponentModel.IListSource.GetList%2A>uygular. Windows Forms BindingSource sınıfı bu arabirimi karşılıyorsa, tek bir bağlantı için GetList () Threes saatini çağırır. Bu duruma geçici bir çözüm için, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] depolanacak örnek başına bir önbellek uygular ve her zaman aynı oluşturulmuş koleksiyonu döndürür.

## <a name="cancellation"></a>İptal Etme

<xref:System.ComponentModel.IBindingList>, bağlantılı bir koleksiyondan yeni bir öğe oluşturmak için denetimler tarafından kullanılan bir <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi tanımlar. `DataGridView` denetimi, son görünür satır üst bilgisinde bir yıldız içerdiğinde bu özelliğin çok iyi olduğunu gösterir. Yıldız, size yeni bir öğe ekleyebilmeniz gerektiğini gösterir.

Bu özelliğe ek olarak, bir koleksiyon de <xref:System.ComponentModel.ICancelAddNew>uygulayabilir. Bu özellik, denetimlerin yeni düzenlenmiş öğenin doğrulanıp doğrulanmadığını veya doğrulamasını sağlar.

<xref:System.ComponentModel.ICancelAddNew> tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri sınırlama koleksiyonlarında (genel `SortableBindingList` ve genel `EntitySet`) uygulanır. Her iki uygulamada da kod aşağıdaki gibi gerçekleştirilir:

- Öğelerin eklenmesine ve sonra koleksiyondan kaldırılmasına izin verir.

- , Kullanıcı arabirimi sürümü yürütmediğinden değişiklikleri izlemez.

- Sürüm iptal edildiği sürece değişiklikleri izlemez (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Sürüm yürütüldüğü sırada izlemeye izin verir (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Yeni öğe <xref:System.ComponentModel.IBindingList.AddNew%2A>gelmediğinde koleksiyonun normal şekilde davranmasına izin verir.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölüm, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama uygulamalarınızın sorunlarını gidermenize yardımcı olabilecek birkaç öğeyi çağırır.

- Özellikleri kullanmanız gerekir; yalnızca alanların kullanılması yeterli değildir. Windows Forms Bu kullanımı gerektirir.

- Varsayılan olarak, `image`, `varbinary`ve `timestamp` veritabanı türleri bayt dizisine eşlenir. `ToString()` Bu senaryoda desteklenmediğinden, bu nesneler görüntülenemez.

- Birincil anahtarla eşlenmiş bir sınıf üyesinin bir ayarlayıcısı vardır, ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne kimliği değişikliğini desteklemez. Bu nedenle, eşlemede kullanılan birincil/benzersiz anahtar veritabanında güncelleştirilemez. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>çağırdığınızda kılavuzdaki bir değişiklik bir özel duruma neden olur.

- Bir varlık iki ayrı kılavuzla (örneğin, bir ana ve başka bir ayrıntı) bağlanmışsa, ana kılavuzdaki bir `Delete` ayrıntı kılavuzuna yayılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
