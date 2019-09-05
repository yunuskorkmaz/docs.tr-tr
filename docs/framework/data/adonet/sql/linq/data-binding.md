---
title: Veri Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 79a14e787b4fe1aa1b16ad661b11a43b12bdd718
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247374"
---
# <a name="data-binding"></a>Veri Bağlama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kılavuz denetimleri gibi ortak denetimlere bağlamayı destekler. Özellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veri kılavuzuna bağlama ve Master-Detail bağlamasını işleme için temel desenleri tanımlar ve bunların her ikisi de görüntüleme ve güncelleştirme ' ye göre yapılır.

## <a name="underlying-principle"></a>Temel Ilke

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] veritabanında yürütmek için sorguları SQL 'e çevirir. Sonuçlar kesin olarak türdedir `IEnumerable`. Bu nesneler sıradan ortak dil çalışma zamanı (CLR) nesneleri olduğundan, sonuçları göstermek için sıradan nesne veri bağlama kullanılabilir. Diğer taraftan, değiştirme işlemleri (ekler, güncelleştirmeler ve silmeler) ek adımlar gerektirir.

## <a name="operation"></a>Çalışma

Windows Forms denetimlerine örtük olarak bağlama, uygulama <xref:System.ComponentModel.IListSource>tarafından gerçekleştirilir. Veri kaynakları genel <xref:System.Data.Linq.Table%601> (`Table<T>` Visual Basic C# içinde `Table(Of T)` veya içinde) ve genel `DataQuery` , uygulamak <xref:System.ComponentModel.IListSource>üzere güncelleştirilmiştir. Kullanıcı arabirimi (UI) veri bağlama motorları (Windows Forms ve Windows Presentation Foundation) her ikisi de veri kaynağının <xref:System.ComponentModel.IListSource>uygulanıp gösterilmeyeceğini test edin. Bu nedenle, bir denetimin veri kaynağına bir sorgunun doğrudan affectation yazmak, aşağıdaki örnekte olduğu gibi, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] koleksiyon oluşturmayı dolaylı olarak çağırır:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Aynı durum Windows Presentation Foundation oluşur:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Koleksiyon oluşturmaları, içinde <xref:System.Data.Linq.Table%601> <xref:System.ComponentModel.IListSource.GetList%2A>genel ve genel `DataQuery` olarak uygulanır.

## <a name="ilistsource-implementation"></a>ISource uygulama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]iki <xref:System.ComponentModel.IListSource> konumda uygular:

- Veri kaynağı bir <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tabloya bir başvuru tutan bir `DataBindingList` koleksiyonu dolduracak şekilde tabloya gözatar.

- Veri kaynağı bir <xref:System.Linq.IQueryable%601>. İki senaryo vardır:

  - <xref:System.Data.Linq.Table%601> ,Öğesinden<xref:System.Linq.IQueryable%601>temel alınan öğesini bulursa,kaynaksürümeizinverirvedurumilkmaddeişaretinoktasıylaaynıolur.[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

  - Temel arama bulamazsa, kaynak sürüme izin vermez (örneğin, `groupby`). <xref:System.Data.Linq.Table%601> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]belirli bir özellik için T varlıklarının sıralama `SortableBindingList`özelliğini uygulayan basit <xref:System.ComponentModel.BindingList%601> olan, genel olarak dolduracak şekilde sorguya göz atar.

## <a name="specialized-collections"></a>Özelleştirilmiş Koleksiyonlar

Bu belgede <xref:System.ComponentModel.BindingList%601> daha önce açıklanan birçok özellik için bazı farklı sınıflarda özelleştirilmiş. Bu sınıflar genel `SortableBindingList` ve geneldir `DataBindingList`. Her ikisi de iç olarak bildirilmiştir.

### <a name="generic-sortablebindinglist"></a>Genel SortableBindingList

Bu sınıf öğesinden <xref:System.ComponentModel.BindingList%601>devralır ve sıralanabilir bir <xref:System.ComponentModel.BindingList%601>sürümüdür. Sıralama, bellek içi bir çözümdür ve veritabanının kendisiyle hiçbir şekilde iletişim kurar. <xref:System.ComponentModel.BindingList%601>uygular <xref:System.ComponentModel.IBindingList> ancak varsayılan olarak sıralamayı desteklemez. Ancak, <xref:System.ComponentModel.BindingList%601> sanal <xref:System.ComponentModel.IBindingList> *çekirdek* yöntemleriyle uygular. Bu yöntemleri kolayca geçersiz kılabilirsiniz. Genel `SortableBindingList` geçersiz <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>kılmalar ,<xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A> ,<xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, ve<xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore`tarafından <xref:System.ComponentModel.IBindingList.ApplySort%2A> çağrılır ve belirli bir özellik için T öğelerinin listesini sıralar.

Özellik T 'ye ait değilse bir özel durum tetiklenir.

Sıralamayı başarmak için, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genel <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> 'den devralan `SortableBindingList.PropertyComparer` genel bir sınıf oluşturur ve belirli bir tür T, a `PropertyDescriptor`ve yön için varsayılan bir karşılaştırıcı uygular. Bu sınıf dinamik olarak t `Comparer` `PropertyType` 'in öğesinin `PropertyDescriptor`bulunduğu bir t 'yi oluşturur. Ardından, varsayılan karşılaştırıcı statik genel `Comparer`' ten alınır. Varsayılan örnek yansıma kullanılarak elde edilir.

Genel `SortableBindingList` Ayrıca için `DataBindingList`temel sınıftır. Genel `SortableBindingList` , öğe ekleme/kaldırma izleme için iki sanal yöntem sunar. Bu iki yöntem sıralama gibi temel özellikler için kullanılabilir, ancak gerçekten genel `DataBindingList`gibi üst sınıflar tarafından uygulanır.

### <a name="generic-databindinglist"></a>Genel DataBindingList

Bu sınıf genel `SortableBindingLIst`öğesinden devralır. Genel `DataBindingList` , koleksiyonun ilk doldurulmasıyla ilgili genel `Table` `IQueryable` genel genelin temel alınarak bir başvuruyu tutar. Genel `DatabindingList` , () ve `RemoveItem`() üzerine `InsertItem`yazarak koleksiyona ekleme/kaldırma öğesi için izleme ekler. Ayrıca, izleme koşullu yapmak için soyut askıya alma/yeniden başlatma izleme özelliğini uygular. Bu özellik genel `DataBindingList` kullanıma sunar ve üst sınıfların izleme özelliğinin tüm polimoral kullanımlarından yararlanır.

## <a name="binding-to-entitysets"></a>EntitySets 'lere bağlama

' A bağlama <xref:System.ComponentModel.IBindingList> `EntitySet` `EntitySet` işlemi, zaten uygulayan bir koleksiyon olduğundan özel bir durumdur. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sıralama ve iptal etme (<xref:System.ComponentModel.ICancelAddNew>) desteği ekler. Bir `EntitySet` sınıf varlıkları depolamak için iç liste kullanır. Bu liste, genel bir diziyi, genel `ItemList` sınıfını temel alan alt düzey bir koleksiyondur.

### <a name="adding-a-sorting-feature"></a>Sıralama özelliği ekleme

Diziler, bir `Comparer` T ile kullanabileceğiniz`Array.Sort()`bir sıralama yöntemi () sunar. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bu `Comparer` , özelliği ve sıralanacak yönü almak `SortableBindingList.PropertyComparer` için bu konuda daha önce açıklanan genel sınıfı kullanır. Bu `ApplySort` özelliği çağırmak için bir yöntem `ItemList` genel 'e eklenir.

`EntitySet` Tarafında, artık sıralama desteği bildirmeniz gerekir:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A>döndürür `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A>çağırır `entities.ApplySort()` ve sonra `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A>ve <xref:System.ComponentModel.IBindingList.SortProperty%2A> özellikleri, yerel üyelerde depolanan geçerli sıralama tanımını kullanıma sunar.

System. Windows. Forms. BindingSource 'u kullandığınızda ve System. Windows. Forms\<. BindingSource. DataSource 'a bir EntitySet TEntity > bağladığınızda, EntitySet\<TEntity > çağırmanız gerekir. BindingSource. List öğesini güncelleştirmek için GetNewBindingList.

Bir System. Windows. Forms. BindingSource kullanın ve BindingSource. DataMember özelliğini ve BindingSource. DataSource ' ı\<TEntity > sunan BindingSource. DataMember içinde adlı bir sınıfa ayarlarsanız, EntitySet\<TEntity > çağırmanız gerekmez. BindingSource. List öğesini güncelleştirmek için GetNewBindingList. ancak sıralama özelliğini kaybedersiniz.

## <a name="caching"></a>Önbelleğe Alma

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sorgular uygular <xref:System.ComponentModel.IListSource.GetList%2A>. Windows Forms BindingSource sınıfı bu arabirimi karşılıyorsa, tek bir bağlantı için GetList () Threes saatini çağırır. Bu durumu geçici olarak çözmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , depolanacak örnek başına bir önbellek uygular ve her zaman aynı oluşturulmuş koleksiyonu döndürür.

## <a name="cancellation"></a>İptal Etme

<xref:System.ComponentModel.IBindingList>bir bağlantılı <xref:System.ComponentModel.IBindingList.AddNew%2A> koleksiyondan yeni bir öğe oluşturmak için denetimler tarafından kullanılan bir yöntemi tanımlar. Denetim `DataGridView` , son görünür satır üst bilgisinde yıldız içerdiğinde bu özelliğin çok iyi olduğunu gösterir. Yıldız, size yeni bir öğe ekleyebilmeniz gerektiğini gösterir.

Bu özelliğe ek olarak, bir koleksiyon da <xref:System.ComponentModel.ICancelAddNew>uygulanabilir. Bu özellik, denetimlerin yeni düzenlenmiş öğenin doğrulanıp doğrulanmadığını veya doğrulamasını sağlar.

<xref:System.ComponentModel.ICancelAddNew>Tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama koleksiyonlarında (genel `SortableBindingList` ve genel `EntitySet`) uygulanır. Her iki uygulamada da kod aşağıdaki gibi gerçekleştirilir:

- Öğelerin eklenmesine ve sonra koleksiyondan kaldırılmasına izin verir.

- , Kullanıcı arabirimi sürümü yürütmediğinden değişiklikleri izlemez.

- , Sürüm iptal edildiği (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>) sürece değişiklikleri izlemez.

- Sürüm yürütüldüğü zaman izlemeye izin verir (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Yeni öğe <xref:System.ComponentModel.IBindingList.AddNew%2A>geldiği takdirde koleksiyonun normal şekilde davranmasına izin verir.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölüm, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama uygulamalarınızın sorunlarını gidermenize yardımcı olabilecek birkaç öğeyi çağırır.

- Özellikleri kullanmanız gerekir; yalnızca alanların kullanılması yeterli değildir. Windows Forms Bu kullanımı gerektirir.

- Varsayılan `image` `timestamp` olarak,, ,veveritabanıtürleribaytdizisineeşlenir.`varbinary` `ToString()` Bu senaryoda desteklenmediğinden, bu nesneler görüntülenemez.

- Birincil anahtarla eşlenmiş bir sınıf üyesinin bir ayarlayıcısı vardır, ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne kimliği değişikliğini desteklemez. Bu nedenle, eşlemede kullanılan birincil/benzersiz anahtar veritabanında güncelleştirilemez. Kılavuzda bir değişiklik, çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>bir özel duruma neden olur.

- Bir varlık iki ayrı kılavuzla (örneğin, bir ana ve başka bir ayrıntı) bağlanmışsa, ana kılavuzdaki bir `Delete` , ayrıntı kılavuzuna yayılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
