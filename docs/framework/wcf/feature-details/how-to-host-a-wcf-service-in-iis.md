---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4fb3957543d6a0fcf3b375f9cb43ae089ac9d600
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Nasıl yapılır: IIS'de WCF Hizmeti Barındırma
Bu konu oluşturmak için gereken temel adımlarda özetler bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Internet Information Services (IIS) barındırılan hizmet. Bu konu, IIS ile bilgi sahibiyseniz ve IIS uygulamaları oluşturmak ve yönetmek için IIS Yönetim Aracı'nı kullanmayı öğrenme varsayar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS bkz [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449). A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] IIS ortamında çalışan bir hizmete işlem geri dönüştürme, boşta kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme gibi IIS özellikleri tüm avantajlarından yararlanır. Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kod uygulamanın bir parçası yazılması gerektirmez. IIS ile yalnızca bir HTTP aktarma barındırma kullanabilirsiniz.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] etkileşim kurmak için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: güvenlik, yapılandırma [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Bu örnekte kaynak kopyası için bkz: [IIS barındırma kullanarak satır içi kod](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS tarafından barındırılan bir hizmet oluşturmak için  
  
1.  IIS yüklü ve bilgisayarınızda çalışır durumda olduğunu doğrulayın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS yükleniyor ve yapılandırılıyor bkz [yükleme ve IIS 7.0 yapılandırma](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Uygulama dosyalarınızın "IISHostedCalcService" adlı yeni bir klasör oluşturun, emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klasörünün içeriğini erişimi vardır ve bu uygulamada fiziksel olarak bulunan yeni bir IIS uygulama oluşturmak için IIS Yönetim Aracı'nı kullanın Dizin. Uygulama dizini kullanımı "IISHostedCalc" için bir diğer ad oluştururken.  
  
3.  Uygulama dizinindeki "service.svc" adlı yeni bir dosya oluşturun. Aşağıdakileri ekleyerek bu dosyayı düzenlemek @ServiceHost öğesi.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Uygulama dizininin içinde bir App_Code dizin oluşturun.  
  
5.  App_Code alt dizinindeki adını da adlı bir kod dosyası oluşturun.  
  
6.  Aşağıdaki using deyimlerini adını da dosyanın en üstüne ekleyin.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Kullandıktan sonra aşağıdaki ad alanı bildirimi ekleyin deyimleri.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Aşağıdaki kodda gösterildiği gibi ad alanı bildiriminin içinde hizmet sözleşmesini tanımlama.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Hizmet sözleşme sonra tanımı aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulama.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve aşağıdaki yapılandırma kodunu dosyasına ekleyin. Çalışma zamanında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı istemci uygulamaları ile iletişim kurabilen bir uç nokta oluşturmak için bilgileri kullanır.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Bu örnek, yapılandırma dosyasında uç noktalar açıkça belirtir. Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Varsayılan uç noktaları, bağlamaları ve davranışları bakın [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Hizmet doğru şekilde barındırılan emin olmak için Internet Explorer ve hizmetin URL'ye örneği açın:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Örnek  
 Barındırılan hesaplayıcı hizmetin IIS kodunu tam listesi verilmiştir.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services'te barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
