---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: ad1fb7d289dea3396b4edb4d3b3e9fb7fb1891e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972415"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Nasıl yapılır: IIS'de WCF Hizmeti Barındırma
Bu konuda, Internet Information Services (IIS) içinde barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir. Bu konu, IIS 'yi bildiğiniz ve IIS yönetim aracını kullanarak IIS uygulamaları oluşturma ve yönetme hakkında bilgi sahibi olduğunuz varsayılmaktadır. IIS hakkında daha fazla bilgi için bkz. [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449). IIS ortamında çalışan bir WCF hizmeti, işlem geri dönüştürme, boşta kalma, işlem sistem durumu izleme ve ileti tabanlı etkinleştirme gibi IIS özelliklerinden tam olarak yararlanır. Bu barındırma seçeneği IIS 'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez. Yalnızca bir HTTP taşıması ile IIS barındırma kullanabilirsiniz.  
  
 WCF ve ASP.NET ile etkileşim kurma hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). Güvenliği yapılandırma hakkında daha fazla bilgi için bkz. [güvenlik](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Bu örneğin kaynak kopyası için bkz. [satır Içi kod kullanarak IIS barındırma](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS tarafından barındırılan bir hizmet oluşturmak için  
  
1. IIS 'nin bilgisayarınızda yüklü olduğundan ve çalıştığından emin olun. IIS yükleme ve yapılandırma hakkında daha fazla bilgi için bkz. [ııs 7,0 yükleme ve yapılandırma](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2. "IISHostedCalcService" adlı uygulama dosyalarınız için yeni bir klasör oluşturun, ASP.NET klasörünün içeriğine erişebildiğinden emin olun ve bu uygulama dizininde fiziksel olarak bulunan yeni bir IIS uygulaması oluşturmak için IIS Yönetim Aracı 'nı kullanın. Uygulama dizini için bir diğer ad oluştururken "IISHostedCalc" kullanın.  
  
3. Uygulama dizininde "Service. svc" adlı yeni bir dosya oluşturun. Aşağıdaki @ServiceHost öğeyi ekleyerek bu dosyayı düzenleyin.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Uygulama dizini içinde bir App_Code alt dizini oluşturun.  
  
5. Service.cs adlı bir kod dosyasını App_Code alt dizininde oluşturun.  
  
6. Aşağıdaki using deyimlerini Service.cs dosyasının en üstüne ekleyin.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Using deyimlerinden sonra aşağıdaki ad alanı bildirimini ekleyin.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Aşağıdaki kodda gösterildiği gibi, ad alanı bildiriminde hizmet sözleşmesini tanımlayın.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Hizmet sözleşmesini, aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi tanımından sonra uygulayın.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Uygulama dizininde "Web. config" adlı bir dosya oluşturun ve aşağıdaki yapılandırma kodunu dosyaya ekleyin. Çalışma zamanında, WCF altyapısı, istemci uygulamaların iletişim kurabildiği bir uç nokta oluşturmak için bu bilgileri kullanır.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir. Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
11. Hizmetin doğru şekilde barındırıldığından emin olmak için Internet Explorer 'ın bir örneğini açın ve hizmetin URL 'sine gidin:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Örnek  
 Aşağıda, IIS tarafından barındırılan Hesaplayıcı hizmeti için kodun tamamen bir listesi verilmiştir.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
