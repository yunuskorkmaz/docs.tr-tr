---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143492"
---
# <a name="workflow-discovery-sample"></a>İş Akışı Keşif Örneği
Bu örnek, bir iş akışı hizmetinin nasıl keşfedilebilir hale getirilebildiğini ve belirli bir hizmeti arayan özel bir kod etkinliğinin nasıl yazılabildiğini gösterir.  
  
## <a name="demonstrates"></a>Gösteriler  
 Bulma Bulma Etkinliği ve İş Akışı Kullanımı  
  
## <a name="discussion"></a>Tartışma  
 Örneğin ilk bölümünde, bir iş akışı hizmeti yapılandırma kullanılarak keşfedilebilir hale getirilir. Yapılandırma, hizmeti özel meta verilerle (kapsamlar gibi) uygun şekilde uygulamak için de kullanılabilir. İstemci de, örnek belirli bir sözleşme eşleşen bir hizmet aramak için Discovery kullanan özel bir kod etkinliği kullanır. Kod etkinliği, daha sonra bir gönderme etkinliği tarafından kullanılan bir URI çıktırıyor.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Bu örnek, çalıştırmak için uygun URL ALA'larına sahip olması gereken HTTP uç noktalarını kullanır (ayrıntılar için [HTTP ve HTTPS'yi yapılandırmaya](../feature-details/configuring-http-and-https.md) bakın). Aşağıdaki komutu yükseltilmiş bir komut isteminde yürütme uygun ALA'ları eklemelisiniz. Kabuğunuz değişken biçimini anlamıyorsa, Etki Alanı nızı ve Kullanıcı Adınızı aşağıdaki bağımsız değişkenler için değiştirin.  
  
     **netsh http urlaclhttp://+:8000/ url ekle=\\kullanıcı=%DOMAIN% %UserName%**  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
