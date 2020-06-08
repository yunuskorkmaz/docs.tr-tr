---
title: 'Nasıl yapılır: Ağ İzlemeyi Yapılandırma'
description: Bilgisayar yapılandırma dosyasında veya uygulama yapılandırma dosyasında ağ izlemesini yapılandırma hakkında bilgi edinin. Bir uygulama yapılandırma dosyası önceliklidir.
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
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502567"
---
# <a name="how-to-configure-network-tracing"></a>Nasıl yapılır: ağ izlemeyi yapılandırma

Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir. Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun. Daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md).

Bilgisayar yapılandırma dosyası *Machine. config*, *%windir%\Microsoft.NET\Framework* klasöründe depolanır. Bilgisayarda yüklü .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *Machine. config* dosyası vardır, örneğin:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.

## <a name="configure-network-tracing"></a>Ağ izlemeyi yapılandırma

Ağ izlemeyi yapılandırmak için, uygun yapılandırma dosyasına aşağıdaki satırları ekleyin. Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.

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

### <a name="trace-output-from-methods"></a>Metotlardan izleme çıktısı

Bloğa bir ad eklediğinizde `<switches>` , izleme çıktısı, ad ile ilgili bazı yöntemlerin bilgilerini içerir. Aşağıdaki tabloda çıkış açıklanmaktadır:

|Name|Çıkış kaynağı|
|----------|-----------------|
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket>,, <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.TcpClient> Ve sınıflarının bazı ortak yöntemleri <xref:System.Net.Dns> .|
|`System.Net`|<xref:System.Net.HttpWebRequest>,, <xref:System.Net.HttpWebResponse> , Ve sınıflarının bazı genel yöntemleri <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları).|
|`System.Net.HttpListener`|<xref:System.Net.HttpListener>, Ve sınıflarının bazı ortak yöntemleri <xref:System.Net.HttpListenerRequest> <xref:System.Net.HttpListenerResponse> .|
|`System.Net.Cache`|İçindeki bazı özel ve iç Yöntemler `System.Net.Cache` .|
|`System.Net.Http`|,,,, <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler> Ve <xref:System.Net.Http.WebRequestHandler> sınıflarının bazı ortak yöntemleri.|
|`System.Net.WebSockets.WebSocket`|Ve sınıflarının bazı genel yöntemleri <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> .|

### <a name="trace-output-attributes"></a>İzleme çıkış öznitelikleri

Aşağıdaki tabloda listelenen öznitelikler izleme çıkışını yapılandırır:

|Öznitelik adı|Öznitelik değeri|
|--------------------|---------------------|
|`value`|Gerekli <xref:System.String> öznitelik. Çıkışın ayrıntı düzeyini ayarlar. Meşru değerler,,, ve ' dir `Critical` `Error` `Verbose` `Warning` `Information` .<br /><br />Bu öznitelik, **Switches** öğesinin **Add** öğesinde ayarlanmalıdır. **Kaynak** öğede bu öznitelik ayarlandıysa bir özel durum oluşturulur.<br/><br/>Örnek: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|İsteğe bağlı <xref:System.Int32> öznitelik. Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar. Varsayılan değer 1024 ' dir.<br /><br />Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır. **Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.<br/><br/>Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|İsteğe bağlı <xref:System.String> öznitelik. `includehex`Protokol izlemelerini onaltılık ve metin biçiminde göstermek için olarak ayarlayın. `protocolonly`Yalnızca metni göstermek için olarak ayarlayın. Varsayılan değer: `includehex`.<br /><br />Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır. **Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.<br/><br/>Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Ayrıca bkz.

- [Ağ İzlemeyi Yorumlama](interpreting-network-tracing.md)
- [.NET Framework'te Ağ İzleme](network-tracing.md)
- [Ağ İzlemeyi Etkinleştirme](enabling-network-tracing.md)
- [İzleme ve İşaretleme Uygulamaları](../debug-trace-profile/tracing-and-instrumenting-applications.md)
