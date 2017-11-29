---
title: "Veri Bağlama"
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
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7405cf37aaa21f8773952c9e7ed941bc8ae3150b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding"></a>Veri Bağlama
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Kılavuz denetimleri gibi ortak denetimlere bağlama destekler. Özellikle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri kılavuza bağlama ve ana-ayrıntı bağlama, hem görüntüleme ve güncelleme açısından işleme için temel düzenlerden tanımlar.  
  
## <a name="underlying-principle"></a>Temel alınan İlkesi  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çevirir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] SQL sorguları bir veritabanı üzerinde yürütme için. Sonuçları kesin türü belirtilmiş `IEnumerable`. Bu nesneler sıradan ortak dil çalışma zamanı (CLR) nesneleri olduğundan, normal nesne veri bağlama sonuçları görüntülemek için kullanılabilir. Diğer taraftan, değişiklik işlemler (ekler, güncelleştirmeleri ve silme) ek adımlar gerektirir.  
  
## <a name="operation"></a>Çalışma  
 Örtük olarak Windows Forms denetimlerine bağlama gerçekleştirilir uygulayarak <xref:System.ComponentModel.IListSource>. Genel veri kaynakları <xref:System.Data.Linq.Table%601> (`Table<T>` C# veya `Table(Of T)` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ve genel `DataQuery` uygulamak için güncelleştirilmiş <xref:System.ComponentModel.IListSource>. Kullanıcı Arabirimi (UI) veri bağlama altyapısı (Windows Forms ve Windows Presentation Foundation) hem de test uygular kendi veri kaynağı olup olmadığını <xref:System.ComponentModel.IListSource>. Bu nedenle, doğrudan affectation bir sorgunun bir veri kaynağına bir denetimin örtük olarak çağrıları yazma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki örnekteki gibi koleksiyonu oluşturma:  
  
 [!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
 [!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]  
  
 Aynı Windows Presentation Foundation ile oluşur:  
  
 [!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
 [!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]  
  
 Koleksiyon nesli genel uygulanan <xref:System.Data.Linq.Table%601> ve genel `DataQuery` içinde <xref:System.ComponentModel.IListSource.GetList%2A>.  
  
## <a name="ilistsource-implementation"></a>IListSource uygulama  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]uygulayan <xref:System.ComponentModel.IListSource> iki konumda:  
  
-   Veri kaynağı bir <xref:System.Data.Linq.Table%601>: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doldurmak için tablo gözatar bir `DataBindingList` başvuru tablosunda tutar koleksiyonu.  
  
-   Veri kaynağı bir <xref:System.Linq.IQueryable%601>. İki senaryo vardır:  
  
    -   Varsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arka plandaki bulur <xref:System.Data.Linq.Table%601> gelen <xref:System.Linq.IQueryable%601>, kaynak sürümü için izin ve ilk imi olduğu gibi aynı durumdur.  
  
    -   Varsa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] arka plandaki bulunamıyor <xref:System.Data.Linq.Table%601>, kaynak sürümü için izin verme (örneğin, `groupby`). [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Genel doldurmak için sorgu gözatar `SortableBindingList`, basit bir olduğu <xref:System.ComponentModel.BindingList%601> T varlıkların belirli bir özellik için sıralama özelliğini uygular.  
  
## <a name="specialized-collections"></a>Özelleştirilmiş Koleksiyonlar  
 Bu belgede daha önce açıklanan birçok özellik için <xref:System.ComponentModel.BindingList%601> bazı farklı sınıflara özelleştirilmiş. Bu sınıfların genel `SortableBindingList` ve genel `DataBindingList`. Her ikisi de olarak iç bildirilir.  
  
### <a name="generic-sortablebindinglist"></a>Genel SortableBindingList  
 Bu sınıf devraldığı <xref:System.ComponentModel.BindingList%601>, ve sıralanabilir bir sürümü <xref:System.ComponentModel.BindingList%601>. Sıralama bir bellek içi çözümüdür ve hiçbir zaman veritabanı ile iletişim kurar. <xref:System.ComponentModel.BindingList%601>uygulayan <xref:System.ComponentModel.IBindingList> ancak varsayılan olarak sıralamayı desteklemiyor. Ancak, <xref:System.ComponentModel.BindingList%601> uygulayan <xref:System.ComponentModel.IBindingList> sanal *çekirdek* yöntemleri. Bu yöntemler kolayca geçersiz kılabilirsiniz. Genel `SortableBindingList` geçersiz kılmaları <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>, <xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>, <xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A>, ve <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>. `ApplySortCore`tarafından çağrılır <xref:System.ComponentModel.IBindingList.ApplySort%2A> ve belirli bir özellik için T öğelerin listesini sıralar.  
  
 Özelliği için T. ait değil, özel durum oluşturuldu  
  
 Sıralama, elde etmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genel oluşturur `SortableBindingList.PropertyComparer` genel devralan sınıf <xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A> ve belirli bir türde T için varsayılan karşılaştırıcı uygular, `PropertyDescriptor`ve bir yönü. Bu sınıf dinamik olarak oluşturur bir `Comparer` T olduğu t `PropertyType` , `PropertyDescriptor`. Ardından, varsayılan karşılaştırıcı statik genel alınır `Comparer`. Varsayılan bir örnek yansıma yoluyla alınır.  
  
 Genel `SortableBindingList` de temel sınıfı olan `DataBindingList`. Genel `SortableBindingList` askıya alma veya sürdürme öğeleri için iki sanal yöntemi Ekle/Kaldır izleme sunar. Bu iki yöntem sıralama gibi temel özellikler için kullanılabilir, ancak genel gibi üst sınıflar tarafından gerçekten uygulanacak `DataBindingList`.  
  
### <a name="generic-databindinglist"></a>Genel DataBindingList  
 Bu sınıf genel devralır `SortableBindingLIst`. Genel `DataBindingList` arka plandaki üzerinde bir başvuru genel tutar `Table` genel olarak `IQueryable` koleksiyonu ilk doldurma için kullanılan. Genel `DatabindingList` izleme öğe eklemek/kaldırmak için geçersiz kılarak koleksiyona ekler `InsertItem`() ve `RemoveItem`(). Ayrıca, soyut askıya/izleme izleme koşullu yapma özelliği Sürdür uygular. Bu özellik genel kılar `DataBindingList` sınıfları biçimli kullanım üst izleme özelliğinin avantajlarından yararlanmak.  
  
## <a name="binding-to-entitysets"></a>EntitySets bağlama  
 Bağlama `EntitySet` bir özel durum çünkü `EntitySet` uygulayan koleksiyondan zaten <xref:System.ComponentModel.IBindingList>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sıralama ve iptal etme ekler (<xref:System.ComponentModel.ICancelAddNew>) destekler. Bir `EntitySet` sınıfı, varlıkları depolamak için bir iç listesi kullanır. Bu liste genel bir genel dizi dayalı bir alt düzey koleksiyondur `ItemList` sınıfı.  
  
### <a name="adding-a-sorting-feature"></a>Sıralama özelliği ekleme  
 Dizileri sıralama yöntemi sunar (`Array.Sort()`) ile kullanılabilen bir `Comparer` t, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] genel kullanır `SortableBindingList.PropertyComparer` bunu elde etmek için bu konunun önceki bölümlerinde açıklanan sınıfı `Comparer` özelliği ve üzerinde sıralanacak yönü. Bir `ApplySort` yöntemi için genel eklenen `ItemList` bu özellik çağırmak için.  
  
 Üzerinde `EntitySet` yan, artık elinizde sıralama destek bildirmek:  
  
-   <xref:System.ComponentModel.IBindingList.SupportsSorting%2A>döndürür `true`.  
  
-   <xref:System.ComponentModel.IBindingList.ApplySort%2A>çağrıları `entities.ApplySort()` ve ardından `OnListChanged()`.  
  
-   <xref:System.ComponentModel.IBindingList.SortDirection%2A>ve <xref:System.ComponentModel.IBindingList.SortProperty%2A> özelliklerini ortaya yerel üyeleri içinde depolanan geçerli sıralama tanımı.  
  
 Ne zaman bir System.Windows.Forms.BindingSource kullanın ve bir EntitySet bağlamak\<TEntity > System.Windows.Forms.BindingSource.DataSource için EntitySet çağırmalısınız\<Tentity >. BindingSource.List güncelleştirmek için GetNewBindingList.  
  
 Bir System.Windows.Forms.BindingSource kullanmak BindingSource.DataMember özelliğini ayarlayın ve EntitySet gösteren BindingSource.DataMember içinde adlı bir özelliği olan bir sınıfı BindingSource.DataSource koymak varsa\<TEntity >, EntitySet çağrılacak yok\<Tentity >. BindingSource.List ancak güncelleştirmek için GetNewBindingList sıralama özelliği kaybedersiniz.  
  
## <a name="caching"></a>Önbelleğe alma  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sorguları uygulamak <xref:System.ComponentModel.IListSource.GetList%2A>. Windows Forms BindingSource sınıfı bu arabirimi karşıladığında threes için tek bir bağlantı zaman GetList() çağırır. Bu durumu çözmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] depolamak ve her zaman aynı oluşturulan koleksiyon döndürmek için örneği başına bir önbellek uygular.  
  
## <a name="cancellation"></a>İptal Etme  
 <xref:System.ComponentModel.IBindingList>tanımlayan bir <xref:System.ComponentModel.IBindingList.AddNew%2A> denetimleri tarafından yeni bir öğe ilişkili koleksiyondan oluşturmak için kullanılan yöntem. `DataGridView` Bu özellik çok iyi son görünür Satır üstbilgisi içinde bir yıldız içerdiğinde denetim gösterir. Yıldız yeni bir öğe ekleyebilirsiniz gösterir.  
  
 Bu özellik ek olarak, bir koleksiyonu da uygulayabilirsiniz <xref:System.ComponentModel.ICancelAddNew>. Bu özellik, öğe veya doğrulandı iptal etme veya yeni düzenlediğiniz doğrulamak için denetimleri sağlar.  
  
 <xref:System.ComponentModel.ICancelAddNew>Tüm uygulanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veriye bağlı koleksiyonları (genel `SortableBindingList` ve genel `EntitySet`). Her iki uygulamalarında kod şu şekilde gerçekleştirir:  
  
-   Sağlar öğeleri eklenebilecek ve koleksiyondan kaldırıldı.  
  
-   Kullanıcı arabirimini edition yürütme değil sürece değişiklikleri izlemez.  
  
-   Edition iptal sürece değişiklikleri izlemez (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>).  
  
-   Edition işlendiğinde izleme sağlar (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>).  
  
-   Yeni öğe gelen gelmez normal olarak hareket etmesini koleksiyonu sağlar <xref:System.ComponentModel.IBindingList.AddNew%2A>.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu bölümde gidermenize yardımcı olabilecek birçok öğeleri çağrıları, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri bağlama uygulamaları.  
  
-   Özellikleri kullanmanız gerekir; yalnızca alanları kullanmak yeterli değildir. Windows Forms bu kullanımı gerektirir.  
  
-   Varsayılan olarak, `image`, `varbinary`, ve `timestamp` veritabanı türleri eşlemek için bayt dizisi. Çünkü `ToString()` desteklenmiyor Bu senaryoda, bu nesnelerin görüntülenemiyor.  
  
-   Ayarlayıcı, birincil bir anahtar ile eşlenen bir sınıf üyesi olan ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne kimliği değişikliğini desteklemiyor. Bu nedenle, veritabanında eşleme içinde kullanılan birincil/benzersiz anahtar güncelleştirilemez. Çağırdığınızda bir özel durum kılavuz içinde bir değişiklik neden <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Bir varlık iki ayrı kılavuzlarda (örneğin, bir ana ve başka bir ayrıntı) bağlıysa bir `Delete` ana kılavuzda ayrıntılı kılavuz dağıtılmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka plan bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
