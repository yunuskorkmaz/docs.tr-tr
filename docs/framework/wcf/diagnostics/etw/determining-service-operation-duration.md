---
title: Hizmet işlemi süresini belirleme
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 8c86ccc09979071e0678be792f4937d526e23fa7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804969"
---
# <a name="determining-service-operation-duration"></a>Hizmet işlemi süresini belirleme
Bir Windows Communication Foundation (WCF) uygulamasında çözümleme izleme etkinleştirilirse, yürütme süresi bir hizmet işlemi için olay günlüğünü inceleyerek kolayca belirlenebilir.  Bu konuda, bir hizmet işlemi tamamlamak için geçen süreyi belirlemek gösterilmiştir.  
  
### <a name="determining-service-operation-execution-duration"></a>Hizmet işlemi yürütme süresini belirleme  
  
1.  Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.  
  
2.  Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** . Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **analitik** seçip **günlüğü etkinleştir**. Hizmet işlemini çalıştırdıktan sonra izlemeleri görüntülenebilir böylece Olay Görüntüleyicisi'ni kapatmayın.  
  
3.  Ardından, bir hizmet projesi ve bu hizmeti ile etkileşime giren istemci proje içeren bir WCF uygulamasını açın.  İzleyerek böyle bir uygulama oluşturabilirsiniz [başlangıç Öğreticisi](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Yüklü WCF örnekleri varsa açabilirsiniz [Başlarken](../../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.  
  
4.  Sunucu uygulaması tuşlarına basarak yürütme **F5**. Üzerinde sağ tıklayarak ve istemci uygulamanın yürütme **istemci** proje ve seçerek **hata ayıklama**, **Başlat yeni örnek**.  
  
5.  Olay Görüntüleyicisi'nde analitik günlüğünü yenilemek ve olayları olay kimliğine göre sıralama  Olay kimliği olan olaylar için Ara [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Bu olaylar, hangi işlemleri tamamladınız ve işlem süresini neydi gösterir.  Aşağıdaki olay bir ekleme işlemi süresini gösterir.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
