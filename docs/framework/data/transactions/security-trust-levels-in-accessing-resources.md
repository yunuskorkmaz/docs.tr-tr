---
title: Kaynaklara Erişimde Güvenlik Güven Düzeyleri
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 847467b964e86f6d13be6ba103162512270fa684
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596753"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Kaynaklara Erişimde Güvenlik Güven Düzeyleri
Bu konuda, erişim kaynak türleri üzerinde nasıl kısıtlanır açıklar, <xref:System.Transactions> kullanıma sunar.  
  
 Güven için üç ana düzeyi <xref:System.Transactions>. Güven düzeyleri kaynak türleri göre tanımlanan, <xref:System.Transactions> kullanıma sunan ve bu kaynakları erişmek için gereken güven düzeyi. Kaynakları, <xref:System.Transactions> erişim sağlar sistem bellek, paylaşılan işlem geniş kaynakları ve uluslararası sistem kaynakları. Düzeyleri şunlardır:  
  
- **AllowPartiallyTrustedCallers** (APTCA) hareketleri içinde tek bir uygulama bir etki alanı kullanan uygulamalar için.  
  
- **DistributedTransactionPermission** (DTP) dağıtılmış işlemler kullanan uygulamalar için.  
  
- Kalıcı kaynakları, yapılandırma yönetimi uygulamaları ve eski birlikte çalışma uygulamaları için tam güven.  
  
> [!NOTE]
>  Herhangi bir Kimliğine bürünülen bağlamları olan liste arabirimler çağırmalıdır değil.  
  
## <a name="trust-levels"></a>Güven düzeyleri  
  
### <a name="aptca-partial-trust"></a>APTCA (kısmi güven)  
 <xref:System.Transactions> Derleme ile işaretlendiğinden kısmen güvenilen kod tarafından çağrılabilir **AllowPartiallyTrustedCallers** özniteliği (APTCA). Bu öznitelik temelde örtük kaldırır <xref:System.Security.Permissions.SecurityAction.LinkDemand> için **FullTrust** izni olan ayarlandı aksi otomatik olarak yerleştirilen her tür genel olarak erişilebilir her yönteminde üzerinde. Ancak, bazı türleri ve üyeleri hala daha güçlü izinleri gerektirir.  
  
 APTCA özniteliği uygulamaların tek bir uygulama etki alanı içinde kısmi güven işlemleri kullanmasını sağlar. Bu işlemler ilerletilmiş olmayan ve hata işleme için kullanılan geçici listeler sağlar. İşlenen karma tablo ve onu kullanan bir uygulama bu bir örnektir. Veri eklenen ve tek bir işlem altında karma tablo kaldırılır. İşlem daha sonra geri alınır, bu işlem altında karma tabloya yapılan değişiklikleri alınabilir.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Olduğunda bir <xref:System.Transactions> işlem ilerletilmiş MSDTC tarafından yönetilmek üzere <xref:System.Transactions> taleplerini <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış işlem oluşturmak için (DTP). İlerletilmiş işlem neden olan kod buna (gibi serileştirme veya ek kalıcı listeye aracılığıyla) DTP verilmesi gerekir. Özgün olarak oluşturulan kod <xref:System.Transactions> işlem gerekmeyen gerekmez bu izne sahip.  
  
### <a name="fulltrust-link-demands"></a>FullTrust bağlantı talepleri  
 Bu izin düzeyi kalıcı kaynaklara yazma uygulamaları sınırlamak üzere tasarlanmıştır. Başarısızlık durumunda, böylece kalıcı veri güncelleştirebilirsiniz işlem son sonucunu belirlemek için işlem yöneticisi ile kurtarabilmek için uygulama gerekir. Bu tür bir uygulama, sağlam kaynak yöneticisi olarak bilinir. Bir Klasik bu tür bir uygulama SQL örnektir.  
  
 Kurtarmayı etkinleştirmek için bu tür bir uygulama kalıcı olarak sistem kaynaklarının kullanılmasına olanağı vardır. İşlem sırasında katılan tüm kalıcı kaynak yöneticileri sonucu aldığınız onaylayabilirsiniz kadar taahhüt işlemler kurtarılabilir hareket yöneticisi unutmayın olmasıdır. Bu nedenle, bu tür bir uygulama tam güven gerektirir ve sürece çalıştırılmamalıdır güven düzeyi verilmiş.  
  
 Kalıcı listeye ve kurtarma hakkında daha fazla bilgi için bkz. [katılımcı bir işlemde kaynakları kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) ve [kurtarma gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md) konuları.  
  
 COM + ile birlikte çalışma eski çalışma gerçekleştirme uygulamaları de tam güven için gereklidir.  
  
 Türlerinin bir listesi aşağıda verilmiştir ve kısmen tarafından çağrılabilir olmayan üyeleri ile tasarlanmış çünkü kod güvenilir **FullTrust** bildirim temelli güvenlik özniteliği:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Yalnızca şu anki çağırıcı sahip gerekli **FullTrust** izin kümesinin yukarıdaki türleri veya yöntemlerini kullanın.
