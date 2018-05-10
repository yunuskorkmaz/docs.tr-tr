---
title: Hizmet İşlemi Hatalarını İzleme
ms.date: 03/30/2017
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
ms.openlocfilehash: 3d708b537789c8d0decf75df780300c1e185c4c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="monitoring-service-operation-failures"></a>Hizmet İşlemi Hatalarını İzleme
Bir uygulama için çözümleme izleme etkinleştirilirse, Olay Görüntüleyicisi'nde hizmet hataları kolayca izlenebilir.  Bu konuda, bir hizmet işlemi başarısız olur ve belirlemek nasıl hatasına neden oldu belirleme gösterilir.  
  
### <a name="determining-service-operation-failure-information"></a>Hizmet işlemi hata bilgileri belirleme  
  
1.  Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.  
  
2.  Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** . Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **analitik** seçip **günlüğü etkinleştir**. Hizmet işlemi başarısız olduktan sonra izleri görüntülenebilir böylece Olay Görüntüleyicisi'ni kapatmayın.  
  
3.  Ardından, oluşturulan örnek açmak [başlangıç Öğreticisi](../../../../../docs/framework/wcf/getting-started-tutorial.md) içinde [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] çalıştırmalısınız Not [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] yönetici olarak böylece hizmet oluşturulabilir. Yüklü WCF örnekleri varsa açabilirsiniz [Başlarken](../../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.  
  
4.  Sunucu projesi Program.cs dosyasında aşağıdaki kod satırını başlangıcına ekleyin `Divide` yönteminde `CalculatorService` sınıfı:  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  İstemci projesindeki Program.cs dosyasında sıfır value2 atanan değer değiştirin:  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  Sunucu uygulaması tuşlarına basarak hata ayıklama olmadan yürütün **Ctrl + F5**.  
  
7.  Visual Studio komut istemi açın.  İstemci dizine gidin ve istemci komut satırından yürütün.  
  
8.  Olay Görüntüleyicisi'nde devre dışı bırakın ve analitik günlük yenileyin ve olayları olay kimliğine göre sıralama  Olay Kimliği sahip bir olay arayın [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), hizmet hatası açıklar.  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  Olayları için Olay Görüntüleyicisi'ni gönderilmekte olan zaman arabelleğe alınmış; Hata olayı hemen görüntülenmeyebilir.
