---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498993"
---
# <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma
Bu konu, Windows Communication Foundation (WCF) hizmetini nasıl yeniden adlandırabilirsiniz açıklar.  
  
## <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma  
 Bir Windows Communication Foundation (WCF) şablonu hizmetinde yeniden adlandırmak için aşağıdaki adımları gerçekleştirin,  
  
-   Hizmet uygulayan sınıf adını değiştirin.  
  
-   Hizmet yapılandırma dosyasında hizmetin adı aşağıdaki örnekte gösterildiği gibi seçtiğiniz yeni bir adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Hizmetinizi webhosted ise, bir *.svc dosyası kullanır. Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmet adını değiştirin. Svc dosya olduğundan bu adımı kendini barındıran uygulamalar için gerekli değildir.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>WCF hizmet sözleşmesini yeniden adlandırma  
  
-   Hizmet sözleşmesi yeniden adlandırmak için aşağıdaki adımları gerçekleştirin,  
  
-   Hizmet sözleşmesi adını değiştirin.  
  
-   Hizmet yapılandırma dosyasında aşağıdaki örnekte gösterildiği gibi hizmet sözleşmesi adı seçtiğiniz yeni bir adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config veya web.config dosyası olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
