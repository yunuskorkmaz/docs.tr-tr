---
title: Nesne Durumları ve Değişiklik İzleme
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: a60afab5158d0d5f66d12d6913ee890abc8ca730
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043514"
---
# <a name="object-states-and-change-tracking"></a>Nesne Durumları ve Değişiklik İzleme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nesneler her zaman bir *duruma*katılır. Örneğin, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni bir nesne oluşturduğunda, nesne `Unchanged` durumundadır. Sizin oluşturduğunuz yeni bir nesne, <xref:System.Data.Linq.DataContext> ve `Untracked` için bilinmiyor durumundadır. ' Nin <xref:System.Data.Linq.DataContext.SubmitChanges%2A>başarılı yürütmesi, ' de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Unchanged` bilinen tüm nesneler durumunda. (Tek istisna, veritabanından `Deleted` başarıyla silinenler tarafından temsil edilir ve bu <xref:System.Data.Linq.DataContext> örnekte kullanılamaz durumda olabilir.)

## <a name="object-states"></a>Nesne durumları

Aşağıdaki tabloda nesneler için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] olası durumlar listelenmektedir.

|Durum|Açıklama|
|-----------|-----------------|
|`Untracked`|Tarafından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]izlenmeyen bir nesne. Örnekler şunlardır:<br /><br /> -Geçerli <xref:System.Data.Linq.DataContext> bir nesne (yeni oluşturulan nesne gibi) aracılığıyla sorgulanmadı.<br />-Serisini kaldırma ile oluşturulan nesne<br />-Farklı <xref:System.Data.Linq.DataContext>bir ile sorgulanan bir nesne.|
|`Unchanged`|Geçerli <xref:System.Data.Linq.DataContext> ve oluşturulduktan sonra değiştirilmiş olarak bilinen bir nesne.|
|`PossiblyModified`|Öğesine<xref:System.Data.Linq.DataContext> *bağlı* bir nesne. Daha fazla bilgi için, bkz. [N katmanlı uygulamalarda veri alma ve CUD işlemleri (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|
|`ToBeInserted`|Geçerli <xref:System.Data.Linq.DataContext>bir nesne kullanılarak alınmadı. Bu, sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>bir `INSERT` veritabanının oluşmasına neden olur.|
|`ToBeUpdated`|Bir nesne alındıktan sonra değiştirilmiş olarak bilinen bir nesne. Bu, sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>bir `UPDATE` veritabanının oluşmasına neden olur.|
|`ToBeDeleted`|Silinmek üzere işaretlenen bir nesne, sırasında `DELETE` <xref:System.Data.Linq.DataContext.SubmitChanges%2A>bir veritabanına neden olur.|
|`Deleted`|Veritabanında silinmiş bir nesne. Bu durum sondur ve ek geçişler için izin vermez.|

## <a name="inserting-objects"></a>Nesneler ekleniyor

`Inserts` Kullanarak<xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>açıkça istek yapabilirsiniz. Alternatif olarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , güncellenmesi `Inserts` gereken bilinen nesnelerden birine bağlı nesneleri bularak çıkarsanamıyor. Örneğin, bir nesnesine bir nesnesi eklerseniz `Untracked` `Untracked` <xref:System.Data.Linq.EntitySet%601> veya nesnesine bir <xref:System.Data.Linq.EntityRef%601> nesnesi ayarlarsanız, `Untracked` nesneyi grafikteki izlenen nesneler yoluyla erişilebilir hale getirebilirsiniz. İşlem <xref:System.Data.Linq.DataContext.SubmitChanges%2A>sırasında izlenen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri gezirken, izlenmeyen kalıcı nesneleri tespit edin. Bu tür nesneler veritabanına ekleme adaylarıdır.

Bir devralma hiyerarşisindeki sınıflar için, ( <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>`o`), nesne `o`türüyle eşleşecek şekilde *ayrıştırıcı* olarak atanan üyenin değerini de ayarlar. Varsayılan Ayrıştırıcı değeriyle eşleşen bir tür söz konusu olduğunda, bu eylem ayrıştırıcı değerinin varsayılan değer ile üzerine yazılmasına neden olur. Daha fazla bilgi için bkz. [Devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).

> [!IMPORTANT]
> Öğesine `Table` eklenen bir nesne, kimlik önbelleğinde değil. Kimlik önbelleği yalnızca veritabanından alınan verileri yansıtır. Bir çağrısından <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>sonra, eklenen varlık başarıyla tamamlanana kadar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanına yönelik sorgularda görünmez.

## <a name="deleting-objects"></a>Nesneleri silme

İzlenen bir nesneyi `o` , (o) uygun <xref:System.Data.Linq.Table%601>şekilde <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>çağırarak silinmek üzere işaretlersiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir nesnenin bir Update işlemi olarak, bir <xref:System.Data.Linq.EntitySet%601> , bir güncelleştirme işlemi olarak kaldırılmasını ve karşılık gelen yabancı anahtar değerinin null olarak ayarlandığını varsayar. İşlemin hedefi (`o`), tablosundan silinmez. Örneğin, `cust.Orders.DeleteOnSubmit(ord)` `ord.CustomerID` ve `cust` arasındaki`ord` ilişkinin, yabancı anahtar null olarak ayarlanarak kullanıldığı bir güncelleştirmeyi belirtir. Öğesine `ord`karşılık gelen satırın silinmesine neden olmaz.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir nesne (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) tablosundan silindiğinde aşağıdaki işlemeyi gerçekleştirir:

- Çağrıldığında, bu nesne için `DELETE` bir işlem gerçekleştirilir. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>

- Kaldırma, yüklenip yüklenmediğine bakılmaksızın ilgili nesnelere yayılmaz. Özellikle, ilişkili nesneler ilişki özelliğini güncelleştirmek için yüklenmez.

- Başarılı yürütmeden <xref:System.Data.Linq.DataContext.SubmitChanges%2A>sonra nesneler `Deleted` duruma ayarlanır. Sonuç olarak, nesnesini veya bunun `id` <xref:System.Data.Linq.DataContext>içinde kullanamazsınız. Bir <xref:System.Data.Linq.DataContext> örnek tarafından tutulan iç önbellek, nesneler veritabanında silindikten sonra bile, yeni olarak alınan veya eklenen nesneleri ortadan kaldırmaz.

<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> Yalnızca<xref:System.Data.Linq.DataContext>tarafından izlenen bir nesnede çağırabilirsiniz. Bir `Untracked` nesne için, çağrısından <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>önce öğesini <xref:System.Data.Linq.Table%601.Attach%2A> çağırmanız gerekir. <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> Bir`Untracked` nesneyi çağırmak özel durum oluşturur.

> [!NOTE]
> Bir nesneden bir nesnenin kaldırılması, sırasında [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] karşılık gelen bir SQL `DELETE` <xref:System.Data.Linq.DataContext.SubmitChanges%2A>komutu oluşturmayı söyler. Bu eylem nesneyi önbellekten kaldırmaz veya silmeyi ilgili nesnelere yaymaz.
>
> Silinen bir nesneyi `id` geri kazanmak için yeni <xref:System.Data.Linq.DataContext> bir örnek kullanın. İlgili nesnelerin temizlenmesi için veritabanının *Cascade Delete* özelliğini kullanabilir veya ilgili nesneleri el ile silebilirsiniz.
>
> İlgili nesnelerin herhangi bir özel sırada silinmesi gerekmez (veritabanından farklı olarak).

## <a name="updating-objects"></a>Nesneler güncelleştiriliyor

Değişikliklerin bildirimlerini gözlemleyerek tespit `Updates` edebilirsiniz. Bildirimler, <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> özellik ayarlayıcıları içindeki olay aracılığıyla sağlanır. Bir nesne için ilk değişiklik bildirildiğinde, nesnenin bir kopyasını oluşturur ve nesneyi bir `Update` deyimin oluşturulması için bir aday olarak değerlendirir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

Uygulamamış <xref:System.ComponentModel.INotifyPropertyChanging>nesneler için, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerin ilk gerçekleştirilmiş olmaları durumunda sahip olduğu değerlerin bir kopyasını tutar. ' İ çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnenin değiştirilip değiştirilmediğini belirlemek için geçerli ve orijinal değerleri karşılaştırır.

İlişkilerle ilgili güncelleştirmeler için, alt öğeden üst öğeye başvuru (yani, yabancı anahtara karşılık gelen başvuru), yetkili olarak kabul edilir. Ters yöndeki başvuru (diğer bir deyişle, üst-alt) isteğe bağlıdır. İlişki sınıfları (<xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601>) çift yönlü başvuruların bire çok ve bire bir ilişkiler için tutarlı olmasını garanti eder. Nesne modeli veya <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntityRef%601>kullanmıyorsa ve ters başvuru mevcutsa, ilişki güncelleniyorsa iletme başvurusuyla tutarlı tutulması sizin sorumluluğunuzdadır.

Hem gerekli başvuruyu hem de karşılık gelen yabancı anahtarı güncelleştirirseniz, kabul ettikleri emin olmanız gerekir. İki <xref:System.InvalidOperationException> kez çağırdığınız <xref:System.Data.Linq.DataContext.SubmitChanges%2A>sırada eşitlenmemişse bir özel durum oluşturulur. Yabancı anahtar değer değişiklikleri, temel alınan satırın güncelleştirilmesini etkileyecek kadar yeterli olsa da, nesne grafiğinin bağlantısını sürdürmek ve ilişkilerin çift yönlü tutarlılığını sağlamak için başvuruyu değiştirmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Insert, Update ve Delete İşlemleri](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
