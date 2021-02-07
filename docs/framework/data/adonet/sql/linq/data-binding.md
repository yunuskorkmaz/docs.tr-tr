---
description: 'Daha fazla bilgi edinin: veri bağlama'
title: Veri Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: d5566fae505f5c5cd54b2a2990cf04169211003c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729581"
---
# <a name="data-binding"></a>Veri Bağlama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kılavuz denetimleri gibi ortak denetimlere bağlamayı destekler. Özellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veri kılavuzuna bağlama ve Master-Detail bağlamasını işleme için temel desenleri tanımlar ve bunların her ikisi de görüntüleme ve güncelleştirme ' ye göre yapılır.

## <a name="underlying-principle"></a>Temel Ilke

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir veritabanında yürütmek üzere LINQ sorgularını SQL 'e çevirir. Sonuçlar kesin olarak türdedir `IEnumerable` . Bu nesneler sıradan ortak dil çalışma zamanı (CLR) nesneleri olduğundan, sonuçları göstermek için sıradan nesne veri bağlama kullanılabilir. Diğer taraftan, değiştirme işlemleri (ekler, güncelleştirmeler ve silmeler) ek adımlar gerektirir.

## <a name="operation"></a>İşlem

Windows Forms denetimlerine örtük olarak bağlama, uygulama tarafından gerçekleştirilir <xref:System.ComponentModel.IListSource> . Veri kaynakları genel <xref:System.Data.Linq.Table%601> ( `Table<T>` C# ' ta veya `Table(Of T)` Visual Basic) ve genel, `DataQuery` uygulamak üzere güncelleştirilmiştir <xref:System.ComponentModel.IListSource> . Kullanıcı arabirimi (UI) veri bağlama motorları (Windows Forms ve Windows Presentation Foundation) her ikisi de veri kaynağının uygulanıp gösterilmeyeceğini test edin <xref:System.ComponentModel.IListSource> . Bu nedenle, bir denetimin veri kaynağına bir sorgunun doğrudan affectation yazmak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , aşağıdaki örnekte olduğu gibi, koleksiyon oluşturmayı dolaylı olarak çağırır:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Aynı durum Windows Presentation Foundation oluşur:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Koleksiyon oluşturmaları, <xref:System.Data.Linq.Table%601> içinde genel ve genel olarak uygulanır `DataQuery` <xref:System.ComponentModel.IListSource.GetList%2A> .

## <a name="ilistsource-implementation"></a>ISource uygulama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.ComponentModel.IListSource>iki konumda uygular:

- Veri kaynağı bir <xref:System.Data.Linq.Table%601> : tabloya bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] başvuru tutan bir koleksiyonu dolduracak şekilde tabloya gözatar `DataBindingList` .

