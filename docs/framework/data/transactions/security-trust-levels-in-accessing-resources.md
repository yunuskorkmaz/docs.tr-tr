---
title: Kaynaklara erişimde güvenlik güven düzeyleri
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 8e7d632c361ea73cb65668e43506d9e1128d31ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-trust-levels-in-accessing-resources"></a>Kaynaklara erişimde güvenlik güven düzeyleri
Bu konuda kaynak türleri sınırlı erişimi nasıl ele alınmıştır, <xref:System.Transactions> kullanıma sunar.  
  
 Üç ana düzeyi için bir güven <xref:System.Transactions>. Güven düzeyleri kaynak türleri göre tanımlanır, <xref:System.Transactions> kullanıma sunar ve bu kaynaklara erişmek için gerekli güven düzeyi. Kaynakları, <xref:System.Transactions> erişim sağlar sistem bellek, paylaşılan işlem geniş kaynakları ve uluslararası sistem kaynakları. Düzeyleri şunlardır:  
  
-   **AllowPartiallyTrustedCallers** (APTCA) işlemleri tek bir uygulama etki alanı içinde kullanan uygulamalar için.  
  
-   **DistributedTransactionPermission** (DTP) dağıtılmış işlemler kullanan uygulamalar için.  
  
-   Dayanıklı kaynakları, yapılandırma yönetimi uygulamaları ve eski birlikte çalışma uygulamaları için tam güven.  
  
> [!NOTE]
>  Herhangi bir Kimliğine bürünülen bağlamları olan liste arabirimler çağırmalıdır değil.  
  
## <a name="trust-levels"></a>Güven düzeyleri  
  
### <a name="aptca-partial-trust"></a>APTCA (kısmi güven)  
 <xref:System.Transactions> Derleme ile işaretlendiğinden kısmen güvenilen kod tarafından çağrılabilir **AllowPartiallyTrustedCallers** özniteliği (APTCA). Bu öznitelik temelde örtük kaldırır <xref:System.Security.Permissions.SecurityAction.LinkDemand> için **FullTrust** diğer bir deyişle izni Aksi takdirde otomatik olarak yerleştirilen her türde genel olarak erişilebilir her yöntemin üzerinde. Ancak, bazı türleri ve üyeleri hala daha güçlü izinleri gerektirir.  
  
 APTCA özniteliği uygulamaların tek bir uygulama etki alanı içinde kısmi güvende işlemleri kullanmasını sağlar. Bu, ilerletilen olmayan işlemler ve hata işleme için kullanılan geçici listeler sağlar. İşlenen karma tablo ve onu kullanan bir uygulama bu bir örnektir. Veriler, eklenen ve tek bir işlem altında karma tablosundan kaldırıldı. İşlem daha sonra geri alınması durumunda, karma tablo bu işlem altında yapılan tüm değişiklikler geri alınabilir.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Zaman bir <xref:System.Transactions> MSDTC tarafından yönetilmek üzere işlem ilerletilen <xref:System.Transactions> taleplerini <xref:System.Transactions.DistributedTransactionPermission> dağıtılmış işlem oluşturmak için (DTP). Bu işlemin ilerletilen neden kodu anlamına gelir (gibi seri hale getirme veya ek dayanıklı kayıtlar aracılığıyla) DTP verilmiş olması gerekir. İlk olarak oluşturulan kodu <xref:System.Transactions> işlem mutlaka gerekmez bu izne sahip.  
  
### <a name="fulltrust-link-demands"></a>FullTrust bağlantı talepleri  
 Bu izin düzeyi dayanıklı kaynaklara yazma uygulamaları kısıtlamak için tasarlanmıştır. Başarısızlık durumunda, uygulama kalıcı veri güncelleştirebilmeniz için son işlem sonucunu belirlemek için işlem yöneticisi ile kurtarmanız mümkün olması gerekir. Bu tür bir uygulama, sağlam kaynak yöneticisi olarak bilinir. Bir Klasik bu tür bir uygulama SQL örnektir.  
  
 Kurtarmayı etkinleştirmek için bu tür bir uygulama kalıcı olarak sistem kaynaklarının kullanılmasına olanağı vardır. Bu durum, kurtarılabilir işlem yöneticisi işlemde katılan tüm dayanıklı kaynak yöneticileri sonucu aldığınız onaylayabilirsiniz kadar taahhüt işlemler unutmamanız gerekir çünkü. Bu nedenle, bu tür bir uygulama tam güven gerektiren ve sürece çalıştırılmamalıdır güven düzeyi verilmiş.  
  
 Dayanıklı listeler ve kurtarma hakkında daha fazla bilgi için bkz: [kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) ve [kurtarma gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md) Konular.  
  
 COM + ile birlikte çalışma eski iş gerçekleştiren uygulamalar da tam güven sağlamak için gereklidir.  
  
 Türlerinin bir listesi aşağıda verilmiştir ve kısmen tarafından çağrılabilir olmayan üyeler güvenilen kodu ile donatılmış olduğundan **FullTrust** bildirim temelli güvenlik özniteliği:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Anında arayanlar sahip olması gerekmez, yalnızca **FullTrust** izni Ayarla yukarıdaki türleri veya yöntemleri kullanmak için.
