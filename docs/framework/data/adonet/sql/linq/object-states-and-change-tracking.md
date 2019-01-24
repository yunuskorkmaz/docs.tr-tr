---
title: Nesne durumları ve değişiklik izleme
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 89e9f44a6cd3579a5ef9cc2078609ca26e0d2ae5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683316"
---
# <a name="object-states-and-change-tracking"></a>Nesne durumları ve değişiklik izleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneler her zaman katılan bazı *durumu*. Örneğin, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni bir nesne oluşturur nesne `Unchanged` durumu. Kendiniz oluşturduğunuz yeni bir nesne için bilinmeyen <xref:System.Data.Linq.DataContext> ve `Untracked` durumu. Başarılı yürütülmesinin <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, bilinen tüm nesneleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bulunan `Unchanged` durumu. (Tek özel durumu başarıyla bulunan veritabanından silinmiş olanlar tarafından temsil edilen `Deleted` durum ve kullanılamaz durumda uygulamasındaki <xref:System.Data.Linq.DataContext> örneği.)  
  
## <a name="object-states"></a>Nesne durumları  
 Olası durumlar için aşağıdaki tabloda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri.  
  
|Durum|Açıklama|  
|-----------|-----------------|  
|`Untracked`|Bir nesne tarafından izlenen değil [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Örnekler şunlardır:<br /><br /> -Sorgulanan geçerli değil bir nesne <xref:System.Data.Linq.DataContext> (örneğin, yeni oluşturulan bir nesne).<br />-Bir nesne seri durumundan çıkarma oluşturulan<br />-Farklı bir ile sorgulanan nesne <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Bir nesne alınan geçerli kullanarak <xref:System.Data.Linq.DataContext> ve oluşturulduktan sonra değiştirilmiş bilinmiyor.|  
|`PossiblyModified`|Bir nesne *bağlı* için bir <xref:System.Data.Linq.DataContext>. Daha fazla bilgi için [veri alma ve CUD işlemleri (LINQ to SQL) N katmanlı uygulamalarda](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Nesneyi geçerli kullanarak alınmamış <xref:System.Data.Linq.DataContext>. Bu bir veritabanı neden `INSERT` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Alındıktan sonra değiştirilmiş gibi bilinen bir nesne. Bu bir veritabanı neden `UPDATE` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Bir nesne bir veritabanı neden silinmek üzere işaretlenmiş `DELETE` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Veritabanında silinmiş olan bir nesne. Bu durum kalıcıdır ve kaynak için ek geçişlere izin verilmez.|  
  
## <a name="inserting-objects"></a>Nesne ekleme  
 Açıkça talep edebilir `Inserts` kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternatif olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çıkarımını `Inserts` güncelleştirilmesi gereken bilinen nesnelerinden birine bağlı nesneleri bulma tarafından. Örneğin eklerseniz, bir `Untracked` nesnesini bir <xref:System.Data.Linq.EntitySet%601> veya bir <xref:System.Data.Linq.EntityRef%601> için bir `Untracked` nesne yaptığınız `Untracked` nesne grafiğinde izlenen nesneler aracılığıyla erişilebilir. İşlem sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenen nesneleri geçirir ve değil izlenen erişilebilir kalıcı nesneler bulur. Bu tür nesneler için veritabanına ekleme adaylardır.  
  
 Devralma Hiyerarşisi, sınıfların <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) olarak belirtilen üyenin değerini de ayarlar *ayrıştırıcı* nesne türüyle eşleşmesi için `o`. Varsayılan ayrıştırıcı değeri ile eşleşen bir tür olması durumunda, bu eylem ayrıştırıcı değeri varsayılan değerin üzerine yazılmasına neden olur. Daha fazla bilgi için [devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Eklenecek nesne bir `Table` kimlik önbellekte değil. Yalnızca ne veritabanından alınan kimlik önbellek yansıtır. Çağrısı yapıldıktan sonra <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, eklenen varlık kadar veritabanı sorguları görünmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> başarıyla tamamlandı.  
  
## <a name="deleting-objects"></a>Nesneleri silme  
 İzlenen nesne işaretlemek `o` çağırarak silinmek <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) uygun <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir nesneden kaldırılmasını olarak değerlendirir bir <xref:System.Data.Linq.EntitySet%601> bir güncelleştirme işlemi ve karşılık gelen yabancı anahtar değeri ayarlanır null. Hedef işlemin (`o`) kendi tablosundan silinmez. Örneğin, `cust.Orders.DeleteOnSubmit(ord)` güncelleştirmeyi belirten burada arasındaki ilişkiyi `cust` ve `ord` yabancı anahtarı ayarlayarak yazıyordunuz `ord.CustomerID` null. Karşılık gelen satırın silinmesine neden olmaz `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir nesne silindiğinde aşağıdaki işlemeyi gerçekleştirir (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) kendi tablosundan:  
  
-   Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılan bir `DELETE` işlemi, bu nesne için gerçekleştirilir.  
  
-   Kaldırma işlemi yüklü olup bağımsız olarak, ilgili nesnelere dağıtılmadı. Özellikle, ilgili nesneleri ilişki özelliği güncelleştirmek için yüklenmez.  
  
-   Başarılı yürütme sonrasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, nesneler kümesine `Deleted` durumu. Sonuç olarak, nesne kullanamazsınız veya kendi `id` bakımından <xref:System.Data.Linq.DataContext>. İç önbelleği tarafından tutulan bir <xref:System.Data.Linq.DataContext> örneği alınan veya hatta veritabanında nesne silindikten sonra yeni olarak, eklenen nesneleri ortadan değil.  
  
 Çağırabilirsiniz <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yalnızca tarafından izlenen bir nesnede <xref:System.Data.Linq.DataContext>. İçin bir `Untracked` nesne çağırmanız <xref:System.Data.Linq.Table%601.Attach%2A> çağırmadan önce <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Çağırma <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> üzerinde bir `Untracked` nesne bir özel durum oluşturur.  
  
> [!NOTE]
>  Bir nesne bir tablodan kaldırma söyler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] karşılık gelen SQL oluşturulacak `DELETE` komutu anında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Bu eylem nesneyi önbellekten kaldırmaz veya ilgili nesneler için silme işlemi yayar.  
>   
>  Geri kazanmak için `id` silinmiş bir nesneyi yeni bir kullanın <xref:System.Data.Linq.DataContext> örneği. İlgili nesneler temizlenmesi için kullanabileceğiniz *art arda silme* özellik veritabanının, aksi takdirde el ile ilgili nesneleri silin.  
>   
>  İlgili nesneler herhangi özel bir sırada silinmesi gerekmez (aksine veritabanındaki).  
  
## <a name="updating-objects"></a>Nesnelerini güncelleştirme  
 Can detect `Updates` değişikliklerin bildirimleri gözleme tarafından. Bildirimleri aracılığıyla sağlanan <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> özellik ayarlayıcılarına olayı. Zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilk değişikliği bildirim bir nesneye nesnesinin bir kopyasını oluşturur ve nesneyi oluşturmak için aday olarak değerlendirir bir `Update` deyimi.  
  
 Değil uygulayan nesneler için <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri, ilk gerçekleştirilmiş olan değerlerin bir kopyasını tutar. Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne değiştirilmiş olup olmadığına karar vermek için geçerli ve özgün değeri karşılaştırır.  
  
 İlişkiler için güncelleştirmeleri almak için (diğer bir deyişle, yabancı anahtara karşılık gelen başvuru) üst alt başvuru yetkilisi olarak kabul edilir. Ters yönde başvurusu (diğer bir deyişle, alt üst öğesinden) isteğe bağlıdır. İlişki sınıfları (<xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601>) çift yönlü başvuruları bire çok ve bire bir ilişkiler için tutarlı olduğunu garanti. Nesne modeli kullanmıyorsa <xref:System.Data.Linq.EntitySet%601> veya <xref:System.Data.Linq.EntityRef%601>, ve ters başvuru varsa, bu ilişkiyi güncelleştirildiğinde ileri başvuru ile tutarlı kalmasını sağlamak için sizin sorumluluğunuzdadır.  
  
 Gerekli başvuru hem ilgili yabancı anahtar güncelleştirirseniz, bunlar kabul emin olmanız gerekir. Bir <xref:System.InvalidOperationException> iki çağırmanızı zamanında eşitlenmemişse özel durum <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Yabancı anahtar değerini değişiklikler temel alınan satırın bir güncelleştirme etkileyen için yeterli olmakla birlikte, tutarlılık Nesne grafiği ve çift yönlü ilişkiler bağlantıyı sürdürmek için başvuru değiştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Insert, Update ve Delete İşlemleri](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
