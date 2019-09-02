---
title: Kaynaklara Erişimde Güvenlik Güven Düzeyleri
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 7070d82c430b762059153c544e26478dc2d7ae39
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205876"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Kaynaklara Erişimde Güvenlik Güven Düzeyleri
Bu konuda, erişimin <xref:System.Transactions> açığa çıkardığı kaynak türleri üzerinde nasıl sınırlandırıldığı anlatılmaktadır.  
  
 İçin <xref:System.Transactions>üç ana güven düzeyi vardır. Güven düzeyleri, <xref:System.Transactions> kullanıma sunan kaynak türlerine ve bu kaynaklara erişmek için gerekli olan güven düzeyine göre tanımlanır. Kaynakları, <xref:System.Transactions> erişim sağlar sistem bellek, paylaşılan işlem geniş kaynakları ve uluslararası sistem kaynakları. Düzeyleri şunlardır:  
  
- **Allowpartiallytrustedçağıranları** (APTCA), tek bir uygulama etki alanı içindeki işlemleri kullanan uygulamalar için.  
  
- **DistributedTransactionPermission** (DTP) dağıtılmış işlemler kullanan uygulamalar için.  
  
- Dayanıklı kaynaklar, yapılandırma yönetimi uygulamaları ve eski birlikte çalışma uygulamaları için tam güven.  
  
> [!NOTE]
> Herhangi bir Kimliğine bürünülen bağlamları olan liste arabirimler çağırmalıdır değil.  
  
## <a name="trust-levels"></a>Güven düzeyleri  
  
### <a name="aptca-partial-trust"></a>APTCA (kısmi güven)  
 , <xref:System.Transactions> **Allowpartiallytrustedçağıranlar** özniteliğiyle (aptca) işaretlendiğinden, derleme kısmen güvenilen kod tarafından çağrılabilir. Bu öznitelik, normalde her türden <xref:System.Security.Permissions.SecurityAction.LinkDemand> herkese açık olarak erişilebilen her metoda otomatik olarak eklenen **FullTrust** izin kümesi için örtük olarak kaldırılır. Ancak bazı türler ve Üyeler hala daha güçlü izinler gerektirir.  
  
 APTCA özniteliği, uygulamaların tek bir uygulama etki alanı içinde kısmi güvende işlemleri kullanmasına olanak sağlar. Bu, hatasız işlemler ve hata işleme için kullanılabilecek geçici listeler sunar. Bunun bir örneği, işlem temelli bir karma tablo ve onu kullanan bir uygulamadır. Veriler, tek bir işlem altında karma tabloya eklenebilir veya kaldırılabilir. İşlem daha sonra geri alınırsa, bu işlem altındaki karma tabloya yapılan tüm değişiklikler geri alınabilir.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Bir <xref:System.Transactions> işlem MSDTC tarafından yönetilmek üzere ilerlediğinde, <xref:System.Transactions> dağıtılmış işlemi oluşturmak için <xref:System.Transactions.DistributedTransactionPermission> (DTP) taleplerini ister. Bu, işlemin ilerlemesine neden olan kodun (serileştirme veya ek dayanıklı kayıtlar gibi) DTP verilmelidir. <xref:System.Transactions> İşlemin başlangıçta oluşturduğu kodun bu izne sahip olması gerekmez.  
  
### <a name="fulltrust-link-demands"></a>FullTrust bağlantı talepleri  
 Bu izin düzeyi, dayanıklı kaynaklara yazılan uygulamaları kısıtlamak için tasarlanmıştır. Hata sonrasında uygulamanın, kalıcı verileri güncelleştirebilmesi için işlemin son sonucunu belirleyebilmesi için işlem yöneticisi ile kurtarma yapabilmesi gerekir. Bu tür bir uygulama, sağlam kaynak yöneticisi olarak bilinir. Bir Klasik bu tür bir uygulama SQL örnektir.  
  
 Kurtarmayı etkinleştirmek için bu tür bir uygulama kalıcı olarak sistem kaynaklarının kullanılmasına olanağı vardır. Bunun nedeni, kurtarılabilir işlem yöneticisinin, işleme katılan tüm dayanıklı kaynak yöneticilerinin sonucu aldığını doğrulayacağından, taahhüt edilen işlemleri hatırlamaları gerekir. Bu nedenle, bu tür bir uygulama için tam güven gerekir ve bu güven düzeyi verilmediği takdirde çalıştırılmamalıdır.  
  
 Kalıcı listeler ve kurtarma hakkında daha fazla bilgi için bkz. [kaynakları bir işlem halinde katılımcılar halinde listeleme](enlisting-resources-as-participants-in-a-transaction.md) ve [kurtarma konuları gerçekleştirme](performing-recovery.md) .  
  
 Eski birlikte çalışabilirliğine sahip uygulamaların tam güvene sahip olması için de gereklidir.  
  
 Aşağıda, **FullTrust** bildirime dayalı güvenlik özniteliğiyle donatılmış olduklarından kısmen güvenilen kod tarafından çağrılabilir olmayan türlerin ve üyelerin listesi verilmiştir:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Yukarıdaki türleri veya yöntemleri kullanmak için **FullTrust** iznine sahip olması için yalnızca anında çağıranın kullanılması gerekir.
