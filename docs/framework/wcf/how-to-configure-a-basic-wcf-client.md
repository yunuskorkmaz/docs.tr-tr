---
title: 'Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: c03bf37c737a19b0a90f12e7ad5db78b75323f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499281"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma
Temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken altı görevleri beşinci budur. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Bu konuda ele alınmıştır hizmet Başvurusu Ekle işlevselliği kullanılarak oluşturulan istemci yapılandırma dosyası [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İstemci yapılandırma İstemcinin hizmete erişmek için kullandığı uç noktası belirterek oluşur. Bir adresi, bağlama ve bir sözleşme bir uç nokta var ve bunların her biri istemci yapılandırma sürecinde belirtilmelidir.  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Windows Communication Foundation istemcisi yapılandırma  
  
1.  Oluşturulan yapılandırma dosyası (App.config) GettingStartedClient projesinden açın. Aşağıdaki örnek, oluşturulan yapılandırma dosyası görülmektedir. Altında [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, Bul [ \<uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     Bu örnek, istemcinin şu adresten bulunduğu hizmete erişmek için kullandığı uç nokta yapılandırır: http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     Uç nokta öğesi belirleyen `ServiceReference1.ICalculator` hizmet sözleşmesini WCF İstemcisi hizmeti arasındaki iletişimi için kullanılır. WCF kanalı sistem tarafından sağlanan ile yapılandırılmış <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>. Bu sözleşme, Visual Studio'da hizmet Başvurusu Ekle kullanılarak oluşturuldu. Bu temelde GettingStartedLib proje tanımlanan sözleşme bir kopyasıdır. <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.  
  
2.  Bu yapılandırma ile oluşturulan istemciyi kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
