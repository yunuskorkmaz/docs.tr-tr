---
title: İş akışı hizmetlerinin güvenliğini sağlama
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 28c34ecf7d6d781bfa461b2737cb9325a657f47e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524341"
---
# <a name="securing-workflow-services"></a>İş akışı hizmetlerinin güvenliğini sağlama
Aşağıdaki yordamlar güvenli iş akışı hizmeti örnek gösterilmektedir:  
  
-   Temel iş akışı kullanarak hizmet oluşturma <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
-   Windows Communication Foundation (WCF) yapılandırması iş akışı hizmeti tarafından kullanım için güvenli uç noktaları tanımlamak için kullanıyor.  
  
-   Özel bir ilke içinde talep oluşturma ve kullanma <xref:System.ServiceModel.ServiceAuthorizationManager> doğrulamak için.  
  
## <a name="demonstrates"></a>Gösteriler  
 WCF güvenliğinde, iş akışı hizmeti ile istemci arasındaki iletişimin güvenliğini sağlamak için kullanarak, talep tabanlı yetkilendirme  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, normal bir WCF Hizmeti ile olduğu gibi bir iş akışı hizmeti güvenli hale getirmek için WCF güvenlik altyapısı kullanımını gösterir. Özellikle, bir özel talep yetkilendirme için kullanır. Bu durumda, kullandığı <xref:System.ServiceModel.WSHttpBinding> iletisi mod güvenliği Windows kimlik bilgilerine sahip.  
  
 Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) istemcinin Windows kullanıcı adı denetler ve belirli bir karakter. Bu karakteri mevcutsa oluşturur ve talep ekler <xref:System.IdentityModel.Policy.EvaluationContext>. Bunu yaparak, özel bir ilke ifadesi, yapıyor istemcinin kullanıcı adını bu karakteri sahip. Bu talep çağrısı kullanım ömrü boyunca sorgulanabilir. Bu karakterin bulabilirsiniz `Constants.cs`.  
  
 İçinde talep yetkilendirme ilkesi arar `SecureWorkFlowAuthZManager`. Bunu bulursa, onu döndürür `true` ve devam etmek iş akışı sağlar. Aksi halde `false`, istemciye döndürülecek 'Erişim engellendi' iletisi neden olur. Diğer talepler bağlamında mevcut olduğundan ve de içinde incelenebilir `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  İçinde SecuringWorkflowServices.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
4.  Hizmet projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
5.  Hata ayıklama olmadan hizmeti başlatmak için CTRL + F5 tuşlarına basın.  
  
6.  İstemci projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
7.  Hata ayıklama olmadan istemcisini başlatmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
