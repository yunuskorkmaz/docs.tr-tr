---
title: Yönetilen İş Parçacıklarında Özel Durumlar
description: İşlenmemiş özel durumların .NET 'te nasıl işlendiğini görün. .NET sürüm 2,0 ile, işlenmemiş iş parçacığı özel durumları doğal olarak devam edecek ve uygulama sonlandırmasına neden olacak.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
ms.openlocfilehash: 2facb68c77815de7a6fb97ab8f2ee683ffbad724
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767890"
---
# <a name="exceptions-in-managed-threads"></a>Yönetilen İş Parçacıklarında Özel Durumlar
.NET Framework sürüm 2,0 ' den başlayarak, ortak dil çalışma zamanı, iş parçacıklarında birçok işlenmemiş özel durumun doğal olarak devam etmesine izin verir. Çoğu durumda bu, işlenmeyen özel durumun uygulamanın sonlandırılmasına neden olduğu anlamına gelir.  
  
> [!NOTE]
> Bu, çok sayıda işlenmemiş özel durum için geri durağı sağlayan 1,0 ve 1,1 .NET Framework sürümlerinden önemli bir değişiklikten (örneğin, iş parçacığı havuzu iş parçacıklarında işlenmemiş özel durumlar). Bu konunun ilerleyen kısımlarında bulunan [önceki sürümlerden değişiklik](#ChangeFromPreviousVersions) bölümüne bakın.  
  
 Ortak dil çalışma zamanı, program akışını denetlemek için kullanılan, işlenmemiş özel durumlar için bir geri durağı sağlar:  
  
- <xref:System.Threading.ThreadAbortException>Çağrıldığında bir iş parçacığında oluşturulur <xref:System.Threading.Thread.Abort%2A> .  
  
- İş parçacığı üzerinde <xref:System.AppDomainUnloadedException> yürütülmekte olan uygulama etki alanı kaldırılmakta olduğundan bir iş parçacığında oluşturulur.  
  
- Ortak dil çalışma zamanı veya bir konak işlemi, bir iç özel durum oluşturarak iş parçacığını sonlandırır.  
  
 Bu özel durumların herhangi biri ortak dil çalışma zamanı tarafından oluşturulan iş parçacıklarında yakalanmadıysa, özel durum iş parçacığını sonlandırır, ancak ortak dil çalışma zamanı özel durumun daha fazla devam edeceğine izin vermez.  
  
 Bu özel durumlar ana iş parçacığında işlenmemiş veya yönetilmeyen koddan çalışma zamanına giren iş parçacıklarında, normalde devam ederler ve uygulamanın sonlandırmasına yol açar.  
  
> [!NOTE]
> Yönetilen herhangi bir kodun özel durum işleyicisi yüklemesi şansı olmadan önce, çalışma zamanının işlenmeyen bir özel durum oluşturması mümkündür. Yönetilen kodun böyle bir özel durumu işleme şansı olmasa da, özel durumun doğal olarak devam etmesi için izin verilir.  
  
## <a name="exposing-threading-problems-during-development"></a>Geliştirme sırasında Iş parçacığı sorunlarını gösterme  
 İş parçacıklarının sessizce başarısız olmasına izin verildiğinde, uygulamayı sonlandırmadan ciddi programlama sorunları saptanmayabilir. Bu, geliştirilmiş dönemler için çalışan hizmetler ve diğer uygulamalar için özel bir sorundur. İş parçacıkları başarısız olduğu sürece program durumu yavaş yavaş bozulur. Uygulama performansı düşebilir veya uygulama yanıt vermiyor olabilir.  
  
 İşletim sistemi programı sonlandırana kadar, iş parçacıklarında işlenmeyen özel durumların doğal olarak devam etmesini sağlamak, geliştirme ve test sırasında böyle sorunlar ortaya çıkarır. Program sonlandırışları üzerindeki hata raporları hata ayıklamayı destekler.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Önceki sürümlerden Değiştir  
 En önemli değişiklik, yönetilen iş parçacıkları ile ilgilidir. .NET Framework sürüm 1,0 ve 1,1 ' de, ortak dil çalışma zamanı, işlenmemiş özel durumlar için aşağıdaki durumlarda bir geri durağı sağlar:  
  
- İş parçacığı havuzu iş parçacığında işlenmemiş özel durum gibi bir şey yoktur. Bir görev, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve iş parçacığını iş parçacığı havuzuna döndürür.  
  
- Sınıf yöntemiyle oluşturulan bir iş parçacığında işlenmemiş özel durum olarak böyle bir şey yoktur <xref:System.Threading.Thread.Start%2A> <xref:System.Threading.Thread> . Böyle bir iş parçacığı üzerinde çalışan kod, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra iş parçacığını normal şekilde sonlandırır.  
  
- Sonlandırıcı iş parçacığında işlenmeyen bir özel durum yok. Bir Sonlandırıcı, işlenmeyen bir özel durum oluşturduğunda, çalışma zamanı özel durum yığın izlemesini konsola yazdırır ve sonra Sonlandırıcı iş parçacığının sonlandırıcıları çalıştırmaya sürdürmesini sağlar.  
  
 Yönetilen bir iş parçacığının ön plan veya arka plan durumu bu davranışı etkilemez.  
  
 Yönetilmeyen kodda oluşan iş parçacıklarında işlenmeyen özel durumlar için, fark daha hafif olur. Çalışma zamanı JıT-iliştirme iletişim kutusu, yönetilen özel durumlar veya yerel kod üzerinden geçen iş parçacıklarında yerel özel durumlar için işletim sistemi iletişim kutusunu preempts. İşlem her durumda sonlandırılır.  
  
### <a name="migrating-code"></a>Kodu geçirme  
 Genellikle, değişiklik, daha önce tanınmayan programlama sorunlarını düzeltilmek üzere kullanıma sunacaktır. Ancak, bazı durumlarda programcılar çalışma zamanı geri 'den faydalanabilir, örneğin iş parçacıklarını sonlandırmak için. Duruma bağlı olarak, aşağıdaki geçiş stratejilerinden birini göz önünde bulundurmalıdır:  
  
- Bir sinyal alındığında iş parçacığının düzgün bir şekilde çıkış yapabilmesi için kodu yeniden yapılandır.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>İş parçacığını durdurmak için yöntemini kullanın.  
  
- İşlem sonlandırmasının devam edebilmesi için bir iş parçacığının durdurulması gerekiyorsa, işlem çıkışında otomatik olarak sonlandırılmak için iş parçacığını bir arka plan iş parçacığı yapın.  
  
 Her durumda, strateji özel durumlar için tasarım kılavuzunu izlemelidir. [Özel durumlar Için tasarım yönergelerine](../design-guidelines/exceptions.md)bakın.  
  
### <a name="application-compatibility-flag"></a>Uygulama uyumluluğu bayrağı  
 Geçici bir uyumluluk ölçüsü olarak, Yöneticiler `<runtime>` uygulama yapılandırma dosyasının bölümüne bir uyumluluk bayrağı yerleştirebilir. Bu, ortak dil çalışma zamanının 1,0 ve 1,1 sürümlerinin davranışına dönüşmesine neden olur.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Konak geçersiz kılma  
 .NET Framework sürüm 2,0 ' de, yönetilmeyen bir konak, ortak dil çalışma zamanının varsayılan işlenmemiş özel durum ilkesini geçersiz kılmak için barındırma API 'sindeki [ICLRPolicyManager](../../framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimini kullanabilir. [ICLRPolicyManager:: SetUnhandledExceptionPolicy](../../framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) işlevi, işlenmemiş özel durumlar için ilkeyi ayarlamak üzere kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](managed-threading-basics.md)
