---
title: İş Akışı Hizmetlerini Barındırma
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 908ef7ebb9bfb1e2c49d96e41c0df1d843c0454d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597286"
---
# <a name="hosting-workflow-services"></a>İş Akışı Hizmetlerini Barındırma

Gelen iletilere yanıt vermesi için bir iş akışı hizmetinin barındırılması gerekir. İş akışı hizmetleri WCF mesajlaşma altyapısını kullanır ve bu nedenle benzer yollarla barındırılır. WCF Hizmetleri gibi, iş akışı hizmetleri herhangi bir yönetilen uygulamada, Internet Information Services (IIS) veya Windows Işlem etkinleştirme Hizmetleri (WAS) altında barındırılabilir. Ayrıca, iş akışı hizmetleri Windows Server App Fabric altında barındırılabilir. Windows Server App Fabric hakkında daha fazla bilgi için bkz. [Windows Server App Fabric belgeleri](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)), [AppFabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))ve [AppFabric barındırma kavramları](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)). WCF hizmetlerini barındırmak için çeşitli yollar hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Yönetilen bir uygulamada barındırma
 Bir iş akışı hizmetini yönetilen bir uygulamada barındırmak için <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfını kullanın. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Oluşturucu, tek bir iş akışı hizmet örneği, bir iş akışı hizmeti tanımı veya iş akışı mesajlaşma etkinliklerini kullanan bir etkinlik belirtmenize olanak tanır. Çağırma <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> , hizmetin gelen iletileri dinlemeye başlamasını sağlar.

## <a name="hosting-under-iis-or-was"></a>IIS veya WAS altında barındırma
 Bir iş akışı hizmetini IIS kapsamında barındırmak, sanal bir dizin oluşturmayı ve hizmeti ve davranışını tanımlayan sanal dizine dosya yerleştirmeyi içerir. Bir iş akışı hizmetini IIS altında barındırırken veya birkaç olasılıktan dolayı:

- Hizmet davranışlarını, uç noktaları ve diğer yapılandırma öğelerini belirten Web. config dosyası ile birlikte bir IIS/WAS sanal dizininde iş akışı hizmetini tanımlayan bir. xamlx dosyası yerleştirin.

- Bir IIS/WAS sanal dizininde iş akışı hizmetini tanımlayan bir. xamlx dosyası yerleştirin. . Xamlx dosyası, kullanıma sunulacak uç noktaları belirtir. Uç noktalar `WorkflowService.Endpoints` , aşağıdaki örnekte gösterildiği gibi bir öğesinde belirtilir.

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
    > Davranışlar bir. xamlx dosyasında belirtilemez, bu nedenle davranış ayarlarını belirtmeniz gerekiyorsa bir Web. config kullanmanız gerekir.

- Bir IIS/WAS sanal dizininde iş akışı hizmetini tanımlayan bir. xamlx dosyası yerleştirin. Ayrıca, sanal dizine bir. svc dosyası yerleştirin. . Svc dosyası özel bir Web hizmeti konak fabrikası belirtmenize, özel davranış uygulamanıza veya yapılandırmanın özel bir konumdan yüklenmesine olanak sağlar.

- Bir derlemeyi, WCF mesajlaşma etkinliklerini kullanan bir etkinlik içeren IIS/WAS sanal dizinine yerleştirin.

 Bir iş akışı hizmetini tanımlayan bir. xamlx dosyası bir <`Service`> kök öğesi ya da öğesinden türetilmiş herhangi bir türü içeren bir kök öğesi içermelidir <xref:System.Workflow.ComponentModel.Activity> . Visual Studio etkinlik şablonu kullanılırken bir. xamlx dosyası oluşturulur. WCF Iş akışı hizmeti şablonu kullanılırken bir. xamlx dosyası oluşturulur.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Windows Server App Fabric altında Iş akışı hizmetlerini barındırma
 Windows Server App Fabric altında bir iş akışı hizmetini barındırmak, IIS/WAS altında barındırmakla aynı şekilde yapılır. Tek fark, Windows Server App Fabric 'in yüklü olduğu gerçedir. Windows Server App Fabric, Internet Information Services Manager 'a eklenen araçları ve PowerShell commandizin sağlar. Bu araçlar, iş akışı hizmetleri ve WCF hizmetlerini dağıtma, yönetme ve izlemeyi basitleştirir.

## <a name="referencing-custom-activities"></a>Özel etkinliklere başvurma
 Özel etkinliklere yapılan başvuruların `Assemblies` <> altındaki <> bölümüne eklenmesi gerekir `System.Web.Compilation` ve bu sayede uygulama etki alanına YÜKLENIR ve xaml seri hale getirici türlerini bulabilecektir. Bu ayarlar, uygulama düzeyinde veya ayarların makinedeki tüm uygulamalara uygulanması gerekiyorsa kök Web. config ' de yapılabilir.

## <a name="deployment"></a>Dağıtım
 Dağıtım işini daha kolay hale getirmek için Web Dağıtım aracı oluşturulmuştur. Araç, uygulamaları IIS 6,0 ile IIS 7,0 arasında geçirmenize, sunucu gruplarını eşitlemeye ve Web uygulamalarını dağıtmanıza, arşivlemenize ve dağıtmanıza olanak tanır. Daha fazla bilgi için bkz. [MS dağıtım aracı](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmeti Konağı Dahili Bileşenleri](workflow-service-host-internals.md)
- [WorkflowServiceHost Yapılandırma](configuring-workflowservicehost.md)
