---
title: Windows Kimlik Doğrulama ile Taşıma Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: 17
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5effb18435241b00c3036fd23e15ef5ce485b646
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="transport-security-with-windows-authentication"></a>Windows Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Windows security tarafından korunan hizmet ve istemci. Programlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows kimlik bilgileri olan bir hizmeti güvenli](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Bir intranet Web hizmeti, İnsan Kaynakları bilgilerini görüntüler. İstemci, bir Windows formu uygulamasıdır. Uygulama etki alanında etki alanı güvenliğini sağlama Kerberos denetleyicisiyle dağıtılır.  
  
 ![Taşıma güvenliği Windows kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Taşıma|  
|Birlikte Çalışabilirlik|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet (Windows tümleşik kimlik doğrulaması kullanarak)<br /><br /> Evet (Windows tümleşik kimlik doğrulaması kullanarak)|  
|Bütünlük|Evet|  
|Gizliliği|Evet|  
|Taşıma|NET. TCP|  
|Bağlama|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, bir Windows Güvenlik kullanan bir hizmet uç noktası oluşturma gösterilmektedir.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Yapılandırma  
 Hizmet uç nokta ayarlamayı kodu yerine aşağıdaki yapılandırma kullanılabilir:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.  
  
-   Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın. Örneğin:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod istemci oluşturur. Bağlama aktarım modu güvenliği Windows kümesi istemci kimlik bilgisi türü ile TCP taşıma ile kullanmak için yapılandırılır.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma kodu yerine istemci oluşturmak için kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
