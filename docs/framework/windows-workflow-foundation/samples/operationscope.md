---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871143"
---
# <a name="operationscope"></a>OperationScope
Bu örnek gösterir nasıl etkinlikleri, Mesajlaşma <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> var olan bir özel etkinlik bir iş akışı hizmeti içinde bir işlem olarak kullanıma sunmak için kullanılabilir. Bu örnek adlı yeni bir özel etkinlik içeren bir `OperationScope`. Yazma işlemlerini ayrı ayrı, özel etkinlikler olarak gövdesi izin vererek ve ardından bunları kullanarak hizmet işlemleri kolayca gösterme tarafından bir iş akışı hizmet geliştirme kolaylığı için tasarlanmıştır `OperationScope` etkinlik. Örneğin, bir özel `Add` iki alan etkinlik `in` bağımsız değişkenleri ve döndürür bir `out` bağımsız değişken ortaya olarak bir `Add` içine bırakmadan tarafından iş akışı hizmeti işlemi bir `OperationScope`.  
  
 Kapsamı gövdesinde sağlanan etkinlik inceleyerek çalışır. Tüm sütunların `in` bağımsız değişkenleri girişlerin gelen iletisi olduğu varsayılır. Tüm `out` olup bağlandıktan, bağımsız olarak bağımsız değişkenler, varsayılır çıkışları sonraki yanıt iletisi. İfşa edilen işlem adı, görünen adından alınmış `OperationScope` etkinlik. Gövde etkinlik içine sarmalanır nihai sonucu olan bir <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> iletilerden bağlı etkinlik bağımsız değişkenleri parametrelere sahip.  
  
 Bu örnek, bir iş akışı hizmeti kullanarak HTTP uç noktalarını kullanıma sunar. Çalıştırmak için uygun URL'yi ACL'leri eklenmesi gerekir. Daha fazla bilgi için [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Yükseltilmiş bir isteminde aşağıdaki komutu yürütülürken uygun ACL'lerin ekler (kullanıcı adı ve etki alanı için etki alanı % başvurulduğunda olun\\% UserName %).  
  
 **Netsh http ekleme urlacl url =http://+:8000/ kullanıcı etki alanı % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  OperationScope.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüm Gezgini'nde çözüme sağ tıklatıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**. Senaryo ve Scenario_Client (bu sırayla) birden çok başlangıç projesi ekleyin.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
    > [!WARNING]
    >  Özel Etkinlik nedeniyle BankService.xaml iş akışını görüntülemek için bu adım gereklidir `OperationScope`.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın. Girdiler için ister Scenario_Client konsolunu ve karşılık gelen çıkış senaryo konsolda görülür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`