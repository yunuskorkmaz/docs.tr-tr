---
title: İşlem Yönetimi Yükseltme
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: d2f027f8a94ee8f0cd23d0f0909ecc9137873bc2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205850"
---
# <a name="transaction-management-escalation"></a>İşlem Yönetimi Yükseltme
Windows, birlikte bir işlem yöneticisi oluşturan bir dizi hizmet ve modül barındırır. İşlem yönetimi yükseltme işlemi, işlem yöneticisinin bileşenlerinden birinden diğerine bir işlem geçirme işlemini açıklar.  
  
 <xref:System.Transactions>en çok, tek bir dayanıklı kaynak veya birden çok geçici kaynakla ilişkili bir işlemi koordine eden bir işlem Yöneticisi bileşeni içerir. İşlem Yöneticisi yalnızca uygulama içi etki alanı çağrılarını kullandığından, en iyi performansı verir. Geliştiricilerin işlem yöneticisiyle doğrudan etkileşimde olmaması gerekir. Bunun yerine, arabirimleri, yaygın davranışı ve yardımcı sınıfları tanımlayan ortak bir altyapı <xref:System.Transactions> ad alanı tarafından sağlanır.  
  
 Aynı bilgisayardaki başka bir uygulama etki alanındaki (işlem ve makine sınırları dahil) bir nesneye işlem sağlamak istediğinizde, <xref:System.Transactions> altyapı Microsoft tarafından yönetilmek üzere işlemi otomatik olarak ilerletir Dağıtılmış İşlem Düzenleyicisi (MSDTC). Başka bir kalıcı Kaynak Yöneticisi listeleme yükseltme de oluşur. İlerletilen zaman, işlem tamamlanana kadar yükseltilmiş durumunda yönetilmeye devam eder.  
  
 <xref:System.Transactions> İşlem ve MSDTC işlemi arasında, promotable tek aşama kaydı (PSPE) aracılığıyla kullanılabilir hale getirilen bir işlem aracı türü vardır. PSPE olan başka bir önemli yönteminde <xref:System.Transactions> performansını iyileştirme için. Farklı bir uygulama etki alanında, işlemde veya bilgisayarda bulunan, uzak kalıcı bir kaynağın bir MSDTC işlemine ilerlemesine neden olmadan <xref:System.Transactions> bir işleme katılmasını sağlar. PSPE hakkında daha fazla bilgi için bkz. [kaynakları bir işlem Içinde katılımcılar olarak listeleme](enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Yükseltme nasıl başlatılır  
 MSDTC, ayrı bir işlemde bulunduğundan ve işlem genelinde gönderilen iletilerde bir işlemi MSDTC sonuçlarına ilerletiğinden, işlem yükseltme performansı azaltır. Performansı artırmak için, MSDTC 'yi geciktirmelisiniz veya bu yükseltmeyi kullanmaktan kaçının; Bu nedenle, ilerletme 'nın nasıl ve ne zaman başlatıldığını bilmeniz gerekir.  
  
 <xref:System.Transactions> Altyapı, geçici kaynakları ve tek aşamalı bildirimleri destekleyen en fazla bir dayanıklı kaynağı işlediği sürece işlem, <xref:System.Transactions> altyapının sahipliğinin yerinde kalır. İşlem Yöneticisi, yalnızca aynı uygulama etki alanında yaşayan ve günlüğe kaydetme (işlem sonucunu diske yazma) gerekli olmayan kaynaklarla yalnızca kendisi için kullanılabilir. İşlemin sahipliğini MSDTC 'ye aktarma altyapısına <xref:System.Transactions> neden olan bir yükseltme, şu durumlarda oluşur:  
  
- Tek aşamalı bildirimleri desteklemeyen en az bir dayanıklı kaynak, işleme kayıtlı.  
  
- Tek aşamalı bildirimleri destekleyen en az iki dayanıklı kaynak, işleme kayıtlı. Örneğin, SQL Server 2005 ile tek bir bağlantının listelenmesi bir işlemin yükseltilmemesine neden olmaz. Ancak, bir SQL Server 2005 veritabanına ikinci bir bağlantı açtığınızda, <xref:System.Transactions> bu, altyapı işlemde ikinci dayanıklı kaynak olduğunu algılar ve bir MSDTC işlemine ilerletir.  
  
- İşlemi farklı bir uygulama etki alanına veya farklı bir işleme "sıralama" isteği çağrılır. Örneğin, bir uygulama etki alanı sınırı genelinde işlem nesnesinin serileştirilmesi. İşlem nesnesi değeri, bir uygulama etki alanı sınırı (aynı işlem içinde bile) üzerinde geçiş girişimleri işlem nesnesinin serileştirilmesi ile sonuçlanarak değere göre sıralanır. İşlem nesnelerini, parametre olarak bir <xref:System.Transactions.Transaction> olarak alan uzak bir yöntemde çağrı yaparak veya uzak bir işlem için hizmet veren bir bileşene erişmeye çalıştığınızda geçirebilirsiniz. Bu işlem nesnesini seri hale getirir ve bir işlem, bir uygulama etki alanı genelinde serileştirildiğinde olduğu gibi bir yükseltme işlemine neden olur. Dağıtılmakta ve yerel işlem yöneticisi artık yeterli değil.  
  
 Aşağıdaki tablo yükseltme sırasında oluşturulan tüm olası özel durumları listeler.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Yalıtım düzeyi eşit <xref:System.Transactions.IsolationLevel.Snapshot>olan bir işlemi bir işleme girişiminde bulunuldu.|  
|<xref:System.Transactions.TransactionAbortedException>|İşlem yöneticisi çalışmıyor.|  
|<xref:System.Transactions.TransactionException>|Yükseltme başarısız olur ve uygulama durduruldu.|
