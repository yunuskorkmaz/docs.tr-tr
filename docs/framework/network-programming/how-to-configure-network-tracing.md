---
title: "Nasıl yapılır: ağ İzlemeyi Yapılandır"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a6b277b2676409bebc059637daca5681b853f03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-network-tracing"></a>Nasıl yapılır: ağ İzlemeyi Yapılandır
Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir. Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun. İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz: [etkinleştirme ağ izleme](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır. Her (örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows\ bilgisayarınızda yüklü .NET Framework sürümü için %Windir%\Microsoft.NET\Framework altında klasörlerde ayrı machine.config dosyasının yok Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
### <a name="to-configure-network-tracing"></a>Ağ izlemesini yapılandırmak için  
  
-   Aşağıdaki satırları uygun yapılandırma dosyasına ekleyin. Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"  
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 Bir ad eklediğinizde `<switches>` bloğu, izleme çıktısı bazı yöntemler adına ilgili bilgileri içerir. Aşağıdaki tabloda çıkış açıklanmaktadır.  
  
|Ad|Çıkış kaynağı|  
|----------|-----------------|  
|`System.Net.Sockets`|Bazı genel yöntemini <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, ve <xref:System.Net.Dns> sınıfları|  
|`System.Net`|Bazı genel yöntemini <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FtpWebResponse> sınıfları ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifika hataları.)|  
|`System.Net.HttpListener`|Bazı genel yöntemini <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, ve <xref:System.Net.HttpListenerResponse> sınıfları.|  
|`System.Net.Cache`|Bazı özel ve iç yöntemler `System.Net.Cache`.|  
|`System.Net.Http`|Bazı genel yöntemini <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, ve <xref:System.Net.Http.WebRequestHandler> sınıfları.|  
|`System.Net.WebSockets.WebSocket`|Bazı genel yöntemini <xref:System.Net.WebSockets.ClientWebSocket> ve <xref:System.Net.WebSockets.WebSocket> sınıfları.|  
  
 Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.  
  
|Öznitelik adı|Öznitelik değeri|  
|--------------------|---------------------|  
|`Value`|Gerekli <xref:System.String> özniteliği. Çıkışın ayrıntı düzeyini ayarlar. Yasal değerler `Critical`, `Error`, `Verbose`, `Warning`, ve `Information`.<br /><br /> Bu özniteliği üzerinde ayarlanmalıdır \<ad ekleyin > öğesinin \<anahtarları > örnekte gösterildiği gibi öğesi. Üzerinde bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.|  
|`maxdatasize`|İsteğe bağlı <xref:System.Int32> özniteliği. Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar. Varsayılan değer 1024'tür.<br /><br /> Bu öznitelik üzerinde ayarlamalısınız \<kaynak > örnekte gösterildiği gibi öğesi. Bu öznitelik altında bir öğede ayarlanırsa bir özel durum \<anahtarları > öğesi.|  
|`Tracemode`|İsteğe bağlı <xref:System.String> özniteliği. Kümesine `includehex` Protokolü izlemeleri onaltılık ve metin biçiminde göstermek için. Kümesine `protocolonly` yalnızca metin göstermek için. Varsayılan değer `includehex` şeklindedir.<br /><br /> Bu öznitelik üzerinde ayarlamalısınız \<anahtarları > örnekte gösterildiği gibi öğesi. Bu öznitelik altında bir öğede ayarlanırsa bir özel durum \<kaynak > öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ İzlemeyi Yorumlama](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [.NET Framework'te Ağ İzleme](../../../docs/framework/network-programming/network-tracing.md)  
 [Ağ İzlemeyi Etkinleştirme](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [İzleme ve izleme giriş](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
