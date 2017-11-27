---
title: "Bir WCF Hizmetini Yeniden Adlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ee707a898bf915491cc1ca44e0606c261dc87dc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma
Bu konu, nasıl adlandırabilirsiniz açıklar bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet.  
  
## <a name="renaming-a-wcf-service"></a>Bir WCF Hizmetini Yeniden Adlandırma  
 Bir hizmet olarak yeniden adlandırmak için aşağıdaki adımları izleyerek bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] şablonu  
  
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
