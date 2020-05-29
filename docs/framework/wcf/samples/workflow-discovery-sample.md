---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1c6210472b594aec02bdf47f472a1a8b1823230c
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202068"
---
# <a name="workflow-discovery-sample"></a>İş Akışı Keşif Örneği
Bu örnek, bir iş akışı hizmetinin nasıl keşfedilebilir olduğunu ve belirli bir hizmeti arayan özel kod etkinliğinin nasıl yazıldığını gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Keşif bul etkinliği ve Iş akışı kullanımı  
  
## <a name="discussion"></a>Tartışma  
 Örneğin ilk bölümünde, yapılandırma kullanılarak bir iş akışı hizmeti bulunabilir hale getirilir. Yapılandırma ayrıca, hizmeti özel meta veriler (kapsamlar gibi) ile uygun şekilde uygulamak için de kullanılabilir. İstemcide, örnek, belirli bir sözleşmeyle eşleşen bir hizmeti aramak için bulma kullanan özel bir kod etkinliği kullanır. Kod etkinliği, daha sonra bir gönderme etkinliği tarafından kullanılan bir URI 'ye çıktı.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örnek, çalıştırmak için uygun URL ACL 'Leri olması gereken HTTP uç noktalarını kullanır (Ayrıntılar için bkz. [http ve https 'Yi yapılandırma](../feature-details/configuring-http-and-https.md) ). Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Kabuğunuz değişken biçimini anlamaz, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için değiştirin.  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
