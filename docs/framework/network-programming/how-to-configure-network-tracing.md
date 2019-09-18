---
title: 'Nasıl yapılır: Ağ İzlemeyi Yapılandırma'
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
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048377"
---
# <a name="how-to-configure-network-tracing"></a>Nasıl yapılır: Ağ İzlemeyi Yapılandırma
Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir. Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun. İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md).  
  
 Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır. Bilgisayarda yüklü .NET Framework her sürümü için%Windir%\Microsoft.NET\Framework altındaki klasörlerde ayrı bir Machine. config dosyası vardır (örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows \ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.  
  
### <a name="to-configure-network-tracing"></a>Ağ izlemesini yapılandırmak için  
  
- Aşağıdaki satırları uygun yapılandırma dosyasına ekleyin. Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.  
  
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
            traceOutputOptions="ProcessId, DateTime" 
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 `<switches>` Bloğa bir ad eklediğinizde, izleme çıktısı, ad ile ilgili bazı yöntemlerin bilgilerini içerir. Aşağıdaki tabloda çıkış açıklanmaktadır.  
  
|Ad|Çıkış kaynağı|  
|----------|-----------------|  
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket> ,<xref:System.Net.Sockets.TcpListener>, Ve sınıflarının<xref:System.Net.Dns> bazı ortak yöntemleri <xref:System.Net.Sockets.TcpClient>|  
|`System.Net`|,,, Ve<xref:System.Net.FtpWebResponse> sınıflarının bazı genel yöntemleri ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları). <xref:System.Net.FtpWebRequest> <xref:System.Net.HttpWebResponse> <xref:System.Net.HttpWebRequest>|  
|`System.Net.HttpListener`|<xref:System.Net.HttpListener> ,<xref:System.Net.HttpListenerRequest>Ve sınıflarının<xref:System.Net.HttpListenerResponse> bazı ortak yöntemleri.|  
|`System.Net.Cache`|İçindeki `System.Net.Cache`bazı özel ve iç Yöntemler.|  
|`System.Net.Http`|<xref:System.Net.Http.HttpClient> ,<xref:System.Net.Http.DelegatingHandler> ,,<xref:System.Net.Http.WebRequestHandler> , Ve sınıflarının bazı ortak yöntemleri. <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler>|  
|`System.Net.WebSockets.WebSocket`|<xref:System.Net.WebSockets.ClientWebSocket> Ve<xref:System.Net.WebSockets.WebSocket> sınıflarının bazı genel yöntemleri.|  
  
 Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.  
  
|Öznitelik adı|Öznitelik değeri|  
|--------------------|---------------------|  
|`Value`|Gerekli <xref:System.String> öznitelik. Çıkışın ayrıntı düzeyini ayarlar. `Critical`Meşru değerler `Error` ,`Warning`,, ve`Information`' dir. `Verbose`<br /><br /> Bu öznitelik, örnekte gösterildiği gibi \< \<anahtarlar > öğesinin ad Ekle > öğesinde ayarlanmalıdır. Bu öznitelik, \<kaynak > öğesinde ayarlandıysa, bir özel durum oluşturulur.|  
|`maxdatasize`|İsteğe <xref:System.Int32> bağlı öznitelik. Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar. Varsayılan değer 1024 ' dir.<br /><br /> Bu öznitelik, örnekte gösterildiği gibi, \<kaynak > öğesinde ayarlanmalıdır. Bu öznitelik, \<anahtarlar > öğesi altındaki bir öğe üzerinde ayarlandıysa, bir özel durum oluşturulur.|  
|`Tracemode`|İsteğe <xref:System.String> bağlı öznitelik. Protokol izlemelerini `includehex` onaltılık ve metin biçiminde göstermek için olarak ayarlayın. Yalnızca metni `protocolonly` göstermek için olarak ayarlayın. Varsayılan değer `includehex` şeklindedir.<br /><br /> Bu öznitelik, örnekte gösterildiği gibi \<anahtarlar > öğesinde ayarlanmalıdır. Bu öznitelik, \<kaynak > öğesinin altındaki bir öğede ayarlandıysa bir özel durum oluşturulur.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Yorumlama](interpreting-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [İzleme ve İşaretleme Uygulamaları](../debug-trace-profile/tracing-and-instrumenting-applications.md)
