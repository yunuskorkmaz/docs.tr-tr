---
description: 'Hakkında daha fazla bilgi edinin: barındırma Iş akışı hizmetleri genel bakış'
title: İş Akışı Hizmetlerini Barındırma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: e183dfd7428c11cf20e731ab4a9975a7388b6f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743089"
---
# <a name="hosting-workflow-services-overview"></a>İş Akışı Hizmetlerini Barındırma Genel Bakış

İş akışı hizmetlerinin yürütülmesi için barındırılması gerekir. , <xref:System.ServiceModel.WorkflowServiceHost> Birden çok örneği, yapılandırmayı ve WCF iletilerini destekleyen, kullanıma hazır olan iş akışı ana bilgisayarı olur (ancak iş akışlarının barındırılmak için mesajlaşma kullanması gerekmez).  Ayrıca, bir dizi hizmet davranışı aracılığıyla Kalıcılık, izleme ve örnek denetimiyle tümleştirilir.  WCF 'nin de olduğu gibi, <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> IIS/was içinde herhangi bir yönetilen .NET uygulamasında veya Web 'de barındırılan (bir. xamlx dosyası olarak) şirket içinde barınabilir.  Bu bölümdeki konular, bir iş akışı hizmetinin nasıl barındıralınacağını açıklamaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [İş Akışı Hizmetlerini Barındırma](hosting-workflow-services.md)  
 Barındırma iş akışı hizmetlerini açıklar.  
  
 [İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri](workflow-service-host-internals.md)  
 <xref:System.ServiceModel.WorkflowServiceHost>Gelen iletileri işleme biçimini açıklar.  
  
 [İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği](workflow-service-host-extensibility.md)  
 İş akışı hizmeti Konağı işlevinin nasıl genişletileceğini açıklar.  
  
 [İş Akışı Denetim Uç Noktası](workflow-control-endpoint.md)  
 İş akışı örnekleri oluşturmanıza izin veren bir uç noktanın nasıl tanımlanacağını açıklar.
  
 [Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 Windows Server App Fabric 'te mevcut bir iş akışı hizmetinin nasıl barındırılacağını gösterir.  
  
 [WorkflowServiceHost Yapılandırma](configuring-workflowservicehost.md)  
 Kalıcılık, izleme, boşta ve işlenmemiş özel durum davranışının nasıl kontrol edileceğini açıklar.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [İş Akışı Hizmetleri](workflow-services.md)
