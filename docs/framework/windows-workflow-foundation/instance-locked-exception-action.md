---
description: 'Daha fazla bilgi edinin: örnek kilitli özel durum eylemi'
title: Örnek Kilitli Özel Durum Eylemi
ms.date: 03/30/2017
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
ms.openlocfilehash: ebbd86aad0f2e628f2656392fd464e3c1436c148
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792680"
---
# <a name="instance-locked-exception-action"></a>Örnek Kilitli Özel Durum Eylemi

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A>SQL Iş akışı örneği deposunun özelliği, SQL kalıcılık sağlayıcısı 'nın ne zaman alacağını belirtmenizi sağlar <xref:System.Runtime.DurableInstancing.InstanceLockedException> . Kalıcılık sağlayıcısı, şu anda başka bir hizmet ana bilgisayarı tarafından kilitlenen bir iş akışı hizmeti örneğini kilitlemeyi denediğinde bu özel durumu alır. Bu özelliğin değerleri <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> , ve ' dir <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> . <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> varsayılan değerdir. Aşağıdaki listede üç seçenek açıklanmaktadır:  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. Hizmet ana bilgisayarı, iş akışı hizmeti örneğini kilitlemeyi denemez ve ' <xref:System.Runtime.DurableInstancing.InstanceLockedException> ı çağırana geçirir.  İş akışınız 60 saniye aşan bir dönem için bellekte kalırsa <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> yeniden deneme olarak kullanın. <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> varsayılan değerdir.  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. Hizmet ana bilgisayarı, yeniden deneme girişimleri arasındaki doğrusal bir aralıkla iş akışı hizmeti örneğini kilitlemeye ve <xref:System.Runtime.DurableInstancing.InstanceLockedException> sıranın sonundaki çağırana geçirir. İş akışı yaklaşık olarak 5-60 saniye arasında bellekte kalırsa ve iletiler, iş akışını kaldırmadan önce tüm iletileri işlemek üzere aynı ana bilgisayardaki aynı örneğe gönderilen iletiler daha büyük olan toplu işlemlere ulaştığında, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> kaynakları beklemeden en iyi gecikme süresini elde etmek için kullanın.  
  
- <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Hizmet ana bilgisayarı, yeniden deneme girişimleri arasında bir üstel geri alma aralığı ile iş akışı hizmeti örneğini kilitleyip özel durumu sıranın sonunda çağırana geçirir. İş akışınız çok kısa bir süre (5 saniyeden az) için bellekte kalırsa veya bir Web grubu büyükse ve aynı konağa teslim edilen başka bir iletinin olasılığı çok yüksek ise, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> en iyi gecikme süresini elde etmek için kullanın.  
  
 Örnek kilitli özel durum eylemi özelliği aşağıdaki senaryoları destekler. Tüm senaryolarda, SqlWorkflowInstanceStore 'un InstanceLockedExceptionAction özelliği veya olarak ayarlandıysa <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> , ana bilgisayar, örnekleri her düzenli aralıklarla kilitlemeyi elde etmek için saydam olarak yeniden dener.  
  
1. **Düzgün kapanma ve uygulama etki alanlarının çakışan geri dönüşümü etkinleştiriliyor.** İş akışı hizmeti örnekleri çalıştıran bir hizmet ana bilgisayarı olan **AppDomain** 'in geri dönüştürülmekte olduğunu ve yeni bir **AppDomain** 'in, eski **AppDomain** 'in düzgün bir şekilde yeniden başlatılmasının paralel olarak yeni istekleri işlemek üzere kullanıldığını varsayalım. Kapalı, iş akışı hizmet örnekleri boşta olana kadar bekler ve örnekleri yeniden kaldırır. Yeni **AppDomain** içindeki konaklar tarafından bir örneği kilitlemek için herhangi bir girişim olur <xref:System.Runtime.DurableInstancing.InstanceLockedException> .  
  
2. **Kalıcı iş akışlarını bir sunucu grubu genelinde yatay olarak ölçeklendirin.** Bir iş akışı örneğinin çalıştırıldığı bir sunucu grubu düğümü olduğunu ve iş akışı ana bilgisayarının, çalıştırdığı örnekteki kilitleri kaldıramadığını varsayın. Grubun başka bir düğümünde çalışan bir hizmet ana bilgisayarı, bu iş akışı örneği için bir ileti aldığında, bu örneklerde elde edilen kilitleri almaya çalışır <xref:System.Runtime.DurableInstancing.InstanceLockedException> . Kilidi yenilemek için beklenen ana bilgisayar artık mevcut olmadığından kilitlerin süresi bir süre sonra dolacak.  
  
     **Kalıcı iş akışlarını bir sunucu grubu genelinde yatay olarak ölçeklendirin.**  Bir NLB 'nin (ağ Load Balancer) arkasında birden çok Konağı kullanarak dayanıklı bir iş akışını yatay olarak ölçeklendirmek istediğinizi varsayalım. grubun bir düğümünde çalışan iş akışı ana bilgisayarı bir iş akışı örneği yükler ve bir iletiyi işliyor ve NLB, örneği zaten çalıştıran konağa ileti teslim etmek için yönlendirme algoritmasına sahip olmadığından örneğe bir sonraki ileti başka bir düğümde çalışan konağa yönlendirilir. İleti alındıktan sonra ikinci ana bilgisayar, iş akışı örneğini yüklemeye çalışır ve <xref:System.Runtime.DurableInstancing.InstanceLockedException> ilk konağın örnek üzerinde bir kilidi olduğundan bunu alır. Birinci ana bilgisayar, ilk iletiyi işlemeye bittiğinde örneği kaldırır ve ikinci ana bilgisayar bir sonraki sefer yeniden denediğinde kilidi alır, örneği yükler ve ikinci iletiyi işler.
