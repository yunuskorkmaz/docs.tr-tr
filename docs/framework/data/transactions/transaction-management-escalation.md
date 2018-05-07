---
title: İşlem yönetimi yükseltme
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: 2a5592cc9ebf0ddfc49f38da9404c81d11a29cf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-management-escalation"></a>İşlem yönetimi yükseltme
Windows Hizmetleri ve birlikte bir işlem yöneticisi oluşturan modüllerin kümesi barındırır. İşlem yönetimi yükseltme bir işlem İşlem Yöneticisi'nin bileşenleri birinden diğerine geçiş işlemini açıklar.  
  
 <xref:System.Transactions> en fazla tek dayanıklı kaynak ya da birden çok volatile kaynakları içeren bir işlem koordine eden bir işlem yöneticisi bileşeni içerir. İşlem Yöneticisi yalnızca içi uygulama etki alanı çağrıları kullandığından, en iyi performansı verir. Geliştiriciler işlem yöneticisi ile doğrudan etkileşim değil. Bunun yerine, arabirimleri, ortak davranışı ve yardımcı sınıfları tanımlar ortak bir altyapısı tarafından sağlanan <xref:System.Transactions> ad alanı.  
  
 İşlem (işlem ve makine sınırları içinde dahil) başka bir uygulama etki alanındaki bir nesneye aynı bilgisayara sağlamak istediğinizde <xref:System.Transactions> altyapı otomatik olarak Microsoft tarafından yönetilecek işlem iletir Dağıtılmış İşlem Düzenleyicisi (MSDTC). Başka bir kalıcı Kaynak Yöneticisi listeleme yükseltme de oluşur. İlerletilen işlemin yükseltilmiş durumundayken kendi tamamlanana kadar yönetilen kalır.  
  
 Arasında <xref:System.Transactions> işlem ve MSDTC işlem yükseltilebilir tek aşaması kaydı (PSPE) aracılığıyla kullanılabilir hale getirileceğini işlem aracı bir tür. PSPE olan başka bir önemli yönteminde <xref:System.Transactions> performansını iyileştirme için. Farklı uygulama etki alanı, işlem veya bunlara katılmak için bilgisayarda bulunan uzak dayanıklı bir kaynak sağlayan bir <xref:System.Transactions> bir MSDTC işleminde ilerletilen için bunu neden olmadan işlem. PSPE hakkında daha fazla bilgi için bkz: [kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Yükseltme nasıl başlatılır  
 MSDTC ayrı bir işlemde ve işlem arasında gönderilen iletiler MSDTC sonuçlarında harekete yükselen bulunduğundan işlem yükseltme performansını düşürür. Performansı artırmak için gecikme veya MSDTC yükseltme kaçının; Bu nedenle, yükseltme nasıl ve ne zaman başlatılır bilmeniz gerekir.  
  
 Sürece <xref:System.Transactions> altyapı işleme volatile kaynakları ve tek aşamalı bildirimlerini, sahipliğini işlem saklanır destekleyen en fazla bir dayanıklı kaynak <xref:System.Transactions> altyapı. İşlem Yöneticisi kendisi yalnızca aynı uygulama etki alanında ve (işlem sonucu diske yazma) hangi günlüğü için Canlı gerekli değildir, bu kaynakları avails. Sonuçlanan bir yükseltme <xref:System.Transactions> gerçekleşir MSDTC için işlem sahipliğini aktarma altyapı zaman:  
  
-   Tek aşamalı bildirimlerini desteklemiyor en az bir dayanıklı kaynak işlemde listeye kayıtlı.  
  
-   Tek aşamalı bildirimlerini desteklemek en az iki dayanıklı kaynakları işlemde kayıtlıdır. Örneğin, tek bir bağlantıyla kaydetme [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] yükseltilmesi bir işlem neden olmaz. Bununla birlikte, her açtığınız ikinci bir bağlantı için bir [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] listeleme, veritabanına neden veritabanı <xref:System.Transactions> altyapı algılar, işlemde ikinci dayanıklı kaynaktır ve bir MSDTC işleminde iletir.  
  
-   "İşlem farklı uygulama etki alanına veya farklı bir işlem sıralama" isteği çağrılır. Örneğin, bir uygulama etki alanı sınırları boyunca işlem nesnesini serileştirme. İşlem nesnesi sıralanmış-tarafından-girişimleri bir uygulama etki alanı sınırı (bile aynı işlemde) üzerinden iletmek için işlem nesnesi serileştirmede sonuçları anlamı değerdir. Alan bir uzak yöntem çağrısı yaparak işlem nesnelerini geçirebilirsiniz bir <xref:System.Transactions.Transaction> gibi bir parametre veya uzak işlemle ilgili hizmet bileşen erişmek deneyebilirsiniz. Bu işlem nesnesini serileştirir ve bir işlem uygulama etki alanı arasında ne zaman seri olarak bağlı olarak, bir yükseltme sonuçlanır. Dağıtılmakta ve yerel işlem yöneticisi artık yeterli değil.  
  
 Aşağıdaki tablo yükseltme sırasında oluşturulan tüm olası özel durumları listeler.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Yalıtım düzeyine eşit olan bir işlem İlerlet girişimi <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|İşlem Yöneticisi çalışmıyor.|  
|<xref:System.Transactions.TransactionException>|Yükseltme başarısız olur ve uygulama durduruldu.|
