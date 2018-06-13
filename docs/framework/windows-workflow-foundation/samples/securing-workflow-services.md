---
title: İş akışı hizmetleri güvenli hale getirme
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 5dbd724f3a2f8febfc74719584f4d69cbf75b567
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806675"
---
# <a name="securing-workflow-services"></a>İş akışı hizmetleri güvenli hale getirme
İş akışı hizmeti güvenli hale getirilmiş örnek aşağıdaki yordamları gösterir:  
  
-   Kullanarak bir temel iş akışı hizmeti oluşturma <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
-   Windows Communication Foundation (WCF) yapılandırma iş akışı hizmeti tarafından kullanım için güvenli uç noktalarını tanımlamak için kullanma.  
  
-   Özel bir ilke içinde talep oluşturma ve kullanma <xref:System.ServiceModel.ServiceAuthorizationManager> doğrulamak için.  
  
## <a name="demonstrates"></a>Gösteriler  
 İş akışı hizmeti ile istemci arasındaki iletişimin güvenliğini sağlamak için WCF güvenlik kullanarak, talep tabanlı yetkilendirme  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek ile normal bir WCF hizmeti gibi bir iş akışı hizmeti güvenli hale getirmek için WCF güvenlik altyapısı kullanımını göstermektedir. Özellikle, bir özel talep yetkilendirme için kullanır. Bu durumda, kullanan <xref:System.ServiceModel.WSHttpBinding> ve ileti mod güvenliği Windows kimlik bilgilerine sahip.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
