---
title: İşlem Yönetimi Yükseltme
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: df2597d6fcce7fbd51f6f17bd42469cb7fcf3fdf
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662459"
---
# <a name="transaction-management-escalation"></a>İşlem Yönetimi Yükseltme
Windows bir Hizmetleri ve birlikte bir işlem yöneticisi oluşturan modülleri kümesini barındırır. İşlem Yönetim yükseltme bir işlem hareket yöneticisinin bileşenlerden biri diğerine geçiş işlemini açıklar.  
  
 <xref:System.Transactions> en çok tek bir kalıcı kaynak veya birden çok geçici kaynakları içeren bir işlem koordinatları bir işlem yöneticisi bileşeni içerir. İşlem Yöneticisi yalnızca içi uygulama etki alanı çağrıları kullandığından, en iyi performansı verir. Geliştiriciler işlem yöneticisi ile doğrudan etkileşimli olarak. Bunun yerine, arabirimleri, ortak davranışını ve yardımcı sınıfları tanımlayan bir ortak altyapısı tarafından sağlanan <xref:System.Transactions> ad alanı.  
  
 Aynı bilgisayarda işlemin (işlem ve makine sınırlarında dahil) başka bir uygulama etki alanındaki bir nesneye sağlamak istediğinizde <xref:System.Transactions> altyapı, Microsoft tarafından yönetilmek üzere işlem otomatik olarak iletir Dağıtılmış İşlem Düzenleyicisi (MSDTC). Başka bir kalıcı Kaynak Yöneticisi listeleme yükseltme de oluşur. İlerletilmiş işlemi, yükseltilmiş durumunda kendi tamamlanana kadar yönetilen kalır.  
  
 Arasında <xref:System.Transactions> işlem ve MSDTC işlem Promotable tek aşaması liste (PSPE) aracılığıyla sunulan işlem bir aracı türü yok. PSPE olan başka bir önemli yönteminde <xref:System.Transactions> performansını iyileştirme için. Farklı uygulama etki alanı, işlem veya'na katılmak için bilgisayarda bulunan bir uzak kalıcı kaynak sağlayan bir <xref:System.Transactions> bir MSDTC işlem ilerletilmiş için bu neden olmadan işlem. PSPE hakkında daha fazla bilgi için bkz: [katılımcı bir işlemde kaynakları kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Yükseltme nasıl başlatılır  
 MSDTC ayrı bir işlemde ve işlem gönderilen iletiler MSDTC sonuçları için bir işlem Etkinleºmesini bulunduğundan işlem yükseltme performans azaltır. Performansı artırmak için gecikme veya MSDTC aktarmayı kaçının; Bu nedenle, nasıl ve ne zaman yükseltme başlatılır bilmeniz gerekir.  
  
 Sürece <xref:System.Transactions> altyapı işler geçici kaynakları ve tek aşamalı bildirimleri, sahipliğini işlem saklanır desteklediği en çok bir kalıcı kaynak <xref:System.Transactions> altyapı. İşlem Yöneticisi yalnızca aynı uygulama etki alanındaki ve (hareketin sonucu yazılırken) hangi günlüğe kaydetme için Canlı gerekli olmadığını kaynakları için kendisini avails. Sonuçlanır bir yükseltme <xref:System.Transactions> MSDTC için işlem sahipliğini aktarma altyapı olur olduğunda:  
  
- Tek aşamalı bildirimleri desteklemiyor en az bir kalıcı kaynak işleme kayıtlı.  
  
- Tek aşamalı bildirimlerini desteklemek en az iki kalıcı kaynak kayıtlı. Örneğin, SQL Server 2005 tek bir bağlantı kaydetme yükseltilecek bir işlem neden olmaz. Ancak, her açtığınız ikinci bağlantıya bir SQL Server 2005, listeleme veritabanına neden veritabanı <xref:System.Transactions> altyapı algılar, işlem ikinci kalıcı kaynak olan ve bir MSDTC işlem için iletir.  
  
- "İşlem farklı uygulama etki alanı ya da farklı bir işlem sıralamakta" bir istek çağrılır. Örneğin, bir uygulama etki alanı sınırları üzerinden işlem nesnesi serileştirme. İşlem nesnesi sıralanmış-tarafından-her türlü girişim, uygulama etki alanı sınırı (hatta aynı işlemde) üzerinden geçmek için işlem nesnesi serileştirmede sonuçları başka bir deyişle değerdir. Alan bir uzak yöntem bir arama yaparak işlem nesneleri geçirebilirsiniz bir <xref:System.Transactions.Transaction> bir parametre veya uzak bir işlem hizmet bileşeni erişmek deneyebilirsiniz. Bu işlem nesnesini serileştirir ve bir uygulama etki bir işlem olduğunda serileştirildiği olarak bir yükseltme sonuçlanır. Bu dağıtılmış ve yerel hareket yöneticisi yeterlidir.  
  
 Aşağıdaki tablo yükseltme sırasında oluşturulan tüm olası özel durumları listeler.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Yalıtım düzeyi eşit olan bir işlem İlerlet girişimi <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|İşlem Yöneticisi kapalı.|  
|<xref:System.Transactions.TransactionException>|Yükseltme başarısız olur ve uygulama durduruldu.|
