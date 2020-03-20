---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184919"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Nasıl yapılır: IIS'de WCF Hizmeti Barındırma
Bu konu, Internet Bilgi Hizmetleri'nde (IIS) barındırılan bir Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımları özetlemektedir. Bu konu, IIS'ye aşina olduğunuzu ve IIS uygulamalarını oluşturmak ve yönetmek için IIS yönetim aracını nasıl kullanacağınızı bildiğinizi varsayar. IIS hakkında daha fazla bilgi için [Internet Bilgi Hizmetleri'ne](https://www.iis.net/)bakın. IIS ortamında çalışan bir WCF hizmeti, işlem geri dönüşümü, boşta kapatma, işlem durumu izleme ve ileti tabanlı etkinleştirme gibi IIS özelliklerinden tam olarak yararlanır. Bu barındırma seçeneği, IIS'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez. IIS barındırma yı yalnızca bir HTTP taşıma ile kullanabilirsiniz.  
  
 WCF ve ASP.NET etkileşimi hakkında daha fazla bilgi için [WCF Hizmetleri ve ASP.NET'](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)a bakın. Güvenliği yapılandırma hakkında daha fazla bilgi için [Güvenlik'e](../../../../docs/framework/wcf/feature-details/security.md)bakın.  
  
 Bu örneğin kaynak kopyası için, [Satır Satır Kodu Kullanarak IIS Hosting'e](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)bakın.  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS tarafından barındırılan bir hizmet oluşturmak için  
  
1. IIS'nin bilgisayarınızda yüklü ve çalıştığını doğrulayın. IIS'nin yüklenmesi ve yapılandırılması hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. "IISHostedCalcService" adlı uygulama dosyalarınız için yeni bir klasör oluşturun, ASP.NET klasörün içeriğine erişebilmesini sağlayın ve bu uygulama dizininde fiziksel olarak bulunan yeni bir IIS uygulaması oluşturmak için IIS yönetim aracını kullanın. Uygulama dizini için bir takma ad oluştururken "IISHostedCalc" kullanın.  
  
3. Uygulama dizininde "service.svc" adlı yeni bir dosya oluşturun. Aşağıdaki @ServiceHost öğeyi ekleyerek bu dosyayı düzenleme.  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Uygulama dizininde App_Code bir alt dizini oluşturun.  
  
5. App_Code alt dizininde Service.cs adlı bir kod dosyası oluşturun.  
  
6. Service.cs dosyasının üst bölümüne aşağıdaki ifadeleri kullanarak ekleyin.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Aşağıdaki ad alanı bildirimini kullanarak ifadelerden sonra ekleyin.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Ad alanı bildirimi içindeki hizmet sözleşmesini aşağıdaki kodda gösterildiği şekilde tanımlayın.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesi tanımından sonra hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Uygulama dizininde "Web.config" adlı bir dosya oluşturun ve dosyaya aşağıdaki yapılandırma kodunu ekleyin. Çalışma zamanında, WCF altyapısı istemci uygulamalarının iletişim kurabileceği bir bitiş noktası oluşturmak için bilgileri kullanır.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir. Hizmete herhangi bir uç nokta eklemezseniz, çalışma süresi sizin için varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için WCF Hizmetleri için [Basitleştirilmiş Yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)bakın.  
  
11. Hizmetin doğru şekilde barındırıldığından emin olmak için Internet Explorer'ın bir örneğini açın ve hizmetin URL'sine göz atın:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Örnek  
 Aşağıda, IIS barındırılan hesap makinesi hizmeti için kodun tam listesi veremivettir.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [WCF Hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
- [Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
