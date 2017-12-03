---
title: "İş akışı hizmetleri güvenli hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cd7620186ed51110a32e251d5239c85bb90e0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="securing-workflow-services"></a>İş akışı hizmetleri güvenli hale getirme
İş akışı hizmeti güvenli hale getirilmiş örnek aşağıdaki yordamları gösterir:  
  
-   Kullanarak bir temel iş akışı hizmeti oluşturma <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
-   Kullanarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iş akışı hizmeti tarafından kullanım için güvenli uç noktalarını tanımlamak için yapılandırma.  
  
-   Özel bir ilke içinde talep oluşturma ve kullanma <xref:System.ServiceModel.ServiceAuthorizationManager> doğrulamak için.  
  
## <a name="demonstrates"></a>Gösteriler  
 İş akışı hizmeti ile istemci arasındaki iletişimin güvenliğini sağlamak için WCF güvenlik kullanarak, talep tabanlı yetkilendirme  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek kullanımını gösteren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ile normal bir şekilde bir iş akışı hizmeti güvenli hale getirmek için güvenlik altyapısı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Özellikle, bir özel talep yetkilendirme için kullanır. Bu durumda, kullanan <xref:System.ServiceModel.WSHttpBinding> ve ileti mod güvenliği Windows kimlik bilgilerine sahip.  
  
 Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) istemcinin Windows kullanıcı adı denetler ve özel karakter. Bu karakteri varsa, oluşturur ve talep ekler <xref:System.IdentityModel.Policy.EvaluationContext>. Bunu yaparak, özel ilke deyimi, yapıyor istemci, kullanıcı bu karakter içeriyor. Bu talep çağrı ömrü sorgulanabilir. Bu karakteri bulabilirsiniz `Constants.cs`.  
  
 İçinde talep yetkilendirme ilkesi arar `SecureWorkFlowAuthZManager`. Bulduğu varsa, döndürür `true` ve devam etmek iş akışı izin verin. Aksi takdirde, döndürür `false`, istemciye döndürülecek bir 'Erişim engellendi' iletisi neden olur. Diğer talepleri bağlamda mevcut olduğundan ve de içinde incelenebilir `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Bu örneği çalıştırmak için  
  
1.  Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  İçinde SecuringWorkflowServices.sln yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
4.  Hizmet projesinin çözüm başlangıç projesi olarak ayarlayın.  
  
5.  Hata ayıklama olmadan hizmetini başlatmak için CTRL + F5 tuşuna basın.  
  
6.  İstemci projesi çözüm başlangıç projesi olarak ayarlayın.  
  
7.  İstemci hata ayıklama olmadan başlatmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
