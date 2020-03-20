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
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040650"
---
# <a name="how-to-configure-network-tracing"></a>Nasıl yapılandırılır: Ağ izlemesini yapılandırma

Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir. Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun. Daha fazla bilgi için [bkz.](enabling-network-tracing.md)

Bilgisayar yapılandırma dosyası, *machine.config*, *%windir%\Microsoft.NET\Framework* klasöründe depolanır. Bilgisayarda yüklü olan .NET Framework'ün her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *machine.config* dosyası vardır, örneğin:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.

## <a name="configure-network-tracing"></a>Ağ izlemeyi yapılandırma

Ağ izlemesini yapılandırmak için aşağıdaki satırları uygun yapılandırma dosyasına ekleyin. Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.

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

### <a name="trace-output-from-methods"></a>Yöntemlerden çıkış izleme

`<switches>` Bloya bir ad eklediğinizde, izleme çıktısı adla ilgili bazı yöntemlerden bilgiler içerir. Aşağıdaki tabloda çıktı açıklanır:

|Adı|Çıkış kaynağı|
|----------|-----------------|
|`System.Net.Sockets`|Bazı kamu yöntemleri <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Dns> , ve sınıflar.|
|`System.Net`|Bazı ortak yöntemler <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.FtpWebResponse> , ve sınıflar ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları).|
|`System.Net.HttpListener`|Bazı kamu yöntemleri <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest>, <xref:System.Net.HttpListenerResponse> , ve sınıflar.|
|`System.Net.Cache`|Bazı özel ve `System.Net.Cache`dahili yöntemler .|
|`System.Net.Http`|Bazı genel yöntemler <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, <xref:System.Net.Http.WebRequestHandler> , , ve sınıflar.|
|`System.Net.WebSockets.WebSocket`|Ve <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> sınıfların bazı kamu yöntemleri.|

### <a name="trace-output-attributes"></a>Çıkış özniteliklerini izleme

Aşağıdaki tabloda listelenen öznitelikler iz çıktısını yapılandırır:

|Öznitelik adı|Öznitelik değeri|
|--------------------|---------------------|
|`value`|Gerekli <xref:System.String> öznitelik. Çıkışın ayrıntı düzeyini ayarlar. Meşru değerler `Critical` `Error`, `Verbose` `Warning`, `Information`, , ve .<br /><br />Bu öznitelik **anahtarları** öğesinin **ekle** öğesi üzerinde ayarlanmalıdır. Bu öznitelik **kaynak** öğe üzerinde ayarlanırsa bir özel durum atılır.<br/><br/>Örnek: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|İsteğe bağlı <xref:System.Int32> öznitelik. Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar. Varsayılan değer 1024'dür.<br /><br />Bu öznitelik **kaynak** öğe üzerinde ayarlanmalıdır. Bu öznitelik **anahtarlar** öğesi altında bir öğe üzerinde ayarlanırsa bir özel durum atılır.<br/><br/>Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|İsteğe bağlı <xref:System.String> öznitelik. `includehex` Protokol izlerini hexadecimal ve metin biçiminde gösterecek şekilde ayarlayın. Yalnızca `protocolonly` metni gösterecek şekilde ayarlayın. Varsayılan değer: `includehex`.<br /><br />Bu öznitelik **kaynak** öğe üzerinde ayarlanmalıdır. Bu öznitelik **anahtarlar** öğesi altında bir öğe üzerinde ayarlanırsa bir özel durum atılır.<br/><br/>Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Yorumlama](interpreting-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [İzleme ve İşaretleme Uygulamaları](../debug-trace-profile/tracing-and-instrumenting-applications.md)
