---
title: İzleme kullanarak iş akışı yürütme süresini belirleme
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: 9f9c65f2c873d54da443db14e7f5797ef1e14174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515091"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>İzleme kullanarak iş akışı yürütme süresini belirleme
Bu konuda, iş akışı izleme kullanarak çalıştırmak başarıyla tamamlandı, kendi kendini barındıran bir iş akışı için geçen süreyi belirlemek gösterilmiştir.  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>İş akışı izleme kullanarak iş akışı uygulama yürütme süresini belirlemek için  
  
1.  Açık [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  Seçin **dosya**, **yeni**, **proje**.  Altında **C#** seçin **iş akışı** düğümü.  Seçin **iş akışı konsol uygulaması** şablonları listesinden.  Yeni proje adı `WorkflowDurationTracing` tıklatıp **Tamam**.  
  
2.  Workflow1.xaml açın.  Sürükleme bir <xref:System.Activities.Statements.Delay> Tasarımcı yüzeyine etkinlik. Değer 00:00:10 (on saniye) etkinlik süresi özelliğine atayın.  
  
3.  Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.  
  
4.  İş akışı izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** . Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **hata ayıklama** seçip **günlüğü etkinleştir**. Böylece iş akışını çalıştırmak sonra izleri görüntülenebilir Olay Görüntüleyicisi'ni kapatmayın.  
  
5.  CTRL + SHIFT + B tuşuna basarak iş akışı uygulaması yürütün.  
  
6.  Olay Görüntüleyicisi'nde yeni bir Olay Kimliği 1009 ve bir ileti aşağıdakine benzer bulun. İleti günlüğe kaydedildi süreyi not edin.  
  
 **Üst etkinlik '', DisplayName: '', InstanceId: '' zamanlanmış alt etkinlik 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', örnek kimliği: '1'.**  
  
7.  Başka bir son olay kimliği 1001 ve bir ileti aşağıdakine benzer bulun.  Önceki süresi yaklaşık 10 saniye olmalıdır iş akışı yürütme süresini belirlemek için bu ileti günlüğe değerinden çıkarın.  
  
 **İş akışı örneği kimliği: '1bbac57b-3322-498e-9e27-8833fda3a5bf' kapalı durumda tamamlandı.**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı İzleme](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
