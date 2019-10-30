---
title: 'Nasıl yapılır: ağ Izlemeyi yapılandırma'
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
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040650"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="97211-102">Nasıl yapılır: ağ izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97211-102">How to: Configure network tracing</span></span>

<span data-ttu-id="97211-103">Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="97211-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="97211-104">Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="97211-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="97211-105">Daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="97211-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="97211-106">Bilgisayar yapılandırma dosyası *Machine. config*, *%windir%\Microsoft.NET\Framework* klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="97211-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="97211-107">Bilgisayarda yüklü .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *Machine. config* dosyası vardır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="97211-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="97211-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="97211-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="97211-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="97211-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="97211-110">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="97211-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="97211-111">Ağ izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97211-111">Configure network tracing</span></span>

<span data-ttu-id="97211-112">Ağ izlemeyi yapılandırmak için, uygun yapılandırma dosyasına aşağıdaki satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97211-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="97211-113">Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97211-113">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="97211-114">Metotlardan izleme çıktısı</span><span class="sxs-lookup"><span data-stu-id="97211-114">Trace output from methods</span></span>

<span data-ttu-id="97211-115">`<switches>` bloğuna bir ad eklediğinizde, izleme çıktısı, ad ile ilgili bazı yöntemlerin bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="97211-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="97211-116">Aşağıdaki tabloda çıkış açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="97211-116">The following table describes the output:</span></span>

|<span data-ttu-id="97211-117">Name</span><span class="sxs-lookup"><span data-stu-id="97211-117">Name</span></span>|<span data-ttu-id="97211-118">Çıkış kaynağı</span><span class="sxs-lookup"><span data-stu-id="97211-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="97211-119"><xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>ve <xref:System.Net.Dns> sınıflarının bazı genel yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97211-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="97211-120"><xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>ve <xref:System.Net.FtpWebResponse> sınıflarının bazı genel yöntemleri ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları).</span><span class="sxs-lookup"><span data-stu-id="97211-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="97211-121"><xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>ve <xref:System.Net.HttpListenerResponse> sınıflarının bazı genel yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97211-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="97211-122">`System.Net.Cache`içindeki bazı özel ve iç Yöntemler.</span><span class="sxs-lookup"><span data-stu-id="97211-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="97211-123"><xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>ve <xref:System.Net.Http.WebRequestHandler> sınıflarının bazı genel yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97211-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="97211-124"><xref:System.Net.WebSockets.ClientWebSocket> ve <xref:System.Net.WebSockets.WebSocket> sınıflarının bazı genel yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97211-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="97211-125">İzleme çıkış öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="97211-125">Trace output attributes</span></span>

<span data-ttu-id="97211-126">Aşağıdaki tabloda listelenen öznitelikler izleme çıkışını yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="97211-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="97211-127">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="97211-127">Attribute name</span></span>|<span data-ttu-id="97211-128">Öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="97211-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="97211-129">Gerekli <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="97211-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="97211-130">Çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="97211-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="97211-131">Meşru değerler `Critical`, `Error`, `Verbose`, `Warning`ve `Information`.</span><span class="sxs-lookup"><span data-stu-id="97211-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="97211-132">Bu öznitelik, **Switches** öğesinin **Add** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97211-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="97211-133">**Kaynak** öğede bu öznitelik ayarlandıysa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97211-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="97211-134">Örnek: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="97211-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="97211-135">İsteğe bağlı <xref:System.Int32> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="97211-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="97211-136">Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="97211-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="97211-137">Varsayılan değer 1024 ' dir.</span><span class="sxs-lookup"><span data-stu-id="97211-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="97211-138">Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97211-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="97211-139">**Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97211-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="97211-140">Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="97211-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="97211-141">İsteğe bağlı <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="97211-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="97211-142">Protokol izlemelerini onaltılık ve metin biçiminde göstermek için `includehex` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97211-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="97211-143">Yalnızca metni göstermek için `protocolonly` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97211-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="97211-144">Varsayılan değer `includehex` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="97211-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="97211-145">Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97211-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="97211-146">**Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97211-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="97211-147">Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="97211-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="97211-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97211-148">See also</span></span>

- [<span data-ttu-id="97211-149">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="97211-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="97211-150">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="97211-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="97211-151">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="97211-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="97211-152">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="97211-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
