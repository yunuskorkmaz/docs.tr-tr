---
title: Bir WCF Hizmetini Yeniden Adlandırma
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052058"
---
# <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma
Bu konu, bir Windows Communication Foundation (WCF) hizmetini nasıl yeniden adlandırabileceğinizi açıklamaktadır.  
  
## <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma  
 Bir Windows Communication Foundation (WCF) şablonunda bir hizmeti yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.  
  
- Hizmeti uygulayan sınıfın adını değiştirin.  
  
- Hizmetin yapılandırma dosyasında, aşağıdaki örnekte gösterildiği gibi hizmetin adını seçtiğiniz yeni adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Hizmetiniz Web 'de barındırılıyorsa, bir * \* . svc* dosyası kullanır. Svc dosyasını açın ve aşağıdaki örnekte gösterildiği gibi hizmetinizin adını değiştirin. Bu adım, bir svc dosyası olmadığından, kendi kendine barındırılan uygulamalar için gerekli değildir.  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>WCF hizmet sözleşmesini yeniden adlandırma  
  
- Hizmet sözleşmesini yeniden adlandırmak için aşağıdaki adımları gerçekleştirin.  
  
- Hizmet sözleşmesinin adını değiştirin.  
  
- Hizmetin yapılandırma dosyasında, hizmet sözleşmesinin adını, aşağıdaki örnekte gösterildiği gibi, seçtiğiniz yeni adla değiştirin. Yapılandırma dosyası, barındırma modelinize bağlı olarak app.config ya da web.config dosya olabilir.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
