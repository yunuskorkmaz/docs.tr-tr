---
title: İş Akışı Hizmetlerini Barındırma
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 02d77b851dcd35108668ee6a42022e9721b84bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-workflow-services"></a>İş Akışı Hizmetlerini Barındırma
Bir iş akışı hizmeti, gelen iletilere yanıt vermesi için barındırılması gerekir. İş akışı hizmetleri WCF Mesajlaşma altyapısını kullanan ve bu nedenle benzer şekilde barındırılır. WCF hizmetleri gibi iş akışı hizmetleri yönetilen bir uygulamada, Internet Information Services (IIS) altında ya da Windows İşlem Etkinleştirme Hizmetleri (WAS) altında barındırılabilir. Ayrıca iş akışı Hizmetleri Windows Server App Fabric altında barındırılabilir. Windows Server App Fabric hakkında daha fazla bilgi için bkz: [Windows Server App Fabric belgelerine](http://go.microsoft.com/fwlink/?LinkId=193037), [AppFabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=196494), ve [AppFabric barındırma kavramları](http://go.microsoft.com/fwlink/?LinkId=196495). Bkz: WCF barındırmak için çeşitli yollar hakkında daha fazla bilgi hizmetleri için [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="hosting-in-a-managed-application"></a>Yönetilen bir uygulamada barındırma  
 Yönetilen bir uygulamada bir iş akışı hizmeti barındırmak için kullandığınız <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Oluşturucusu bir singleton iş akışı hizmet örneği, bir iş akışı hizmeti tanımı veya Mesajlaşma etkinlikleriyle iş akışının kullandığı bir etkinlik belirtmenize olanak verir. Çağırma <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> gelen iletiler için dinleme başlatmak hizmetinin neden olur.  
  
## <a name="hosting-under-iis-or-was"></a>IIS ya da WAS altında barındırma  
 IIS ya da WAS altında bir iş akışı hizmeti barındıran bir sanal dizin oluşturma ve hizmet ve davranışını tanımlamak sanal dizinde dosyaları yerleştirme içerir. IIS ya da WAS altında bir iş akışı hizmeti var. barındırma birkaç olasılık olduğunda:  
  
-   İş akışı hizmeti bir IIS tanımlar / hizmet davranışları, uç noktaları ve diğer yapılandırma öğeleri belirten bir Web.config dosyası ile birlikte sanal dizini olan bir .xamlx dosyası yerleştirin.  
  
-   İş akışı hizmeti bir IIS tanımlar / sanal dizini olan bir .xamlx dosyası yerleştirin. .Xamlx dosya kullanıma sunmak için uç nokta belirtir. Uç noktalar olarak belirtilen bir `WorkflowService.Endpoints` aşağıdaki örnekte gösterildiği gibi öğesi.  
  
    ```xml  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
    ```  
  
    > [!NOTE]
    >  Davranış ayarları belirtmeniz gerekiyorsa bir Web.config kullanmalısınız davranışları .xamlx dosyasında belirtilemez.  
  
-   İş akışı hizmeti bir IIS tanımlar / sanal dizini olan bir .xamlx dosyası yerleştirin. Ayrıca, sanal dizinde .svc dosya yerleştirin. .Svc dosyasındaki özel bir Web hizmeti ana bilgisayar üreteci belirtin, özel davranışı uygulamak veya özel bir konumdan yapılandırma yük sağlar.  
  
-   IIS'de bir derlemeyi yerleştirin / WCF kullanan bir etkinlik içeren sanal dizin etkinlikleri Mesajlaşma.  
  
 Bir iş akışı hizmeti tanımlayan bir .xamlx dosyanın içermesi gereken bir <`Service`> kök türetilmiş herhangi bir türü içeren bir kök öğesi veya <xref:System.Workflow.ComponentModel.Activity>. Kullanırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] etkinlik şablonu .xamlx dosyası oluşturulur. WCF iş akışı hizmeti şablonu kullanarak bir .xamlx dosyası oluşturulur.  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Windows Server App Fabric altında iş akışı hizmetlerini barındırma  
 Windows Server App Fabric altında bir iş akışı hizmeti barındırma IIS altında barındırma olarak aynı şekilde yapılır / OLUŞTU. Tek fark, Windows Server App Fabric yüklendiğini gerçeğidir. Windows Server App Fabric Internet Information Services Yöneticisi yanı için powershell cmdlet'leri eklenen araçlar sağlar. Bu araçlar, dağıtma, yönetme ve iş akışı hizmetleri ve WCF hizmetlerini izleme basitleştirin. biçimindeki telefon numarasıdır. Windows Server App Fabric hakkında daha fazla bilgi için bkz: [Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>Özel etkinlikler başvurma  
 Özel etkinlikler başvurular eklenmelidir <`Assemblies`> altında bölümünde <`System.Web.Compilation`> uygulama etki alanına yüklenir ve XAML kaldırıcı türleri bulabilir. Makinedeki tüm uygulamalar için ayarlar uygulanması gerekiyorsa bu ayarları, uygulama düzeyinde veya kök Web.config yapılabilir.  
  
## <a name="deployment"></a>Dağıtım  
 Web dağıtım aracı, dağıtım işlemini kolaylaştırmak için oluşturuldu. Aracı, IIS 6.0 ve IIS 7.0 arasında uygulamaları geçirmek, sunucu grupları, eşitleme ve paketleme, arşivleme ve Web uygulamalarını dağıtmasına olanak sağlar. Daha fazla bilgi için bkz: [MS dağıtım aracı](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmeti Konağı Dahili Bileşenleri](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [WorkflowServiceHost Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
