---
title: "Yönetilen İş Parçacıklarında Özel Durumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a>Yönetilen İş Parçacıklarında Özel Durumlar
.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanı en işlenmeyen özel durumlar doğal olarak devam etmek için iş parçacığı sağlar. Çoğu durumda bu işlenmeyen bir özel durum için uygulamanın neden olduğunu anlamına gelir.  
  
> [!NOTE]
>  Bu önemli bir backstop sağlamak için birçok işlenmeyen özel durumlar 1.0 ve 1.1, .NET Framework sürümleri farklıdır — Örneğin, iş parçacığı havuzu iş parçacıklarında özel durumlar işlenmemiş. Bkz: [değiştirmek önceki sürümlerden](#ChangeFromPreviousVersions) bu konuda daha sonra.  
  
 Ortak dil çalışma zamanı program akışı denetimi için kullanılan bir backstop belirli işlenmeyen özel durumlar sağlar:  
  
-   A <xref:System.Threading.ThreadAbortException> bir iş parçacığı, çünkü atılır <xref:System.Threading.Thread.Abort%2A> çağrıldı.  
  
-   Bir <xref:System.AppDomainUnloadedException> iş parçacığı Yürütülüyor uygulama etki alanı bellekten çünkü bir iş parçacığında oluşturulur.  
  
-   Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi iş parçacığı bir iç özel durum atma tarafından sonlandırır.  
  
 Bu özel durumlar hiçbirini ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında işlenmemiş, özel iş parçacığı sonlanır, ancak ortak dil çalışma zamanı devam etmek özel durum izin vermiyor.  
  
 Bu özel durumlar ana iş parçacığı veya yönetilmeyen koddan çalışma zamanı girilen iş parçacığı işlenmeyen varsa, bunlar normalde, uygulamanın sonlandırılmasıyla kaynaklanan devam edin.  
  
> [!NOTE]
>  Yönetilen kod bir özel durum işleyici yüklemek için bir fırsat dolmadığı önce işlenmeyen bir özel durum atmak için çalışma zamanı için mümkündür. Yönetilen kod gibi özel bir durumu işlemek için hiçbir şansınız olsa bile, özel durum doğal olarak devam etmesine izin verilir.  
  
## <a name="exposing-threading-problems-during-development"></a>Geliştirme sırasında sorunları iş parçacığı oluşturma gösterme  
 İş parçacığı uygulama sonlandırma olmadan sessizce başarısız olmasına izin verildiğinde programlama ciddi sorunlar algılanmayabilir. Bu, hizmetler ve uzun süre çalışan diğer uygulamalar için belirli bir sorundur. Başarısız iş parçacıkları gibi program durumu kademeli olarak bozulur. Uygulama performansı düşebilir veya uygulama askıda.  
  
 İşletim sistemi program sonlanana kadar doğal olarak, devam etmek için iş parçacığı işlenmeyen özel durumlar izin vererek bu tür sorunları geliştirme ve sınama sırasında kullanıma sunar. Program sonlandırmalar hata ayıklama desteği üzerinde hata bildirir.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Önceki sürümlerden değiştirme  
 Yönetilen iş parçacığı için en önemli değişiklik ilgilidir. .NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı aşağıdaki durumlarda işlenmeyen özel durumlar için bir backstop sağlar:  
  
-   Bir iş parçacığı havuzu iş parçacığı işlenmeyen bir özel olarak bu tür bir şey yoktur. Bir görev, işlemiyor bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve iş parçacığı iş parçacığı havuzuna döndürür.  
  
-   Bir iş parçacığı işlenmeyen özel durum ile oluşturulmuş böyle bir şey olduğunu <xref:System.Threading.Thread.Start%2A> yöntemi <xref:System.Threading.Thread> sınıfı. Böyle bir iş parçacığı üzerinde çalışan kodu değil işleyecek bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve iş parçacığı düzgün biçimde sonlanır.  
  
-   Sonlandırıcı iş parçacığı işlenmeyen özel durum olarak böyle bir şey yoktur. Bir sonlandırıcı olmayan işleyecek bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve sonlandırıcılar çalışmasını devam ettirmek sonlandırıcıyı iş parçacığı sağlar.  
  
 Yönetilen iş parçacığı ön plan veya arka plan durumunu bu davranışını etkilemez.  
  
 İş parçacıklarını yönetilmeyen kodunda kaynaklanan işlenmeyen özel durumlar için daha hafif farktır. Çalışma zamanı JIT-ekleme iletişim yönetilen özel durumlar veya aracılığıyla yerel koda geçtiğinde iş parçacığı yerel özel durumlar için işletim sistemi iletişim etkisiz hale getiren. Tüm durumlarda işlemi sonlandırır.  
  
### <a name="migrating-code"></a>Geçirme kodu  
 Genel olarak, böylece bunlar sabit değişikliği önceden tanınmayan programlama sorunlarını açığa çıkarır. Bazı durumlarda, ancak programcıları örneğin iş parçacıklarını sonlandırma çalışma zamanı backstop avantajlarından gerçekleştirmişsiniz. Durum bağlı olarak, aşağıdaki geçiş stratejiler birini dikkate alın:  
  
-   Sinyal alındığında iş parçacığı düzgün biçimde çıkar şekilde kodu yeniden yapılandırabilirsiniz.  
  
-   Kullanım <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacığı iptal etmek için yöntem.  
  
-   İşlem sonlandırma devam edebilirsiniz böylece bir iş parçacığı durdurulması gerekir, böylece işlem Çıkışta otomatik olarak sona erdi iş parçacığı bir arka plan iş parçacığı olun.  
  
 Tüm durumlarda stratejisi özel durumlar için tasarım yönergeleri izlemelidir. Bkz: [tasarım yönergeleri için özel durumları](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Uygulama uyumluluk bayrağı  
 Geçici uyumluluk ölçü olarak bir uyumluluk bayrağı Yöneticiler yerleştirebilirsiniz `<runtime>` uygulama yapılandırma dosyasının. Bu, 1.0 ve 1.1 sürümleri davranışa geri dönmek ortak dil çalışma zamanı neden olur.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Ana bilgisayar geçersiz kılma  
 .NET Framework sürüm 2. 0'da, yönetilmeyen bir ana bilgisayar kullanabilirsiniz [Iclrpolicymanager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) varsayılan geçersiz kılmak için barındırma API arabiriminde işlenmeyen özel durum ilkesi ortak dil çalışma zamanı. [Iclrpolicymanager::setunhandledexceptionpolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi işlenmeyen özel durumlar için ilkesini ayarlamak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
