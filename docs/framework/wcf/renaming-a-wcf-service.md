---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8cb86621972423f55bfa18c60c1d4eb60cacb205
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651053"
---
# <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma
Bu konuda, bir Windows Communication Foundation (WCF) hizmeti nasıl yeniden adlandırabilirsiniz açıklanmaktadır.  
  
## <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma  
 Bir Windows Communication Foundation (WCF) şablonu hizmetinde yeniden adlandırmak için aşağıdaki adımları uygulayın,  
  
- Hizmet uygulayan sınıfın adını değiştirin.  
  
- Hizmet yapılandırma dosyasında hizmetin adı aşağıdaki örnekte gösterildiği gibi seçtiğiniz yeni bir adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Hizmetinizi webhosted ise, *.svc dosyası kullanır. Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmetin adını değiştirin. Svc dosya olduğundan bu adım şirket içinde barındırılan uygulamalar için gerekli değildir.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Bir WCF hizmet sözleşmesini yeniden adlandırma  
  
- Hizmet sözleşmesi yeniden adlandırmak için aşağıdaki adımları uygulayın,  
  
- Hizmet sözleşmesi adını değiştirin.  
  
- Hizmet yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi hizmet sözleşmesi adı seçmiş olduğunuz yeni bir adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
