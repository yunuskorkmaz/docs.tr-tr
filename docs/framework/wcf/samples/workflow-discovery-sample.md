---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964429"
---
# <a name="workflow-discovery-sample"></a>İş Akışı Keşif Örneği
Bu örnek, bir iş akışı hizmeti bulunabilir hale getirme ve belirli bir hizmet için arayan bir özel kod etkinliği yazmak nasıl gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif bulma etkinliği ve iş akışı kullanımı  
  
## <a name="discussion"></a>Tartışma  
 İlk bölümünde örnek bir iş akışı hizmeti bulunabilirlik yapılan yapılandırma kullanarak. Yapılandırma özel meta verileri (örneğin, kapsam) hizmetiyle uygun şekilde uygulamak için de kullanılabilir. İstemcide, örnek bulma aramak için belirli bir sözleşme eşleşen bir hizmetini kullanan bir özel kod etkinliği kullanır. Kod etkinliği, daha sonra bir gönderme etkinlik tarafından kullanılan bir URI çıkarır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Bu örneği çalıştırmak için doğru URL ACL olmalıdır HTTP uç noktaları kullanır (bkz [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için). Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütülürken uygun ACL'lerin eklemeniz gerekir. Kabuğunuz değişken biçimi anlamıyorsa şu bağımsız değişkenler için kullanıcı adı ve etki alanı değiştirin.  
  
     **Netsh http ekleme urlacl url =http://+:8000/ kullanıcı etki alanı % =\\% UserName %**  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
