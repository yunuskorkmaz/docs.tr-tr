---
title: 'Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f23918031c6cc8cd6509d7b7c079b8df050bbb08
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Yapılandırma
Temel bir oluşturmak için gereken altı görevleri beşinci budur [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama. Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.  
  
 Bu konuda disuccess hizmet Başvurusu Ekle işlevselliği kullanılarak oluşturulan istemci yapılandırma dosyası [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] veya [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İstemci yapılandırma İstemcinin hizmete erişmek için kullandığı uç noktası belirterek oluşur. Bir adresi, bağlama ve bir sözleşme bir uç nokta var ve bunların her biri istemci yapılandırma sürecinde belirtilmelidir.  
  
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
  
     Bu örnek istemcinin şu adresten bulunduğu hizmete erişmek için kullandığı uç nokta yapılandırır: 8000/ServiceModelSamples/Service/CalculatorService  
  
     Uç nokta öğesi belirleyen `ServiceReference1.ICalculator` hizmet sözleşmesini WCF İstemcisi hizmeti arasındaki iletişimi için kullanılır. WCF kanalı sistem tarafından sağlanan ile yapılandırılmış <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>. Bu sözleşme, Visual Studio'da hizmet Başvurusu Ekle kullanılarak oluşturuldu. Bu temelde GettingStartedLib proje tanımlanan sözleşme bir kopyasıdır. <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] Bu yapılandırma ile oluşturulan istemciyi kullanma hakkında [nasıl yapılır: bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Başlarken](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
