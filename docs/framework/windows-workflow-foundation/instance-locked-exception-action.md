---
title: "Özel eylem örneği kilitli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b221b0eef1e132789ef04fb59b56126f023bc43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="instance-locked-exception-action"></a>Özel eylem örneği kilitli
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> Özelliği SQL iş akışı örneği deposunun SQL Kalıcılık sağlayıcısı tarafından alındığında almalıdır eylemi belirtmenize olanak sağlar bir <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Başka bir hizmet ana bilgisayarı tarafından şu anda kilitli bir iş akışı hizmeti örneği kilitlemek çalıştığında, bu özel Kalıcılık sağlayıcısı alır. Bu özellik için değerler <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, ve <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Varsayılan değer <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> şeklindedir. Aşağıdaki listede üç seçenekten açıklanmaktadır:  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. Hizmet ana bilgisayarı iş akışı hizmet örneği ve geçişleri kilitlemek denemez <xref:System.Runtime.DurableInstancing.InstanceLockedException> çağırana.  İş akışınızı 60 saniye aşan bir dönem için bellekte kalırsa kullanmak <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> olarak yeniden deneyin. Varsayılan değer <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> şeklindedir.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. Hizmet ana bilgisayarı reattempts yeniden deneme girişimleri arasındaki geçişleri doğrusal bir aralığı iş akışı hizmeti örneğiyle kilitlemek <xref:System.Runtime.DurableInstancing.InstanceLockedException> dizisi sonunda çağırana. İş akışı yaklaşık 5-60 saniye arasında bellekte kalır ve iletiler geldiğinde toplu olarak aynı ana bilgisayardaki aynı örneğini iş akışının kaldırılması önce tüm iletileri işlemek için gönderilen iletiler kullanmak için büyük olasılıkla olduğu <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> için en iyi gecikme kaynakları İsraf etmeden elde edin.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Hizmet ana bilgisayarını yeniden deneme girişimleri arasındaki üstel geri alma aralığı iş akışı hizmeti örneğiyle kilitlemek reattempts ve dizisi sonunda çağırana özel durum geçirir. İş akışınızı kalırsa bellekte çok kısa bir süre (5 saniyeden daha az) veya bir Web grubu büyük ve başka bir ileti aynı ana bilgisayarına teslim edilmesini olasılığını çok yüksek değil, kullanın <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> en iyi gecikme süresi elde etmek için.  
  
 Örnek kilitli özel eylem özelliği aşağıdaki senaryoları destekler. Tüm senaryolarda, SqlWorkflowInstanceStore instanceLockedExceptionAction özelliği ayarlanmışsa <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> veya <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, örneklerinde kilidi düzenli aralıklarla almak için konak saydam olarak yeniden dener.  
  
1.  **Normal olarak kapatmak ve çakışan uygulama etki alanlarının geri dönüşüm etkinleştiriliyor.** Varsayalım bir **AppDomain** hizmet ana bilgisayarı ile hizmet örnekleri iş akışını çalıştıran geri dönüştürüldüğünde ve yeni bir yapılıyor **AppDomain** paralel eski sırasında yeni isteklerini işlemek için duruma  **AppDomain** düzgün biçimde getirilene. Kapatma iş akışı hizmeti örnekleri boşta kadar bekler ve ardından devam ederse ve örnekleri kaldırır. Yeni ana bilgisayar tarafından girişimlerini **AppDomain** örneği kilitlemek için neden olacak bir <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **Yatay dayanıklı iş akışları homojen bir sunucuları grubu arasında ölçeklendirme.** Bir iş akışı örneği kilitlenme çalıştığı bir sunucu grubu düğümünün varsayalım ve iş akışı ana çalıştığı örneğinde kilitleri kaldıramazsınız. Gruptaki başka bir düğüm üzerinde çalışan bir hizmet ana bilgisayarı, iş akışı örneği için bir ileti aldığında, onu alırsınız Bu örnekler kilit edinmeye çalışır <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Kilidi yenilemek için gereken ana bilgisayar artık mevcut olmadığından kilitler bir süre sonra dolacak.  
  
     **Yatay dayanıklı iş akışları homojen bir sunucuları grubu arasında ölçeklendirme.**  Yatay bir NLB (Ağ Yük Dengeleyici) arkasında birden çok ana bilgisayar kullanarak dayanıklı bir iş akışı ölçeklendirmek istediğiniz, gruptaki bir düğüm üzerinde çalışan iş akışı ana iş akışı örneği yükler ve bir ileti işleme ve sonraki iletiyi örneğine yönlendirilir varsayalım NLB ana bilgisayara iletileri sunmak için yönlendirme algoritmasını sahip olmadığından, başka bir düğüm üzerinde çalışan ana bilgisayarın, örneği zaten çalışıyor. İletiyi alır almaz, ikinci ana iş akışı örneğini yüklemeye çalışır ve alan <xref:System.Runtime.DurableInstancing.InstanceLockedException> ilk ana örnek üzerinde bir kilit olduğundan. İlk ana bilgisayar örneği ile ilk ileti işleme tamamlandı ve sonraki yeniden deneme sayısı, örnek yüklediğinde ve ikinci bir ileti işler ikinci ana bilgisayar kilit alır kilidini açar.
