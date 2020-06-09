---
title: "Nasıl yapılır: IIS'de WCF Hizmeti Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 326a270c4af38738c910828acd483070ab02ecd1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593093"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Nasıl yapılır: IIS'de WCF Hizmeti Barındırma
Bu konuda, Internet Information Services (IIS) içinde barındırılan Windows Communication Foundation (WCF) hizmeti oluşturmak için gereken temel adımlar özetlenmektedir. Bu konu, IIS 'yi bildiğiniz ve IIS yönetim aracını kullanarak IIS uygulamaları oluşturma ve yönetme hakkında bilgi sahibi olduğunuz varsayılmaktadır. IIS hakkında daha fazla bilgi için bkz. [Internet Information Services](https://www.iis.net/). IIS ortamında çalışan bir WCF hizmeti, işlem geri dönüştürme, boşta kalma, işlem sistem durumu izleme ve ileti tabanlı etkinleştirme gibi IIS özelliklerinden tam olarak yararlanır. Bu barındırma seçeneği IIS 'nin düzgün şekilde yapılandırılmasını gerektirir, ancak herhangi bir barındırma kodunun uygulamanın bir parçası olarak yazılmasını gerektirmez. Yalnızca bir HTTP taşıması ile IIS barındırma kullanabilirsiniz.  
  
 WCF ve ASP.NET ile etkileşim kurma hakkında daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md). Güvenliği yapılandırma hakkında daha fazla bilgi için bkz. [güvenlik](security.md).  
  
 Bu örneğin kaynak kopyası için bkz. [satır Içi kod kullanarak IIS barındırma](../samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS tarafından barındırılan bir hizmet oluşturmak için  
  
1. IIS 'nin bilgisayarınızda yüklü olduğundan ve çalıştığından emin olun. IIS yükleme ve yapılandırma hakkında daha fazla bilgi için bkz. [ııs 7,0 yükleme ve yapılandırma](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. "IISHostedCalcService" adlı uygulama dosyalarınız için yeni bir klasör oluşturun, ASP.NET klasörünün içeriğine erişebildiğinden emin olun ve bu uygulama dizininde fiziksel olarak bulunan yeni bir IIS uygulaması oluşturmak için IIS Yönetim Aracı 'nı kullanın. Uygulama dizini için bir diğer ad oluştururken "IISHostedCalc" kullanın.  
  
3. Uygulama dizininde "Service. svc" adlı yeni bir dosya oluşturun. Aşağıdaki öğeyi ekleyerek bu dosyayı düzenleyin @ServiceHost .  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Uygulama dizini içinde bir App_Code alt dizini oluşturun.  
  
5. App_Code alt dizininde Service.cs adlı bir kod dosyası oluşturun.  
  
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
  
     Bu örnek, yapılandırma dosyasındaki uç noktaları açıkça belirtir. Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
11. Hizmetin doğru şekilde barındırıldığından emin olmak için Internet Explorer 'ın bir örneğini açın ve hizmetin URL 'sine gidin:`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Örnek  
 Aşağıda, IIS tarafından barındırılan Hesaplayıcı hizmeti için kodun tamamen bir listesi verilmiştir.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Services'te Barındırma](hosting-in-internet-information-services.md)
- [Barındırma Hizmetleri](../hosting-services.md)
- [WCF Hizmetleri ve ASP.NET](wcf-services-and-aspnet.md)
- [Güvenlik](security.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
