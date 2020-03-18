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
ms.openlocfilehash: 6c14c60b30f8f70aa5e888ed45d6f867154e18d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159656"
---
# <a name="exceptions-in-managed-threads"></a>Yönetilen İş Parçacıklarında Özel Durumlar
.NET Framework sürüm 2.0 ile başlayarak, ortak dil çalışma süresi işlenmemiş çoğu özel durum iş parçacığı doğal olarak devam sağlar. Çoğu durumda bu, işlenmemiş özel durum uygulamanın sonlandırılmasına neden olduğu anlamına gelir.  
  
> [!NOTE]
> Bu, işlenmemiş birçok özel durum için bir stoper sağlayan .NET Framework sürümleri 1.0 ve 1.1'den önemli bir değişikliktir — örneğin, iş parçacığı havuzu iş parçacıklarındaki işlenmemiş özel durumlar. Bu konunun ilerleyen saatlerinde [Önceki Sürümlerden Değişiklik'e](#ChangeFromPreviousVersions) bakın.  
  
 Ortak dil çalışma süresi, program akışını denetlemek için kullanılan bazı işlenmemiş özel durumlar için bir durak sağlar:  
  
- A <xref:System.Threading.ThreadAbortException> çağrıldığı için <xref:System.Threading.Thread.Abort%2A> bir iş parçacığı atılır.  
  
- İş <xref:System.AppDomainUnloadedException> parçacığının yürütüldettiği uygulama etki alanı kaldırıldığından, iş parçacığına bir iş parçacığı atılır.  
  
- Ortak dil çalışma süresi veya ana bilgisayar işlemi, iç özel durum atarak iş parçacığı sonlandırır.  
  
 Bu özel durumlardan herhangi biri ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında işlenmemişse, özel durum iş parçacığı sonlandırır, ancak ortak dil çalışma süresi özel durum daha fazla devam etmesine izin vermez.  
  
 Bu özel durumlar ana iş parçacığında veya yönetilmeyen koddan çalışma zamanı giren iş parçacıklarında işlenmemişse, normal olarak devam eder ve bu da uygulamanın sonlandırılmasıyla sonuçlanır.  
  
> [!NOTE]
> Yönetilen herhangi bir kodun bir özel durum işleyicisi yükleme şansı olmadan önce çalışma zamanının işlenmemiş bir özel durum atması mümkündür. Yönetilen kodun böyle bir özel durumu işleme şansı olmamasına rağmen, özel durum doğal olarak devam etmesine izin verilir.  
  
## <a name="exposing-threading-problems-during-development"></a>Geliştirme Sırasında İş Parçacığı Sorunlarının Açığa Çıkarılması  
 İş parçacıklarının uygulamayı sonlandırmadan sessizce başarısız olması izin verildiğinde, ciddi programlama sorunları algılanmadan gidebilir. Bu, uzun süre çalışan hizmetler ve diğer uygulamalar için özel bir sorundur. İş parçacıkları başarısız olduğunda, program durumu yavaş yavaş bozulur. Uygulama performansı bozulabilir veya uygulama yanıt vermese dönüşebilir.  
  
 İşletim sistemi programı sonlandırına kadar iş parçacıklarındaki işlenmemiş özel durumların doğal olarak ilerlemesine izin vermek, geliştirme ve sınama sırasında bu tür sorunları ortaya çıkarır. Program sonlandırmalarına ilişkin hata raporları hata ayıklamayı destekler.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Önceki Sürümlerden Değişiklik  
 En önemli değişiklik yönetilen iş parçacıkları ile ilgilidir. .NET Framework sürümleri 1.0 ve 1.1'de, ortak dil çalışma süresi aşağıdaki durumlarda işlenmemiş özel durumlar için bir stoper sağlar:  
  
- İş parçacığı havuzu iş parçacığı üzerinde işlenmemiş bir özel durum olarak bir şey yoktur. Bir görev işlemediği bir özel durum attığında, çalışma zamanı özel durum yığınını konsola yazdırır ve iş parçacığı havuzuna döndürür.  
  
- <xref:System.Threading.Thread> Sınıfın <xref:System.Threading.Thread.Start%2A> yöntemi yle oluşturulan bir iş parçacığı üzerinde işlenmemiş özel durum diye bir şey yoktur. Böyle bir iş parçacığı üzerinde çalışan kod işlemediği bir özel durum attığında, çalışma zamanı özel durum yığını nı konsola yazdırır ve iş parçacığı düzgün bir şekilde sonlandırır.  
  
- Sonlandırıcı iş parçacığı üzerinde işlenmemiş bir özel durum olarak bir şey yoktur. Bir sonlandırıcı işlemediği bir özel durum attığında, çalışma zamanı özel durum yığınıizlemesini konsola yazdırır ve sonlandırıcı iş parçacığının sonlandırıcıları çalıştırmaya devam etmesine izin verir.  
  
 Yönetilen bir iş parçacığının ön plan veya arka plan durumu bu davranışı etkilemez.  
  
 Yönetilmeyen kod kaynaklı iş parçacıkları üzerinde işlenmemiş özel durumlar için fark daha ince. Çalışma zamanı JIT ekleme iletişim kutusu, yerel koddan geçen iş parçacıklarındaki yönetilen özel durumlar veya yerel özel durumlar için işletim sistemi iletişim kutusunu önler. İşlem her durumda sona erer.  
  
### <a name="migrating-code"></a>Geçiş Kodu  
 Genel olarak, değişiklik, düzeltilebilmeleri için daha önce tanınmayan programlama sorunlarını ortaya çıkarır. Ancak bazı durumlarda, programcılar iş parçacıklarını sonlandırmak için çalışma süresi stop'undan yararlanmış olabilir. Duruma bağlı olarak, aşağıdaki göç stratejilerinden birini göz önünde bulundurmalıdırlar:  
  
- Bir sinyal geldiğinde iş parçacığı nın zarif bir şekilde çıkması için kodu yeniden yapılandırın.  
  
- İş <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> parçacığı iptal etmek için yöntemi kullanın.  
  
- İşlem sonlandırma işleminin devam edilebilsin diye bir iş parçacığının durdurulması gerekiyorsa, işlem çıkışında otomatik olarak sonlandırılabilmesi için iş parçacığının bir arka plan iş parçacığı haline getirin.  
  
 Her durumda, strateji özel durumlar için tasarım yönergelerine uymalıdır. [Özel Durumlar için Tasarım Yönergeleri'ne](../../../docs/standard/design-guidelines/exceptions.md)bakın.  
  
### <a name="application-compatibility-flag"></a>Uygulama Uyumluluk Bayrağı  
 Geçici bir uyumluluk önlemi olarak, yöneticiler uygulama `<runtime>` yapılandırma dosyasının bölümüne bir uyumluluk bayrağı yerzesin. Bu, ortak dil çalışma zamanının 1.0 ve 1.1 sürümlerinin davranışına geri dönülmesine neden olur.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Ana Bilgisayar Geçersiz Kılma  
 .NET Framework sürüm 2.0'da, yönetilmeyen bir ana bilgisayar, ortak dil çalışma zamanının varsayılan işlenmemiş özel durum ilkesini geçersiz kılmak için Barındırma API'sindeki [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimini kullanabilir. [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi işlenmemiş özel durumlar için ilke ayarlamak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
