---
title: İş Akışı Hizmetlerini Barındırma
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: dbb5e9b687a735376d720b83607fc67350cd429f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613331"
---
# <a name="hosting-workflow-services"></a>İş Akışı Hizmetlerini Barındırma
Bir iş akışı hizmeti, gelen iletilere yanıt vermesi için barındırılması gerekir. İş akışı hizmetleri WCF Mesajlaşma altyapısını kullanır ve bu nedenle benzer şekillerde barındırılır. WCF hizmetlerinde olduğu gibi iş akışı Hizmetleri, yönetilen bir uygulamada, Internet Information Services (IIS) altında veya Windows İşlem Etkinleştirme Hizmetleri (WAS) altında barındırılabilir. Ayrıca, iş akışı Hizmetleri Windows Server App Fabric altında barındırılabilir. Windows Server App Fabric hakkında daha fazla bilgi için bkz. [Windows Server App Fabric belgeleri](https://go.microsoft.com/fwlink/?LinkId=193037), [AppFabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=196494), ve [AppFabric barındırma kavramları](https://go.microsoft.com/fwlink/?LinkId=196495). Bkz: ana bilgisayar WCF için çeşitli yollar hakkında daha fazla bilgi hizmetleri için [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Yönetilen bir uygulamada barındırma
 Yönetilen bir uygulamada bir iş akışı hizmeti barındırmak için kullandığınız <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Oluşturucusu, tek bir iş akışı hizmet örneği, bir iş akışı hizmet tanımı veya Mesajlaşma etkinlikleriyle iş akışı kullanan bir etkinlik belirtmenize olanak sağlar. Çağırma <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> gelen iletiler için dinleme başlatmak hizmetin neden olur.

## <a name="hosting-under-iis-or-was"></a>IIS ya da WAS altında barındırma
 IIS ya da WAS altında bir iş akışı hizmeti barındırma, sanal dizin oluşturma ve hizmet ve davranışını tanımlayan sanal dizinde dosyaları yerleştirme içerir. IIS ya da WAS altında bir iş akışı hizmeti var. barındırma birkaç olasılık olduğunda:

- İş akışı hizmeti tanımlayan bir IIS / hizmet davranışları, uç noktaları ve diğer yapılandırma öğeleri belirten bir Web.config dosyasıyla birlikte sanal dizini olan bir .xamlx dosyası yerleştirin.

- İş akışı hizmeti tanımlayan bir IIS / sanal dizini olan bir .xamlx dosyası yerleştirin. .Xamlx dosyayı kullanıma sunulacak uç nokta belirtir. Uç noktalar olarak belirtilen bir `WorkflowService.Endpoints` aşağıdaki örnekte gösterildiği gibi bir öğe.

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
    > Davranış ayarları belirtmek gerekiyorsa bir Web.config kullanmalısınız .xamlx dosyasında, davranışları belirtilemez.

- İş akışı hizmeti tanımlayan bir IIS / sanal dizini olan bir .xamlx dosyası yerleştirin. Ayrıca, sanal dizinde .svc dosyası yerleştirin. .Svc dosyası özel bir Web hizmeti ana bilgisayar üreteci belirtin, özel davranışı uygulamak veya özel bir konumdan yapılandırması yük sağlar.

- IIS'de bir derleme yerleştirmek / WCF kullanan bir etkinlik içeren sanal dizin Mesajlaşma etkinlikleri.

 Bir iş akışı hizmeti tanımlayan bir .xamlx dosyası içermelidir bir <`Service`> kök öğesinden türetilen her tür içeren bir kök öğesi veya <xref:System.Workflow.ComponentModel.Activity>. Visual Studio etkinlik şablonu kullanarak, bir .xamlx dosyası oluşturulur. WCF iş akışı hizmet şablonunu kullanarak, bir .xamlx dosyası oluşturulur.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Windows Server AppFabric altında iş akışı hizmetlerini barındırma
 Windows Server App Fabric altında bir iş akışı hizmeti barındırma IIS altında'i barındırıyor olarak aynı şekilde yapılır / WAS'da. Tek fark, Windows Server App Fabric yüklendiğini gerçeğidir. Windows Server App Fabric Internet Information Services Manager, yanı sıra powershell commandlet'lerini eklenmiş olan araçları sağlar. Bu araçlar, dağıtma, yönetme ve iş akışı hizmetleri ve WCF hizmetlerini izleme basitleştirin.

## <a name="referencing-custom-activities"></a>Özel etkinlikler başvurma
 Özel etkinlikler başvuruları eklenmelidir <`Assemblies`> bölümündeki <`System.Web.Compilation`> uygulama etki alanına yüklenir ve XAML seri durumdan çıkarıcı türleri bulamaz. Makine üzerindeki tüm uygulamalara ayarlarının uygulanması gerekiyorsa bu ayarları uygulama düzeyinde veya kök Web.config yapılabilir.

## <a name="deployment"></a>Dağıtım
 Web dağıtım aracı dağıtım görevi kolaylaştırmak için oluşturuldu. Aracı, IIS 6.0 ve IIS 7.0 arasında uygulama geçirme, sunucu grupları, eşitleme ve paketleme, arşivleme ve Web uygulamaları dağıtmanıza olanak sağlar. Daha fazla bilgi için [MS dağıtımı aracı](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Konağı Dahili Bileşenleri](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)
- [WorkflowServiceHost Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)