---
description: 'Hakkında daha fazla bilgi edinin: hizmet işlemi süresini belirleme'
title: Hizmet işlemi süresini belirleme
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: e9dd9ee4113ee4b4521afb6dfaf6a913e72ea5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798816"
---
# <a name="determining-service-operation-duration"></a>Hizmet işlemi süresini belirleme

Analitik izleme bir Windows Communication Foundation (WCF) uygulamasında etkinleştirilmişse, bir hizmet işlemi için yürütme süresi, olay günlüğü incelenerek kolayca belirlenebilir.  Bu konuda, bir hizmet işleminin tamamlanma süresini belirleme işlemi gösterilmektedir.  
  
### <a name="determining-service-operation-execution-duration"></a>Hizmet işlemi yürütme süresini belirleme  
  
1. **Başlat**, **çalıştır** ve girerek Olay Görüntüleyicisi açın `eventvwr.exe` .  
  
2. Analitik izlemeyi etkinleştirmediyseniz, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' ı genişletin. **Görünüm**, **analitik ve hata ayıklama günlüklerini göster**' i seçin. **Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin. İzlemelerin, hizmet işlemi çalıştırıldıktan sonra görüntülenebilmesi için Olay Görüntüleyicisi açık bırakın.  
  
3. Ardından, bir hizmet projesi ve bu hizmetle etkileşime sahip bir istemci projesi içeren bir WCF uygulaması açın.  [Kullanmaya başlama öğreticisini](../../getting-started-tutorial.md)izleyerek böyle bir uygulama oluşturabilirsiniz.  WCF örnekleri yüklüyse, öğreticide oluşturulan tamamlanmış projeyi içeren [Başlarken](../../samples/getting-started-sample.md)' i açabilirsiniz.  
  
4. **F5** tuşuna basarak sunucu uygulamasını yürütün. İstemci uygulamasını, **istemci** projesine sağ tıklayıp **Hata Ayıkla**, **Yeni örnek Başlat**' ı seçerek yürütün.  
  
5. Olay Görüntüleyicisi, analitik günlüğünü yenileyin ve olayları olay KIMLIĞINE göre sıralayın.  Olay KIMLIĞI 214 olan olayları ara [-OperationCompleted](214-operationcompleted.md).  Bu olaylar hangi işlemlerin tamamlandığını ve işlemin süresini gösterir.  Aşağıdaki olay bir ekleme işleminin süresini gösterir.  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
