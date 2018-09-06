---
title: Yönetilen İş Parçacıklarında Özel Durumlar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63931f4498f4c1f313e7980b91ef712d4a46a837
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865185"
---
# <a name="exceptions-in-managed-threads"></a>Yönetilen İş Parçacıklarında Özel Durumlar
.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma zamanı doğal olarak devam etmek için iş parçacıklarının en işlenmeyen özel durumları tanır. Çoğu durumda bu işlenmeyen özel durumu uygulamanın sonlandırılmasına neden anlamına gelir.  
  
> [!NOTE]
>  Bu önemli bir backstop sağlamak için birçok işlenmeyen özel durumları 1.0 ve 1.1 .NET Framework sürümlerini farklıdır — Örneğin, iş parçacığı havuzu iş parçacıklarında özel durumlar işlenmemiş. Bkz: [değiştirme önceki sürümlerden](#ChangeFromPreviousVersions) bu konunun devamındaki.  
  
 Ortak dil çalışma zamanı program akışı denetimi için kullanılan bir backstop belirli işlenmeyen özel durumları sağlar:  
  
-   A <xref:System.Threading.ThreadAbortException> çünkü bir iş parçacığında oluşturulan <xref:System.Threading.Thread.Abort%2A> çağrıldı.  
  
-   Bir <xref:System.AppDomainUnloadedException> iş parçacığı yürütüyordur uygulama etki alanı kaldırıldı çünkü bir dizi oluşturulur.  
  
-   Ortak dil çalışma zamanı ya da bir ana bilgisayar işlemi bir iç özel durum tarafından iş parçacığı sonlanır.  
  
 Herhangi birini bu özel durumları iş parçacıklarında ortak dil çalışma zamanı tarafından oluşturulan işlenmemiş özel durum iş parçacığı sonlanır, ancak ortak dil çalışma zamanı özel durumu, devam etmek izin vermez.  
  
 Bu özel durumlar ana iş parçacığı veya bir çalışma zamanı yönetilmeyen koddan girilen iş parçacığı işlenmeyen varsa, bunlar normal olarak, uygulamanın sonlandırılmasıyla kaynaklanan devam edin.  
  
> [!NOTE]
>  Önce herhangi bir yönetilen kod bir özel durum işleyicisi yüklemek için bir fırsat işlenmeyen bir özel durum oluşturmak için çalışma zamanı için mümkündür. Yönetilen kod gibi bir özel durumu işlemek için hiçbir şansınız olsa da, özel durum doğal olarak devam etmesine izin verilir.  
  
## <a name="exposing-threading-problems-during-development"></a>Sorunları, geliştirme sırasında iş parçacığı gösterme  
 İş parçacıkları sessiz bir şekilde, uygulamayı sonlandırmadan başarısız olmasına izin verildiğinde programlama ciddi sorunlar algılanmayabilir. Bu, hizmetlerin ve uzun süre çalışan diğer uygulamaların belirli bir sorundur. Başarısız iş parçacıkları gibi program durumunu kademeli olarak bozulur. Uygulama performansı düşebilir veya uygulama askıda.  
  
 Doğal olarak, işletim sistemi program sonlanana kadar devam etmek için iş parçacığı işlenmeyen özel durumlara izin sorunları, geliştirme ve test sırasında sunar. Program sonlandırmalar hata ayıklama desteği üzerinde hata bildirir.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Önceki sürümlerden değiştirme  
 Yönetilen iş parçacıkları için en önemli değişiklik ilgilidir. .NET Framework sürüm 1.0 ve 1.1, ortak dil çalışma zamanı aşağıdaki durumlarda işlenmeyen özel durumlara ilişkin bir backstop sağlar:  
  
-   Bir iş parçacığı havuzu iş parçacığı üzerinde işlenmeyen bir özel durum de yoktur. Bir görev değil işleyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve iş parçacığının iş parçacığı havuzuna döndürür.  
  
-   Bir iş parçacığında işlenmeyen bir özel durum ile oluşturulmuş gibi bir şey olduğunu <xref:System.Threading.Thread.Start%2A> yöntemi <xref:System.Threading.Thread> sınıfı. Böyle bir iş parçacığı üzerinde çalışan kodu değil işleyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve düzgün bir şekilde iş parçacığı sonlanır.  
  
-   Sonlandırıcı iş parçacığı işlenmeyen bir özel olarak böyle bir şey yoktur. Bir sonlandırıcı olmayan işleyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesi konsola yazdırır ve ardından sonlandırıcılar çalıştırmayı sürdürmek herhangi bir sonlandırıcı sağlar.  
  
 Yönetilen iş parçacığı ön plan veya arka plan durum, bu davranışı etkilemez.  
  
 Yönetilmeyen kodda kaynaklanan iş parçacığı işlenmeyen özel durumlar için fark daha inceliklidir. Çalışma zamanı JIT-ekleme iletişim kutusu, yönetilen özel durumlar veya yerel kod arasında geçen iş parçacığı yerel özel durumları için işletim sistemi iletişim preempts. Her durumda işlemi sonlandırır.  
  
### <a name="migrating-code"></a>Kod geçirme  
 Genel olarak, değişiklik düzeltilebilir böylece daha önce tanınmayan programlama sorunları açığa çıkarır. Bazı durumlarda, ancak programcılar örneğin iş parçacıklarını sonlandırma çalışma zamanı backstop avantajlarından almış. Duruma bağlı olarak, aşağıdaki geçiş stratejileri birini düşünmelisiniz:  
  
-   Kod, sinyal alındığında düzgün bir şekilde iş parçacığından çıkar şekilde yeniden yapılandırabilirsiniz.  
  
-   Kullanım <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> iş parçacığını durdurmak için yöntemi.  
  
-   İşlem sonlandırma devam edebilmeniz adına bir iş parçacığı durdurulması gerekir, böylece otomatik olarak işlem çıkış sonlandırılır iş parçacığı bir arka plan iş parçacığı sağlayın.  
  
 Her durumda, strateji özel durumlar için tasarım yönergeleri izlemelidir. Bkz: [özel durumlar için tasarım yönergeleri](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Uygulama uyumluluk bayrağı  
 Geçici uyumluluk önlemi olarak, Yöneticiler bir uyumluluk bayrağı yerleştirebilirsiniz `<runtime>` uygulama yapılandırma dosyası bölümünü. Bu, 1.0 ve 1.1 sürümlerinde, davranıştır dönmek ortak dil çalışma zamanı neden olur.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Ana bilgisayar geçersiz kılma  
 .NET Framework sürüm 2. 0'da, yönetilmeyen bir konak kullanabilirsiniz [Iclrpolicymanager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) varsayılan geçersiz kılmak için barındırma API Arabirimi işlenmeyen özel durum ilkesi ortak dil çalışma zamanı. [Iclrpolicymanager::setunhandledexceptionpolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi, işlenmemiş özel durumlar için ilke ayarlamak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
