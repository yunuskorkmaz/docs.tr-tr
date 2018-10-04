---
title: 'Nasıl yapılır: ağ izlemeyi yapılandırma'
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4b8fa55375de5057eca92591cbf4d9da628a3f85
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582495"
---
# <a name="how-to-configure-network-tracing"></a>Nasıl yapılır: ağ izlemeyi yapılandırma
Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir. Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun. İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz: [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır. (Örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows\ bilgisayarda yüklü .NET Framework'ün her sürümü için %Windir%\Microsoft.NET\Framework altındaki klasörlerde ayrı bir machine.config dosyası yok Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
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
  
 İçin bir ad eklediğinizde `<switches>` blok, izleme çıkışı adla ilgili bazı yöntemlerden alınan bilgiler içerir. Aşağıdaki tabloda çıkış açıklanmaktadır.  
  
|Ad|Çıkış kaynağı|  
|----------|-----------------|  
|`System.Net.Sockets`|Bazı genel yöntemleri <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, ve <xref:System.Net.Dns> sınıfları|  
|`System.Net`|Bazı genel yöntemleri <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FtpWebResponse> sınıflar ve SSL hata ayıklama bilgileri (geçersiz sertifikaları, eksik sertifika verenler listesi ve istemci sertifikası hataları.)|  
|`System.Net.HttpListener`|Bazı genel yöntemleri <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, ve <xref:System.Net.HttpListenerResponse> sınıfları.|  
|`System.Net.Cache`|Bazı özel ve iç yöntemler `System.Net.Cache`.|  
|`System.Net.Http`|Bazı genel yöntemleri <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, ve <xref:System.Net.Http.WebRequestHandler> sınıfları.|  
|`System.Net.WebSockets.WebSocket`|Bazı genel yöntemleri <xref:System.Net.WebSockets.ClientWebSocket> ve <xref:System.Net.WebSockets.WebSocket> sınıfları.|  
  
 Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.  
  
|Öznitelik adı|Öznitelik değeri|  
|--------------------|---------------------|  
|`Value`|Gerekli <xref:System.String> özniteliği. Çıkışın ayrıntı düzeyini ayarlar. Meşru değerler `Critical`, `Error`, `Verbose`, `Warning`, ve `Information`.<br /><br /> Bu özniteliği ayarlanmalıdır \<adı Ekle > öğesinin \<anahtarlar > örnekte gösterildiği gibi bir öğe. Şirket bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.|  
|`maxdatasize`|İsteğe bağlı <xref:System.Int32> özniteliği. Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar. Varsayılan değer 1024'tür.<br /><br /> Bu öznitelik ayarlanmalıdır \<kaynak > örnekte gösterilen şekilde öğesi. Altındaki bir öğede bu öznitelik ayarlanırsa bir özel durum \<anahtarlar > öğesi.|  
|`Tracemode`|İsteğe bağlı <xref:System.String> özniteliği. Kümesine `includehex` protokol izlemelerini onaltılık ve metin biçiminde göstermek için. Kümesine `protocolonly` yalnızca metin göstermek için. Varsayılan değer `includehex` şeklindedir.<br /><br /> Bu öznitelik ayarlanmalıdır \<anahtarlar > örnekte gösterilen şekilde öğesi. Altındaki bir öğede bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ İzlemeyi Yorumlama](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [.NET Framework'te Ağ İzleme](../../../docs/framework/network-programming/network-tracing.md)  
 [Ağ İzlemeyi Etkinleştirme](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [İzlemeye giriş](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
