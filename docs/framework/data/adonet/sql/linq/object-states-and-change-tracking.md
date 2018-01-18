---
title: "Nesne durumlarını ve değişiklik izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f7eb1a8afe87caece18432c66a8d8a268ce9fbd2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="object-states-and-change-tracking"></a>Nesne durumlarını ve değişiklik izleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nesneler her zaman katılmak bazı durumlarda *durumu*. Örneğin, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yeni bir nesne oluşturur nesne `Unchanged` durumu. Kendi başınıza oluşturduğunuz yeni bir nesne için bilinmeyen <xref:System.Data.Linq.DataContext> ve `Untracked` durumu. Başarılı yürütülmesinin <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, bilinen tüm nesneleri [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bulunan `Unchanged` durumu. (Tek istisnası, başarılı bir şekilde olan veritabanından silinmiş tarafından temsil edilen `Deleted` durum ve, kullanılamaz <xref:System.Data.Linq.DataContext> örneğinin.)  
  
## <a name="object-states"></a>Nesne durumlarını  
 Olası durumlar için aşağıdaki tabloda listelenmektedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesneleri.  
  
|Durum|Açıklama|  
|-----------|-----------------|  
|`Untracked`|Tarafından izlenen değil bir nesne [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Örnekler şunlardır:<br /><br /> -Sorgulanan geçerli değil bir nesne <xref:System.Data.Linq.DataContext> (örneğin, yeni oluşturulan bir nesne).<br />-Seri durumdan çıkarma oluşturulan bir nesne<br />-Farklı bir sorgulanan nesne <xref:System.Data.Linq.DataContext>.|  
|`Unchanged`|Bir nesne alınan geçerli kullanarak <xref:System.Data.Linq.DataContext> ve oluşturulduktan sonra değişiklik bilinmiyor.|  
|`PossiblyModified`|Bir nesne *bağlı* için bir <xref:System.Data.Linq.DataContext>. Daha fazla bilgi için bkz: [veri alımı ve N katmanlı uygulamalar (LINQ-SQL) CUD işlemlerinde](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md).|  
|`ToBeInserted`|Geçerli kullanarak alınmamış bir nesne <xref:System.Data.Linq.DataContext>. Bu bir veritabanı neden `INSERT` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeUpdated`|Bunu alındığından beri değiştirilen bilinen bir nesne. Bu bir veritabanı neden `UPDATE` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`ToBeDeleted`|Bir nesne bir veritabanı neden silinmek üzere işaretlenmiş `DELETE` sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.|  
|`Deleted`|Veritabanında silinmiş bir nesne. Bu durum, son ve ek geçişler için izin vermez.|  
  
## <a name="inserting-objects"></a>Nesne ekleme  
 Açıkça isteyebilir `Inserts` kullanarak <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>. Alternatif olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çıkarımını `Inserts` tarafından güncelleştirilmesi gereken bilinen nesneleri birine bağlı nesneleri bulma. Örneğin eklerseniz, bir `Untracked` nesnesine bir <xref:System.Data.Linq.EntitySet%601> veya bir <xref:System.Data.Linq.EntityRef%601> için bir `Untracked` nesnesi, yaptığınız `Untracked` nesne grafikte izlenen nesneleri yöntem kullanılarak erişilebilir. İşleme sırasında <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izlenen nesneleri erişir ve değil izlenen ulaşılabilir kalıcı nesneler bulur. Bu tür nesneleri veritabanına eklemek için bir aday değildir.  
  
 Bir devralma hiyerarşisini sınıfların <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) olarak belirtilen üyenin değerini de ayarlar *Ayrıştırıcıyı* nesne türüyle eşleşecek şekilde `o`. Varsayılan Ayrıştırıcıyı değer eşleşen bir tür olması durumunda, varsayılan değer olan üzerine yazılmasını Ayrıştırıcıyı değeri bu eylem neden olur. Daha fazla bilgi için bkz: [devralma desteği](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
> [!IMPORTANT]
>  Eklenecek nesne bir `Table` kimlik önbellekte değil. Kimlik önbellek yalnızca ne veritabanından alınır yansıtır. Çağrı sonra <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>, eklenen varlık kadar veritabanı sorguları görünmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> başarıyla tamamlandı.  
  
## <a name="deleting-objects"></a>Nesneleri silme  
 İzlenen nesne işaretlemek `o` çağırarak silinmek <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o) uygun <xref:System.Data.Linq.Table%601>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir nesneden kaldırılmasını göz önünde bulundurur bir <xref:System.Data.Linq.EntitySet%601> bir güncelleştirme olarak işlemi ve ilgili yabancı anahtar değeri ayarlanmış null. İşlemin hedefi olan (`o`) kendi tablosundan silinmez. Örneğin, `cust.Orders.DeleteOnSubmit(ord)` güncelleştirmeyi belirten burada arasındaki ilişkiyi `cust` ve `ord` yabancı anahtarı ayarlanarak zarar görmesi `ord.CustomerID` null. Karşılık gelen satırın silinmesi neden olmaz `ord`.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]bir nesnesi silindiğinde aşağıdaki işleme gerçekleştirir (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) kendi tablosundan:  
  
-   Zaman <xref:System.Data.Linq.DataContext.SubmitChanges%2A> olarak adlandırılan bir `DELETE` işlemi, bu nesne için gerçekleştirilir.  
  
-   Kaldırma yüklenen olmanıza bakılmaksızın ilgili nesnelere dağıtılmaz. Özellikle, ilgili nesneleri ilişki özelliği güncelleştirmek için yüklenmez.  
  
-   Aktarılmadığı sonra <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, nesneler kümesine `Deleted` durumu. Sonuç olarak, nesne kullanamazsınız veya kendi `id` bakımından <xref:System.Data.Linq.DataContext>. İç önbelleği tarafından korunan bir <xref:System.Data.Linq.DataContext> örneği olan veya nesnelerin veritabanında bile silindikten sonra yeni olarak, eklenen nesneleri ortadan değil.  
  
 Çağırabilirsiniz <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> yalnızca tarafından izlenen bir nesnede <xref:System.Data.Linq.DataContext>. İçin bir `Untracked` nesne çağırmanız gerekir <xref:System.Data.Linq.Table%601.Attach%2A> çağırmadan önce <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>. Çağırma <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> üzerinde bir `Untracked` nesnesi bir özel durum oluşturur.  
  
> [!NOTE]
>  Bir tablodan bir nesne kaldırma söyler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] karşılık gelen SQL oluşturmak için `DELETE` zamanında komutu <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Bu eylem nesneyi önbellekten kaldırmaz veya ilişkili nesneleri silme işlemini yayılması.  
>   
>  Geri kazanmak için `id` silinmiş bir nesneyi yeni bir kullanmak <xref:System.Data.Linq.DataContext> örneği. İlişkili nesneleri temizlenmesi için kullandığınız *art arda silme* özellik veritabanının, aksi takdirde el ile ilgili nesneleri silin.  
>   
>  İlişkili nesneleri herhangi bir özel sırada silinmesi gerekmez (aksine veritabanındaki).  
  
## <a name="updating-objects"></a>Nesnelerini güncelleştirme  
 Tespit edebilirsiniz `Updates` değişikliklerin bildirimleri Gözlemleme tarafından. Bildirimleri aracılığıyla sağlanan <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> özellik ayarlayıcıları olayı. Zaman [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilk değişikliği bildirim bir nesneye nesnesinin bir kopyasını oluşturur ve nesne oluşturmak için aday göz önünde bulundurur bir `Update` deyimi.  
  
 Uygulamayan nesneler için <xref:System.ComponentModel.INotifyPropertyChanging>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilk gerçekleştirilip yükleyen nesneler içeriyor değerlerin bir kopyasını tutar. Çağırdığınızda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne değiştirilmiş olup olmadığına karar vermek için geçerli ve özgün değerleri karşılaştırır.  
  
 İlişkileri için güncelleştirmeler için alt başvurusundan (diğer bir deyişle, yabancı anahtar karşılık gelen başvuru) üst yetkilisi olarak kabul edilir. Ters yönde başvurusu (diğer bir deyişle, alt üst) isteğe bağlıdır. İlişki sınıfları (<xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601>) çift yönlü başvurular bir çok ve bire bir ilişkiler için tutarlı olduğunu garanti. Nesne modeli kullanmıyorsa <xref:System.Data.Linq.EntitySet%601> veya <xref:System.Data.Linq.EntityRef%601>, ve geriye doğru başvuru varsa, bu ilişkiyi güncelleştirildiğinde ileri başvuru ile tutarlı tutmak için sizin sorumluluğunuzdadır.  
  
 Gerekli referans ve ilgili yabancı anahtar güncelleştirirseniz, kullanıcının kabul etmesi olduğundan emin olmanız gerekir. Bir <xref:System.InvalidOperationException> iki çağırmanız aynı anda eşitlenmemişse özel durum <xref:System.Data.Linq.DataContext.SubmitChanges%2A>. Yabancı anahtar değerini değişiklikler temel satırın bir güncelleştirme etkileyen için yeterli olmakla birlikte, ilişkileri Nesne grafiği ve çift yönlü tutarlılığını bağlantısını korumak için başvuru değiştirmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Insert, Update ve Delete İşlemleri](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
