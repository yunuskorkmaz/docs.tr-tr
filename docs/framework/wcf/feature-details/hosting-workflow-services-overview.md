---
title: "İş Akışı Hizmetlerini Barındırma Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2c38cd352eb860982b9b1e3aa32daa7aeeee9ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-workflow-services-overview"></a>İş Akışı Hizmetlerini Barındırma Genel Bakış
İş akışı hizmetleri yürütmek için barındırılması gerekir. <xref:System.ServiceModel.WorkflowServiceHost> (İş akışları barındırılması için Mesajlaşma kullanmak için gerekli olmasa da) destekleyen birden çok örneği, yapılandırma ve WCF ileti Giden kutusu iş akışı ana bilgisayardır.  Ayrıca Kalıcılık, izleme ve bir dizi hizmet davranışları örneği denetimi ile tümleştirilir.  WCF'ın ' olduğu gibi <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> herhangi bir yönetilen .NET uygulamasında kendi kendini barındıran veya web (.xamlx dosyası olarak) IIS'de barındırılan / OLUŞTU.  Bu bölümdeki konular, bir iş akışı hizmeti barındırma açıklar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İş akışı hizmetlerini barındırma](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 İş akışı hizmetlerini barındırma açıklar.  
  
 [İş akışı hizmeti konağı dahili bileşenleri](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 Açıklar nasıl <xref:System.ServiceModel.WorkflowServiceHost> gelen iletileri işler.  
  
 [İş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 İş akışı hizmeti ana bilgisayarı işlevselliğini genişletmek açıklar.  
  
 [İş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 İş akışı örnekleri oluşturmanıza olanak tanıyan bir uç nokta tanımlanacağını açıklar.  
  
 [Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 Bir iş akışı hizmeti IIS olmayan bir iş akışı barındırma gösterir.  
  
 [Nasıl yapılır: Windows Server App Fabric ile iş akışı hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Windows Server App Fabric var olan bir iş akışı hizmetinde barındırmak gösterilmiştir.  
  
 [WorkflowServiceHost yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 Kalıcılık, izleme, boşta ve işlenmeyen özel durum davranışını denetlemek açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [İş akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
