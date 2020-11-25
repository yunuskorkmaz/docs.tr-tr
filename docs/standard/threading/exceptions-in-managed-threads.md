---
title: Yönetilen İş Parçacıklarında Özel Durumlar
description: İşlenmemiş özel durumların .NET 'te nasıl işlendiğini görün. İşlenmemiş iş parçacığı özel durumlarının çoğu doğal olarak devam edip uygulama sonlandırmasına yol açabilir.
ms.date: 03/30/2017
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET],unhandled exceptions
- threading [.NET],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 740cd1b78b96c2fcaecf39a725973d738037f403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723759"
---
# <a name="exceptions-in-managed-threads"></a>Yönetilen iş parçacıklarında özel durumlar

Ortak dil çalışma zamanı, iş parçacıklarında işlenmemiş özel durumların çoğunu doğal olarak devam etmesine izin verir Çoğu durumda bu, işlenmeyen özel durumun uygulamanın sonlandırılmasına neden olduğu anlamına gelir.
  
Ortak dil çalışma zamanı, program akışını denetlemek için kullanılan, işlenmemiş özel durumlar için bir geri durağı sağlar:  
  
- <xref:System.Threading.ThreadAbortException>Çağrıldığında bir iş parçacığında oluşturulur <xref:System.Threading.Thread.Abort%2A> .  
  
- İş parçacığı üzerinde <xref:System.AppDomainUnloadedException> yürütülmekte olan uygulama etki alanı kaldırılmakta olduğundan bir iş parçacığında oluşturulur.  
  
- Ortak dil çalışma zamanı veya bir konak işlemi, bir iç özel durum oluşturarak iş parçacığını sonlandırır.  
  
 Bu özel durumların herhangi biri ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında yakalanmadıysa, özel durum iş parçacığını sonlandırır, ancak ortak dil çalışma zamanı özel durumun daha fazla devam edeceğine izin vermez.  
  
 Bu özel durumlar ana iş parçacığında işlenmemiş veya yönetilmeyen koddan çalışma zamanına giren iş parçacıklarında, normalde devam ederler ve uygulamanın sonlandırmasına yol açar.  
  
> [!NOTE]
> Yönetilen herhangi bir kodun özel durum işleyicisi yüklemesi şansı olmadan önce, çalışma zamanının işlenmeyen bir özel durum oluşturması mümkündür. Yönetilen kodun böyle bir özel durumu işleme şansı olmasa da, özel durumun doğal olarak devam etmesi için izin verilir.  
  
## <a name="exposing-threading-problems-during-development"></a>Geliştirme sırasında Iş parçacığı sorunlarını gösterme  

 İş parçacıklarının sessizce başarısız olmasına izin verildiğinde, uygulamayı sonlandırmadan ciddi programlama sorunları saptanmayabilir. Bu, gelişmiş dönemler için çalışan hizmetler ve diğer uygulamalar için özel bir sorundur. İş parçacıkları başarısız olduğu sürece program durumu yavaş yavaş bozulur. Uygulama performansı düşebilir veya uygulama yanıt vermiyor olabilir.  
  
 İşletim sistemi programı sonlandırana kadar, iş parçacıklarında işlenmeyen özel durumların doğal olarak devam etmesini sağlamak, geliştirme ve test sırasında böyle sorunlar ortaya çıkarır. Program sonlandırışları üzerindeki hata raporları hata ayıklamayı destekler.  
  
## <a name="change-from-previous-versions"></a>Önceki sürümlerden Değiştir

.NET Framework sürüm 1,0 ve 1,1 ' de, ortak dil çalışma zamanı, işlenmemiş özel durumlar için aşağıdaki durumlarda bir geri durağı sağlar:  
  
- İş parçacığı havuzu iş parçacığında işlenmemiş özel durum gibi bir şey yoktur. Bir görev, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve iş parçacığını iş parçacığı havuzuna döndürür.  
  
- Sınıf yöntemiyle oluşturulan bir iş parçacığında işlenmemiş özel durum olarak böyle bir şey yoktur <xref:System.Threading.Thread.Start%2A> <xref:System.Threading.Thread> . Böyle bir iş parçacığı üzerinde çalışan kod, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra iş parçacığını normal şekilde sonlandırır.  
  
- Sonlandırıcı iş parçacığında işlenmeyen bir özel durum yok. Bir Sonlandırıcı, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra Sonlandırıcı iş parçacığının sonlandırıcıları çalıştırmaya sürdürmesini sağlar.  
  
 Yönetilen bir iş parçacığının ön plan veya arka plan durumu bu davranışı etkilemez.  
  
 Yönetilmeyen kodda oluşan iş parçacıklarında işlenmeyen özel durumlar için, fark daha hafif olur. Çalışma zamanı JıT-iliştirme iletişim kutusu, yönetilen özel durumlar veya yerel kod üzerinden geçen iş parçacıklarında yerel özel durumlar için işletim sistemi iletişim kutusunu preempts. İşlem her durumda sonlandırılır.

### <a name="migration"></a>Geçiş

.NET Framework 1,0 veya 1,1 ' den geçiş yapıyorsanız ve çalışma zamanı geri durağı avantajlarından yararlanarak, örneğin iş parçacıklarını sonlandırmak için aşağıdaki geçiş stratejilerinden birini göz önünde bulundurun:  
  
- Bir sinyal alındığında iş parçacığının düzgün bir şekilde çıkış yapabilmesi için kodu yeniden yapılandır.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>İş parçacığını durdurmak için yöntemini kullanın.  
  
- İşlem sonlandırmasının devam edebilmesi için bir iş parçacığının durdurulması gerekiyorsa, işlem çıkışında otomatik olarak sonlandırılmak için iş parçacığını bir arka plan iş parçacığı yapın.  
  
Her durumda, strateji özel durumlar için tasarım kılavuzunu izlemelidir. [Özel durumlar Için tasarım yönergelerine](../design-guidelines/exceptions.md)bakın.  
  
Geçici bir uyumluluk ölçüsü olarak, Yöneticiler `<runtime>` uygulama yapılandırma dosyasının bölümüne bir uyumluluk bayrağı yerleştirebilir. Bu, ortak dil çalışma zamanının 1,0 ve 1,1 sürümlerinin davranışına dönüşmesine neden olur.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Konak geçersiz kılma

Yönetilmeyen bir konak, ortak dil çalışma zamanının varsayılan işlenmemiş özel durum ilkesini geçersiz kılmak için barındırma API 'sindeki [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimini kullanabilir. [ICLRPolicyManager:: SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi, işlenmemiş özel durumlar için ilkeyi ayarlamak üzere kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](managed-threading-basics.md)
