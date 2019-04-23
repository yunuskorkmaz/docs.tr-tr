---
title: Veri Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
ms.openlocfilehash: 66964497159c5c03a9070090ee60b43fa7d31abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978932"
---
# <a name="data-binding"></a>Veri Bağlama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Kılavuz denetimleri gibi ortak denetimler bağlama destekler. Özellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kılavuzu için bağlama ve ana öğe-ayrıntı bağlama, hem görüntüleme ve güncelleştirme işleme için temel desenleri tanımlar.

## <a name="underlying-principle"></a>Temel alınan İlkesi

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] SQL sorguları yürütme bir veritabanı için. Sonuçları kesin `IEnumerable`. Bu nesneler Normal ortak dil çalışma zamanı (CLR) nesneleri olduğundan, sıradan bir nesne veri bağlama sonuçları görüntülemek için kullanılabilir. Öte yandan, değişiklik işlemleri (ekleme, güncelleştirme ve silme) ek adımlar gerektirir.

## <a name="operation"></a>Çalışma

Windows Forms denetimleri için örtük olarak bağlama gerçekleştirilir uygulayarak <xref:System.ComponentModel.IListSource>. Genel veri kaynakları <xref:System.Data.Linq.Table%601> (`Table<T>` içinde C# veya `Table(Of T)` Visual Basic'te) ve genel `DataQuery` uygulamak için güncelleştirilen <xref:System.ComponentModel.IListSource>. Kullanıcı Arabirimi (UI) veri bağlama altyapısı (Windows Forms ve Windows Presentation Foundation) hem de uygular, veri kaynağı olup olmadığını test <xref:System.ComponentModel.IListSource>. Bu nedenle, sorgu doğrudan bir affectation bir veri kaynağına bir denetimin örtük olarak çağrıları yazma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki örnekte olduğu gibi koleksiyon oluşturma:

[!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
[!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]

Aynı Windows Presentation Foundation ile oluşur:

[!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
[!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]

Toplama kuşakları genel uygulanan <xref:System.Data.Linq.Table%601> ve genel `DataQuery` içinde <xref:System.ComponentModel.IListSource.GetList%2A>.

## <a name="ilistsource-implementation"></a>IListSource uygulama

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygulayan <xref:System.ComponentModel.IListSource> iki konumda:

- Veri kaynağı bir <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gözatar tabloyu doldurmak için bir `DataBindingList` tablosunda bir başvuru tutan bir koleksiyon.

- Veri kaynağı bir <xref:System.Linq.IQueryable%601>. İki senaryo vardır:

  - Varsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel bulur <xref:System.Data.Linq.Table%601> gelen <xref:System.Linq.IQueryable%601>, kaynak sürümü için izin verir ve ilk madde işaretinde olduğu gibi bir durumdur.

  - Varsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] temel bulunamıyor <xref:System.Data.Linq.Table%601>, kaynak sürümü için izin vermez (örneğin, `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Genel doldurmak için sorgu gözatar `SortableBindingList`, basit olduğu <xref:System.ComponentModel.BindingList%601> , belirli bir özellik için T varlıklar için sıralama özelliği uygular.

## <a name="specialized-collections"></a>Özelleştirilmiş Koleksiyonlar

Bu belgede daha önce açıklanan birçok özellik için <xref:System.ComponentModel.BindingList%601> bazı farklı sınıfları için özel. Bu sınıfların genel `SortableBindingList` ve genel `DataBindingList`. Her ikisi de internal olarak bildirilir.

### <a name="generic-sortablebindinglist"></a>Genel SortableBindingList

Bu sınıf devraldığı <xref:System.ComponentModel.BindingList%601>, ve sıralanabilir bir sürümü <xref:System.ComponentModel.BindingList%601>. Sıralama, bir bellek içi çözümüdür ve hiçbir zaman veritabanı ile iletişim kurar. <xref:System.ComponentModel.BindingList%601> uygulayan <xref:System.ComponentModel.IBindingList> ancak varsayılan olarak sıralamayı desteklemiyor. Ancak, <xref:System.ComponentModel.BindingList%601> uygulayan <xref:System.ComponentModel.IBindingList> sanal *çekirdek* yöntemleri. Bu yöntemler, bir kolayca kılabilirsiniz. Genel `SortableBindingList` geçersiz kılmalar <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, ve <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore` çağıran <xref:System.ComponentModel.IBindingList.ApplySort%2A> ve belirli bir özellik için T öğelerin listesini sıralar.

Özellik T'ye ait değilse bir özel durum oluşturulur

Sıralama, elde etmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genel oluşturur `SortableBindingList.PropertyComparer` genel devralan sınıf <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> ve T verilen tür için bir varsayılan karşılaştırıcı uygular, `PropertyDescriptor`ve bir yönü. Bu sınıf dinamik olarak bir `Comparer` Burada T, t `PropertyType` , `PropertyDescriptor`. Ardından, varsayılan karşılaştırıcı statik genel alınır `Comparer`. Varsayılan bir örnek, yansıma yoluyla alınır.

Genel `SortableBindingList` de temel sınıfı olan `DataBindingList`. Genel `SortableBindingList` askıya alma veya sürdürme öğeleri için iki sanal yöntemler ekleme/kaldırma izleme sunar. Bu iki yöntem sıralama gibi temel özellikleri için kullanılabilir, ancak gerçekten üst sınıflar gibi genel tarafından uygulanacaktır `DataBindingList`.

### <a name="generic-databindinglist"></a>Genel DataBindingList

Bu sınıf genel devralır `SortableBindingLIst`. Genel `DataBindingList` genel arka plandaki üzerinde bir başvuru tutar `Table` genel, `IQueryable` koleksiyonun ilk doldurma için kullanılır. Genel `DatabindingList` izleme öğesi Ekle/Kaldır için'geçersiz kılarak koleksiyonuna ekler `InsertItem`() ve `RemoveItem`(). Ayrıca, soyut askıya alma/izleme özelliğini izleme koşullu olarak yapmak için sürdürme uygular. Bu özellik genel kılar `DataBindingList` sınıfları izleme özelliğinin bir üst grubun tüm polimorfik kullanım yararlanın.

## <a name="binding-to-entitysets"></a>Entityset'i bağlama

Bağlama `EntitySet` özel bir durum olduğundan `EntitySet` uygulayan koleksiyondan zaten <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Sıralama ve iptal etme ekler (<xref:System.ComponentModel.ICancelAddNew>) destekler. Bir `EntitySet` sınıfı, varlıkları depolamak için bir iç listesi kullanır. Bu bir listedir genel bir genel dizi göre düşük düzeyde bir toplama `ItemList` sınıfı.

### <a name="adding-a-sorting-feature"></a>Sıralama özelliği ekleme

Diziler sunan sort yöntemi (`Array.Sort()`) ile kullanılabilecek bir `Comparer` t, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genel kullanır `SortableBindingList.PropertyComparer` bunu elde etmek için bu konuda daha önce açıklanan sınıfı `Comparer` özelliği ve üzerinde sıralanacak yönü. Bir `ApplySort` yöntemi için genel eklenen `ItemList` bu özellik çağırmak için.

Üzerinde `EntitySet` tarafı, artık sahip olduğunuz sıralama desteği bildirmek:

- <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> döndürür `true`.

- <xref:System.ComponentModel.IBindingList.ApplySort%2A> çağrıları `entities.ApplySort()` ardından `OnListChanged()`.

- <xref:System.ComponentModel.IBindingList.SortDirection%2A> ve <xref:System.ComponentModel.IBindingList.SortProperty%2A> özellikleri yerel Üyeler'de depolanan geçerli sıralama tanımını gösterin.

Ne zaman bir System.Windows.Forms.BindingSource kullanın ve bir EntitySet bağlama\<TEntity > System.Windows.Forms.BindingSource.DataSource için EntitySet çağırmalıdır\<TEntity >. GetNewBindingList BindingSource.List güncelleştirilecek.

Bir System.Windows.Forms.BindingSource kullanın BindingSource.DataMember özelliğini ayarlayın ve Entityset'i sunan BindingSource.DataMember içinde adında bir özelliğe sahip bir sınıf için BindingSource.DataSource ayarlayın,\<TEntity >, EntitySet çağırmak zorunda değilsiniz\<TEntity >. BindingSource.List ancak güncelleştirilecek GetNewBindingList sıralama özelliğini kaybedersiniz.

## <a name="caching"></a>Önbelleğe Alma

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları <xref:System.ComponentModel.IListSource.GetList%2A>. Windows Forms BindingSource sınıfı bu arabirimi karşıladığında threes için tek bir bağlantı zaman GetList() çağırır. Bu durumu çözmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] depolamak ve her zaman aynı oluşturulan koleksiyon döndürmek için örnek başına bir önbellek uygular.

## <a name="cancellation"></a>İptal Etme

<xref:System.ComponentModel.IBindingList> tanımlayan bir <xref:System.ComponentModel.IBindingList.AddNew%2A> denetimleri tarafından bağlanmış bir derlemeden yeni bir öğe oluşturmak için kullanılan yöntem. `DataGridView` Bu özellik çok iyi kendi üst bilgisindeki bir yıldız görünür son satır içerdiğinde denetimi gösterir. Yıldız yeni bir öğe ekleyebileceğiniz gösterilmektedir.

Bu özellik ek olarak, bir koleksiyon de uygulayabilirsiniz <xref:System.ComponentModel.ICancelAddNew>. Bu özellik, öğe veya doğrulandı iptal etme veya yeni düzenlenebilir olduğunu doğrulamak için denetimleri sağlar.

<xref:System.ComponentModel.ICancelAddNew> Tüm uygulanan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] databound koleksiyonları (genel `SortableBindingList` ve genel `EntitySet`). Her iki uygulamada da bulunan kodu aşağıdaki şekilde gerçekleştirir:

- Sağlar öğeleri eklenebilecek ve sonra koleksiyondan kaldırılır.

- Kullanıcı Arabirimi sürümü kaydetmeyen bir işlevi sürece değişiklikleri izlemiyor.

- Sürüm iptal sürece değişiklikleri izlemiyor (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).

- Sürüm işlendiğinde izleme sağlar (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).

- Yeni öğe nereden geliyor değil, normal şekilde davranır koleksiyonu sağlar <xref:System.ComponentModel.IBindingList.AddNew%2A>.

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde gidermenize yardımcı olabilecek birkaç öğeleri çağırır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama uygulamaları.

- Özellikleri kullanmanız gerekir; yalnızca alanlara kullanarak yeterli değildir. Windows Forms, bu kullanımı gerektirir.

- Varsayılan olarak, `image`, `varbinary`, ve `timestamp` veritabanı türleriyle eşlenmesini bayt dizisi. Çünkü `ToString()` desteklenmeyen Bu senaryoda, bu nesneler görüntülenemiyor.

- Bir ayarlayıcı birincil anahtara eşlenen bir sınıf üyesine sahiptir ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne kimliği değişikliğini desteklemez. Bu nedenle, eşlemede kullanılan birincil/benzersiz anahtar veritabanında güncelleştirilemez. Çağırdığınızda kılavuzundaki bir değişiklik neden olan bir özel durum <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

- Varlığın iki ayrı kılavuzlarda (örneğin, bir ana ve başka bir ayrıntı) bağlıysa bir `Delete` ayrıntılı kılavuz için ana kılavuz dağıtılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
