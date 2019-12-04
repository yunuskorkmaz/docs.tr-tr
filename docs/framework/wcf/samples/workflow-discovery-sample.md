---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b503e6231741fb049dbd8e9fdaae73c127ceaa51
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714989"
---
# <a name="workflow-discovery-sample"></a>İş Akışı Keşif Örneği
Bu örnek, bir iş akışı hizmetinin nasıl keşfedilebilir olduğunu ve belirli bir hizmeti arayan özel kod etkinliğinin nasıl yazıldığını gösterir.  
  
## <a name="demonstrates"></a>Gösterir  
 Keşif bul etkinliği ve Iş akışı kullanımı  
  
## <a name="discussion"></a>Tartışma  
 Örneğin ilk bölümünde, yapılandırma kullanılarak bir iş akışı hizmeti bulunabilir hale getirilir. Yapılandırma ayrıca, hizmeti özel meta veriler (kapsamlar gibi) ile uygun şekilde uygulamak için de kullanılabilir. İstemcide, örnek, belirli bir sözleşmeyle eşleşen bir hizmeti aramak için bulma kullanan özel bir kod etkinliği kullanır. Kod etkinliği, daha sonra bir gönderme etkinliği tarafından kullanılan bir URI 'ye çıktı.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, çalıştırmak için uygun URL ACL 'Leri olması gereken HTTP uç noktalarını kullanır (Ayrıntılar için bkz. [http ve https 'Yi yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353) ). Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Kabuğunuz değişken biçimini anlamaz, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için değiştirin.  
  
     **netsh http Add urlacl URL =http://+:8000/ Kullanıcı =% ETKIALANı%\\ % UserName%**  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