- Veri kaynağı bir <xref:System.Linq.IQueryable%601> . İki senaryo vardır:

  - , [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Öğesinden temel alınan <xref:System.Data.Linq.Table%601> öğesini bulursa, <xref:System.Linq.IQueryable%601> kaynak sürüme izin verir ve durum ilk madde işareti noktasıyla aynı olur.

  - [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Temel arama bulamazsa <xref:System.Data.Linq.Table%601> , kaynak sürüme izin vermez (örneğin, `groupby` ). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`SortableBindingList` <xref:System.ComponentModel.BindingList%601> belirli bir özellik için T varlıklarının sıralama özelliğini uygulayan basit olan, genel olarak dolduracak şekilde sorguya göz atar.

## <a name="specialized-collections"></a>Özelleştirilmiş Koleksiyonlar

Bu belgede daha önce açıklanan birçok özellik için <xref:System.ComponentModel.BindingList%601> bazı farklı sınıflarda özelleştirilmiş. Bu sınıflar genel `SortableBindingList` ve geneldir `DataBindingList` . Her ikisi de iç olarak bildirilmiştir.

### <a name="generic-sortablebindinglist"></a>Genel SortableBindingList

Bu sınıf öğesinden devralır <xref:System.ComponentModel.BindingList%601> ve sıralanabilir bir sürümüdür <xref:System.ComponentModel.BindingList%601> . Sıralama, bellek içi bir çözümdür ve veritabanının kendisiyle hiçbir şekilde iletişim kurar. <xref:System.ComponentModel.BindingList%601> uygular <xref:System.ComponentModel.IBindingList> ancak varsayılan olarak sıralamayı desteklemez. Ancak, <xref:System.ComponentModel.BindingList%601> <xref:System.ComponentModel.IBindingList> sanal *çekirdek* yöntemleriyle uygular. Bu yöntemleri kolayca geçersiz kılabilirsiniz. Genel `SortableBindingList` geçersiz kılmalar <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A> , <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A> ,, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A> ve <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A> . `ApplySortCore` tarafından çağrılır <xref:System.ComponentModel.IBindingList.ApplySort%2A> ve belirli bir özellik Için T öğelerinin listesini sıralar.

Özellik T 'ye ait değilse bir özel durum tetiklenir.

Sıralamayı başarmak için, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `SortableBindingList.PropertyComparer` genel 'den devralan genel bir sınıf oluşturur <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> ve belirli bir tür T, a ve yön için varsayılan bir karşılaştırıcı uygular `PropertyDescriptor` . Bu sınıf dinamik olarak `Comparer` t 'in öğesinin bulunduğu bir t 'yi oluşturur `PropertyType` `PropertyDescriptor` . Ardından, varsayılan karşılaştırıcı statik genel ' ten alınır `Comparer` . Varsayılan örnek yansıma kullanılarak elde edilir.

Genel `SortableBindingList` Ayrıca için temel sınıftır `DataBindingList` . Genel, `SortableBindingList` öğe ekleme/kaldırma izleme için iki sanal yöntem sunar. Bu iki yöntem sıralama gibi temel özellikler için kullanılabilir, ancak gerçekten genel gibi üst sınıflar tarafından uygulanır `DataBindingList` .

### <a name="generic-databindinglist"></a>Genel DataBindingList

Bu sınıf genel öğesinden devralır `SortableBindingLIst` . Genel, `DataBindingList` `Table` `IQueryable` koleksiyonun ilk doldurulmasıyla ilgili genel genel genelin temel alınarak bir başvuruyu tutar. Genel `DatabindingList` `InsertItem` , () ve () üzerine yazarak koleksiyona ekleme/kaldırma öğesi için izleme ekler `RemoveItem` . Ayrıca, izleme koşullu yapmak için soyut askıya alma/yeniden başlatma izleme özelliğini uygular. Bu özellik genel kullanıma sunar ve `DataBindingList` üst sınıfların izleme özelliğinin tüm polimoral kullanımlarından yararlanır.

## <a name="binding-to-entitysets"></a>EntitySets 'lere bağlama

' A bağlama `EntitySet` işlemi, `EntitySet` zaten uygulayan bir koleksiyon olduğundan özel bir durumdur <xref:System.ComponentModel.IBindingList> . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sıralama ve iptal etme ( <xref:System.ComponentModel.ICancelAddNew> ) desteği ekler. Bir `EntitySet` sınıf varlıkları depolamak için iç liste kullanır. Bu liste, genel bir diziyi, genel sınıfını temel alan alt düzey bir koleksiyondur `ItemList` .

### <a name="adding-a-sorting-feature"></a>Sıralama özelliği ekleme

Diziler `Array.Sort()` , bir T ile kullanabileceğiniz bir sıralama yöntemi () sunar `Comparer` . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `SortableBindingList.PropertyComparer` Bu `Comparer` , özelliği ve sıralanacak yönü almak için bu konuda daha önce açıklanan genel sınıfı kullanır. `ApplySort`Bu özelliği çağırmak için bir yöntem genel 'e eklenir `ItemList` .

`EntitySet`Tarafında, artık sıralama desteği bildirmeniz gerekir:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> döndürür `true` .

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> çağırır `entities.ApplySort()` ve sonra `OnListChanged()` .

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> ve <xref:System.ComponentModel.IBindingList.SortProperty%2A> Özellikleri, yerel üyelerde depolanan geçerli sıralama tanımını kullanıma sunar.

Bir System. Windows. Forms. BindingSource kullandığınızda ve \<TEntity> System. Windows. Forms. BindingSource. DataSource 'a bir EntitySet bağladığınızda, EntitySet 'i çağırmanız gerekir \<TEntity> . BindingSource. List öğesini güncelleştirmek için GetNewBindingList.

Bir System. Windows. Forms. BindingSource kullanın ve BindingSource. DataMember özelliğini ve BindingSource. DataSource ' ı, EntitySet 'i kullanıma sunan BindingSource. DataMember içinde adlı bir sınıfa ayarlarsanız \<TEntity> , EntitySet 'i çağırmanız gerekmez \<TEntity> . BindingSource. List öğesini güncelleştirmek için GetNewBindingList. ancak sıralama özelliğini kaybedersiniz.

## <a name="caching"></a>Önbelleğe Alma

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgular uygular <xref:System.ComponentModel.IListSource.GetList%2A> . Windows Forms BindingSource sınıfı bu arabirimi karşılıyorsa, tek bir bağlantı için GetList () Threes saatini çağırır. Bu durumu geçici olarak çözmek için, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] depolanacak örnek başına bir önbellek uygular ve her zaman aynı oluşturulmuş koleksiyonu döndürür.

## <a name="cancellation"></a>İptal

<xref:System.ComponentModel.IBindingList><xref:System.ComponentModel.IBindingList.AddNew%2A>bir bağlantılı koleksiyondan yeni bir öğe oluşturmak için denetimler tarafından kullanılan bir yöntemi tanımlar. `DataGridView`Denetim, son görünür satır üst bilgisinde yıldız içerdiğinde bu özelliğin çok iyi olduğunu gösterir. Yıldız, size yeni bir öğe ekleyebilmeniz gerektiğini gösterir.

Bu özelliğe ek olarak, bir koleksiyon da uygulanabilir <xref:System.ComponentModel.ICancelAddNew> . Bu özellik, denetimlerin yeni düzenlenmiş öğenin doğrulanıp doğrulanmadığını veya doğrulamasını sağlar.

<xref:System.ComponentModel.ICancelAddNew> Tüm [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama koleksiyonlarında (genel `SortableBindingList` ve genel) uygulanır `EntitySet` . Her iki uygulamada da kod aşağıdaki gibi gerçekleştirilir:

- Öğelerin eklenmesine ve sonra koleksiyondan kaldırılmasına izin verir.

- , Kullanıcı arabirimi sürümü yürütmediğinden değişiklikleri izlemez.

- , Sürüm iptal edildiği () sürece değişiklikleri izlemez <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> .

- Sürüm yürütüldüğü zaman izlemeye izin verir ( <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> ).

- Yeni öğe geldiği takdirde koleksiyonun normal şekilde davranmasına izin verir <xref:System.ComponentModel.IBindingList.AddNew%2A> .

## <a name="troubleshooting"></a>Sorun giderme

Bu bölüm, veri bağlama uygulamalarınızın sorunlarını gidermenize yardımcı olabilecek birkaç öğeyi çağırır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

- Özellikleri kullanmanız gerekir; yalnızca alanların kullanılması yeterli değildir. Windows Forms Bu kullanımı gerektirir.

- Varsayılan olarak, `image` , `varbinary` , ve `timestamp` veritabanı türleri bayt dizisine eşlenir. `ToString()`Bu senaryoda desteklenmediğinden, bu nesneler görüntülenemez.

- Birincil anahtarla eşlenmiş bir sınıf üyesinin bir ayarlayıcısı vardır, ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne kimliği değişikliğini desteklemez. Bu nedenle, eşlemede kullanılan birincil/benzersiz anahtar veritabanında güncelleştirilemez. Kılavuzda bir değişiklik, çağırdığınızda bir özel duruma neden olur <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .

- Bir varlık iki ayrı kılavuzla (örneğin, bir ana ve başka bir ayrıntı) bağlanmışsa, `Delete` ana kılavuzdaki bir, ayrıntı kılavuzuna yayılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
