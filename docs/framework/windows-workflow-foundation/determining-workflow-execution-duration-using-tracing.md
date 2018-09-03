---
title: İzleme kullanarak iş akışı yürütme süresini belirleme
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: c51fdf4543939fc068092b84e02eeb5f52e77d6d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486287"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>İzleme kullanarak iş akışı yürütme süresini belirleme
Bu konuda, iş akışı izleme kullanarak çalıştırmak başarıyla tamamlandı, şirket içinde barındırılan bir iş akışı için gereken süreyi belirlemek nasıl gösterir.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>İş akışı izleme kullanarak iş akışı uygulama yürütme süresini belirlemek için  
  
1.  Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Seçin **dosya**, **yeni**, **proje**.  Altında **C#** seçin **iş akışı** düğümü.  Seçin **iş akışı konsol uygulaması** şablonları listesinden.  Yeni proje adını `WorkflowDurationTracing` tıklatıp **Tamam**.  
  
2.  Workflow1.xaml açın.  Sürükleme bir <xref:System.Activities.Statements.Delay> Tasarımcı yüzeyine etkinlik. Değer 00:00:10 (on saniye) etkinlik süresi özelliğine atayın.  
  
3.  Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırma**, girerek `eventvwr.exe`.  
  
4.  İş akışı izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucu uygulamaları** . Seçin **görünümü**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **hata ayıklama** seçip **günlüğü etkinleştir**. Olay Görüntüleyicisi, böylece iş akışını çalıştırdığınızda, izlemeleri görüntülenebilir açık bırakın.  
  
5.  İş akışı uygulaması, CTRL + SHIFT + B tuşlarına basarak çalıştırın.  
  
6.  Olay Görüntüleyicisi'nde yeni bir Olay Kimliği 1009 ve bir ileti aşağıdakine benzer bulun. İleti günlüğe kaydedildi süreyi not edin.  
  
 **Üst etkinlik '', DisplayName: '', InstanceId: '' zamanlanmış alt etkinlik 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**  
  
7.  Başka bir son olay kimliği 1001 ve bir ileti aşağıdakine benzer bulun.  Önceki ileti süresi yaklaşık 10 saniye olmalıdır iş akışı yürütme süresini belirlemek için bu ileti günlüğe değerinden çıkarır.  
  
 **WorkflowInstance ID: kapalı durumda '1bbac57b-3322-498e-9e27-8833fda3a5bf' tamamlandı.**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı İzleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
