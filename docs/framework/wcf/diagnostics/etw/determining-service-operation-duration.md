---
title: Hizmet işlemi süresini belirleme
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: fd7dec5784f50a0613b574822a31202a859b34c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299039"
---
# <a name="determining-service-operation-duration"></a>Hizmet işlemi süresini belirleme
Bir Windows Communication Foundation (WCF) uygulamasında çözümleme izleme etkinleştirilirse, bir hizmet işlemi için yürütme süresini olay günlüğünü inceleyerek kolayca belirlenebilir.  Bu konuda, bir hizmet işlemi tamamlamak için gereken süreyi belirlemek nasıl gösterir.  
  
### <a name="determining-service-operation-execution-duration"></a>Hizmet işlemi yürütme süresini belirleme  
  
1. Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırma**, girerek `eventvwr.exe`.  
  
2. Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucu uygulamaları** . Seçin **görünümü**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **analitik** seçip **günlüğü etkinleştir**. Hizmet işlemi çalıştırıldıktan sonra izlemeleri görüntülenebilir, böylece Olay Görüntüleyicisi'ni açık bırakın.  
  
3. Ardından, bir hizmet projesi ve hizmetle etkileşime giren istemci projesi içeren bir WCF uygulamasını açın.  İzleyerek bu tür bir uygulama oluşturabilirsiniz [başlangıç Öğreticisi](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Yüklü WCF örnekleri varsa açabileceğiniz [Başlarken](../../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.  
  
4. Sunucu uygulaması tuşlarına basarak yürütme **F5**. İstemci uygulamayı sağ tıklayarak yürütme **istemci** proje ve seçerek **hata ayıklama**, **yeni örnek Başlat**.  
  
5. Olay Görüntüleyicisi ' nde, analitik günlüğü yenileyin ve olayları olay kimliğine göre sırala  Olay Kimliği ile olayları arayın [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Bu olaylar, hangi işlemleri tamamladıktan ve işlem süresince neydi gösterilir.  Aşağıdaki olay süresi bir ekleme işlemi gösterilmektedir.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
