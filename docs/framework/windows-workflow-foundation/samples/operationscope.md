---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: bca5a32e25537aea8c8fad7b80eb296d66fadf77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515791"
---
# <a name="operationscope"></a>OperationScope
Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri, <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> var olan bir özel etkinlik bir iş akışı hizmetinde bir işlem olarak kullanıma sunmak için kullanılabilir. Bu örnek olarak adlandırılan yeni bir özel etkinlik içeren bir `OperationScope`. Kullanıcıların kendi işlemleri ayrı olarak özel etkinlikler olarak gövdesi Yazar izin vermek ve ardından bunları kullanarak hizmet işlemleri kolayca gösterme tarafından bir iş akışı hizmeti geliştirmeyi kolaylaştırmak için tasarlanmıştır `OperationScope` etkinlik. Örneğin, bir özel `Add` iki alan etkinlik `in` bağımsız değişkenleri ve döndürür bir `out` bağımsız değişkeni ortaya olarak bir `Add` içine bırakmadan tarafından iş akışı hizmeti işlemi bir `OperationScope`.  
  
 Kapsam, kendi gövdesi olarak sağlanan etkinlik inceleyerek çalışır. Herhangi bir ilişkisiz `in` bağımsız değişkenleri varsayılır girişleri gelen iletisi. Tüm `out` olup bağlandıktan, bağımsız olarak bağımsız değişkenler, varsayılır çıkışları sonraki yanıt iletisi. Sunulan işlemin adı görünen adından alınan `OperationScope` etkinlik. Gövde etkinlik olarak paketlenir nihai sonucu olan bir <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> bağlı etkinlik bağımsız değişkenler için iletilerden parametrelere sahip.  
  
 Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar. Çalıştırmak için doğru URL ACL eklenmesi gerekir. Daha fazla bilgi için bkz: [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütülürken ekler uygun ACL'ler (kullanıcı adı ve etki alanı için etki alanı % yerine olun\\% UserName %).  
  
 **Netsh http add urlacl url =http://+:8000/ kullanıcı etki alanı % =\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  OperationScope.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Çözüm Gezgini'ndeki çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**. Senaryo ve Scenario_Client (sırayla) birden fazla başlangıç projesi ekleyin.  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
    > [!WARNING]
    >  Özel Etkinlik nedeniyle BankService.xaml iş akışı görüntülemek için bu adım gereklidir `OperationScope`.  
  
4.  Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın. Scenario_Client konsol girdileri ister ve karşılık gelen çıktı senaryo konsolunda görülür.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`