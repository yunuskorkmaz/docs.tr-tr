---
description: 'Hakkında daha fazla bilgi edinin: nesne durumları ve Change-Tracking'
title: Nesne Durumları ve Değişiklik İzleme
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 5f3aa6197fa44d8b5ea9333c85255202cbfe519b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695508"
---
# <a name="object-states-and-change-tracking"></a>Nesne Durumları ve Değişiklik İzleme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneler her zaman bir *duruma* katılır. Örneğin, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Yeni bir nesne oluşturduğunda, nesne `Unchanged` durumundadır. Sizin oluşturduğunuz yeni bir nesne, ve için bilinmiyor <xref:System.Data.Linq.DataContext> `Untracked` durumundadır. ' Nin başarılı yürütmesi <xref:System.Data.Linq.DataContext.SubmitChanges%2A> , ' de bilinen tüm nesneler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Unchanged` durumunda. (Tek istisna, veritabanından başarıyla silinenler tarafından temsil edilir `Deleted` ve bu örnekte kullanılamaz durumda olabilir <xref:System.Data.Linq.DataContext> .)

## <a name="object-states"></a>Nesne durumları

Aşağıdaki tabloda nesneler için olası durumlar listelenmektedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

|Durum|Açıklama|
|-----------|-----------------|
|`Untracked`|Tarafından izlenmeyen bir nesne [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Örnekler şunlardır:<br /><br /> -Geçerli bir nesne <xref:System.Data.Linq.DataContext> (yeni oluşturulan nesne gibi) aracılığıyla sorgulanmadı.<br />-Serisini kaldırma ile oluşturulan nesne<br />-Farklı bir ile sorgulanan bir nesne <xref:System.Data.Linq.DataContext> .|
|`Unchanged`|Geçerli <xref:System.Data.Linq.DataContext> ve oluşturulduktan sonra değiştirilmiş olarak bilinen bir nesne.|
|`PossiblyModified`|Öğesine *bağlı* bir nesne <xref:System.Data.Linq.DataContext> . Daha fazla bilgi için, bkz. [N katmanlı uygulamalarda veri alma ve CUD işlemleri (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).|
|`ToBeInserted`|Geçerli bir nesne kullanılarak alınmadı <xref:System.Data.Linq.DataContext> . Bu, sırasında bir veritabanının oluşmasına neden olur `INSERT` <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .|
|`ToBeUpdated`|Bir nesne alındıktan sonra değiştirilmiş olarak bilinen bir nesne. Bu, sırasında bir veritabanının oluşmasına neden olur `UPDATE` <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .|
|`ToBeDeleted`|Silinmek üzere işaretlenen bir nesne, sırasında bir veritabanına neden olur `DELETE` <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .|
|`Deleted`|Veritabanında silinmiş bir nesne. Bu durum sondur ve ek geçişler için izin vermez.|

## <a name="inserting-objects"></a>Nesneler ekleniyor

Kullanarak açıkça istek yapabilirsiniz `Inserts` <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> . Alternatif olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Inserts` güncellenmesi gereken bilinen nesnelerden birine bağlı nesneleri bularak çıkarsanamıyor. Örneğin, bir nesnesine bir nesnesi eklerseniz `Untracked` <xref:System.Data.Linq.EntitySet%601> veya nesnesine bir nesnesi ayarlarsanız <xref:System.Data.Linq.EntityRef%601> `Untracked` , `Untracked` nesneyi grafikteki izlenen nesneler yoluyla erişilebilir hale getirebilirsiniz. İşlem sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> izlenen nesneleri gezirken, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenmeyen kalıcı nesneleri tespit edin. Bu tür nesneler veritabanına ekleme adaylarıdır.

Bir devralma hiyerarşisindeki sınıflar için, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> ( `o` ), nesne türüyle eşleşecek şekilde *ayrıştırıcı* olarak atanan üyenin değerini de ayarlar `o` . Varsayılan Ayrıştırıcı değeriyle eşleşen bir tür söz konusu olduğunda, bu eylem ayrıştırıcı değerinin varsayılan değer ile üzerine yazılmasına neden olur. Daha fazla bilgi için bkz. [Devralma desteği](inheritance-support.md).

> [!IMPORTANT]
> Öğesine eklenen bir nesne, `Table` kimlik önbelleğinde değil. Kimlik önbelleği yalnızca veritabanından alınan verileri yansıtır. Bir çağrısından sonra <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> , eklenen varlık başarıyla tamamlanana kadar veritabanına yönelik sorgularda görünmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .

## <a name="deleting-objects"></a>Nesneleri silme

İzlenen bir nesneyi `o` <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> , (o) uygun şekilde çağırarak silinmek üzere işaretlersiniz <xref:System.Data.Linq.Table%601> . [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir nesnenin bir <xref:System.Data.Linq.EntitySet%601> Update işlemi olarak, bir, bir güncelleştirme işlemi olarak kaldırılmasını ve karşılık gelen yabancı anahtar değerinin null olarak ayarlandığını varsayar. İşlemin hedefi ( `o` ), tablosundan silinmez. Örneğin, `cust.Orders.DeleteOnSubmit(ord)` ve arasındaki ilişkinin, `cust` `ord` yabancı anahtar null olarak ayarlanarak kullanıldığı bir güncelleştirmeyi belirtir `ord.CustomerID` . Öğesine karşılık gelen satırın silinmesine neden olmaz `ord` .

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir nesne () tablosundan silindiğinde aşağıdaki işlemeyi gerçekleştirir <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> :

- <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Çağrıldığında, `DELETE` Bu nesne için bir işlem gerçekleştirilir.

- Kaldırma, yüklenip yüklenmediğine bakılmaksızın ilgili nesnelere yayılmaz. Özellikle, ilişkili nesneler ilişki özelliğini güncelleştirmek için yüklenmez.

- Başarılı yürütmeden sonra <xref:System.Data.Linq.DataContext.SubmitChanges%2A> nesneler `Deleted` duruma ayarlanır. Sonuç olarak, nesnesini veya bunun `id` içinde kullanamazsınız <xref:System.Data.Linq.DataContext> . Bir örnek tarafından tutulan iç önbellek, <xref:System.Data.Linq.DataContext> nesneler veritabanında silindikten sonra bile, yeni olarak alınan veya eklenen nesneleri ortadan kaldırmaz.

<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>Yalnızca tarafından izlenen bir nesnede çağırabilirsiniz <xref:System.Data.Linq.DataContext> . Bir `Untracked` nesne için, çağrısından önce öğesini çağırmanız gerekir <xref:System.Data.Linq.Table%601.Attach%2A> <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> . <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>Bir nesneyi çağırmak `Untracked` özel durum oluşturur.

> [!NOTE]
> Bir nesneden bir nesnenin kaldırılması [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , sırasında karşılık gelen BIR SQL komutu oluşturmayı söyler `DELETE` <xref:System.Data.Linq.DataContext.SubmitChanges%2A> . Bu eylem nesneyi önbellekten kaldırmaz veya silmeyi ilgili nesnelere yaymaz.
>
> Silinen bir nesneyi geri kazanmak için `id` Yeni bir <xref:System.Data.Linq.DataContext> örnek kullanın. İlgili nesnelerin temizlenmesi için veritabanının *Cascade Delete* özelliğini kullanabilir veya ilgili nesneleri el ile silebilirsiniz.
>
> İlgili nesnelerin herhangi bir özel sırada silinmesi gerekmez (veritabanından farklı olarak).

## <a name="updating-objects"></a>Nesneler güncelleştiriliyor

`Updates`Değişikliklerin bildirimlerini gözlemleyerek tespit edebilirsiniz. Bildirimler, <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> özellik ayarlayıcıları içindeki olay aracılığıyla sağlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bir nesne için ilk değişiklik bildirildiğinde, nesnenin bir kopyasını oluşturur ve nesneyi bir deyimin oluşturulması için bir aday olarak değerlendirir `Update` .

Uygulamamış nesneler için <xref:System.ComponentModel.INotifyPropertyChanging> , [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnelerin ilk gerçekleştirilmiş olmaları durumunda sahip olduğu değerlerin bir kopyasını tutar. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>' İ çağırdığınızda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesnenin değiştirilip değiştirilmediğini belirlemek için geçerli ve orijinal değerleri karşılaştırır.

İlişkilerle ilgili güncelleştirmeler için, alt öğeden üst öğeye başvuru (yani, yabancı anahtara karşılık gelen başvuru), yetkili olarak kabul edilir. Ters yöndeki başvuru (diğer bir deyişle, üst-alt) isteğe bağlıdır. İlişki sınıfları ( <xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601> ) çift yönlü başvuruların bire çok ve bire bir ilişkiler için tutarlı olmasını garanti eder. Nesne modeli <xref:System.Data.Linq.EntitySet%601> veya kullanmıyorsa <xref:System.Data.Linq.EntityRef%601> ve ters başvuru mevcutsa, ilişki güncelleniyorsa iletme başvurusuyla tutarlı tutulması sizin sorumluluğunuzdadır.

Hem gerekli başvuruyu hem de karşılık gelen yabancı anahtarı güncelleştirirseniz, kabul ettikleri emin olmanız gerekir. <xref:System.InvalidOperationException>İki kez çağırdığınız sırada eşitlenmemişse bir özel durum oluşturulur <xref:System.Data.Linq.DataContext.SubmitChanges%2A> . Yabancı anahtar değer değişiklikleri, temel alınan satırın güncelleştirilmesini etkileyecek kadar yeterli olsa da, nesne grafiğinin bağlantısını sürdürmek ve ilişkilerin çift yönlü tutarlılığını sağlamak için başvuruyu değiştirmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
- [Insert, Update ve Delete İşlemleri](insert-update-and-delete-operations.md)
