---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 207010f594959708322aed2e630935252c873cf8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466177"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Nasıl yapılır: IIS'de WCF Hizmeti Barındırma
Bu konuda, Internet Information Services (IIS) barındırılan Windows Communication Foundation (WCF) hizmet oluşturmak için gerekli temel adımlar açıklanmaktadır. Bu konuda, IIS ile ilgili bilgi sahibi olduğunuz ve IIS uygulamaları oluşturmak ve yönetmek için IIS Yönetim Aracı'nı kullanmayı öğrenmenize varsayılır. IIS hakkında daha fazla bilgi için bkz. [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449). Bir WCF Hizmeti IIS ortamında çalışır gibi işlem geri dönüştürme, IIS özellikleri tüm avantajlarından yararlanır, kapatma, sistem durumu izleme işlemi ve ileti tabanlı etkinleştirme boş. Bu barındırma seçeneği IIS düzgün şekilde yapılandırılmasını gerektirir, ancak uygulamanın bir parçası herhangi bir barındırma kod yazılmasını gerektirmez. Yalnızca bir HTTP aktarımı ile IIS barındırma kullanabilirsiniz.  
  
 Hakkında daha fazla bilgi için WCF ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] etkileşim kurmak için bkz: [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Güvenlik yapılandırma hakkında daha fazla bilgi için bkz. [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Bu örnekte kaynak kopyası için bkz: [IIS kullanarak satır içi kod barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS tarafından barındırılan bir hizmet oluşturmak için  
  
1.  IIS yüklü ve bilgisayarınızda çalışmakta olduğunu doğrulayın. Yükleme ve IIS yapılandırma hakkında daha fazla bilgi için bkz: [yükleme ve IIS 7.0 yapılandırma](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  "IISHostedCalcService" adlı uygulama dosyalarınızı için yeni bir klasör oluşturun, emin [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klasörünün içeriğini erişimi vardır ve bu uygulamada bulunan fiziksel olarak yeni bir IIS uygulama oluşturmak için IIS Yönetim Aracı'nı kullanın Dizin. Uygulamanın directory kullan "IISHostedCalc" için bir diğer ad oluştururken.  
  
3.  Uygulama dizininde, "service.svc" adlı yeni bir dosya oluşturun. Aşağıdakileri ekleyerek bu dosyayı Düzenle @ServiceHost öğesi.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Uygulama dizininin içinde bir App_Code dizin oluşturun.  
  
5.  App_Code alt dizinde adını da adlı bir kod dosyası oluşturun.  
  
6.  Aşağıdaki using deyimlerini adını da dosyasının en üstüne.  
  
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
  
8.  Aşağıdaki kodda gösterildiği gibi ad alanı bildirimi içinde hizmet sözleşmesini tanımlamaktır.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Hizmet sözleşme sonra tanımı aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulama.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve aşağıdaki kodu yapılandırma dosyasına ekleyin. Çalışma zamanında, WCF altyapısı, istemci uygulamaları ile iletişim kurabilen bir uç nokta oluşturmak için bilgileri kullanır.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Bu örnek, uç noktaları yapılandırma dosyasında açıkça belirtir. Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler. Varsayılan uç noktaları, bağlamalar ve davranışları bakın hakkında daha fazla bilgi için [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Hizmet doğru şekilde barındırılan emin olmak için Internet Explorer ve hizmetin URL'ye Gözat örneğini açın: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Örnek  
 Barındırılan hesaplayıcı hizmeti IIS için kod tam listesi verilmiştir.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)  
 [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
