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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="6602b-104">Nasıl yapılır: ağ izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6602b-104">How to: Configure network tracing</span></span>

<span data-ttu-id="6602b-105">Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="6602b-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="6602b-106">Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6602b-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="6602b-107">Daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="6602b-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="6602b-108">Bilgisayar yapılandırma dosyası *Machine. config*, *%windir%\Microsoft.NET\Framework* klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="6602b-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="6602b-109">Bilgisayarda yüklü .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *Machine. config* dosyası vardır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="6602b-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="6602b-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="6602b-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="6602b-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="6602b-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="6602b-112">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="6602b-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="6602b-113">Ağ izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6602b-113">Configure network tracing</span></span>

<span data-ttu-id="6602b-114">Ağ izlemeyi yapılandırmak için, uygun yapılandırma dosyasına aşağıdaki satırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6602b-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="6602b-115">Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6602b-115">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="6602b-116">Metotlardan izleme çıktısı</span><span class="sxs-lookup"><span data-stu-id="6602b-116">Trace output from methods</span></span>

<span data-ttu-id="6602b-117">Bloğa bir ad eklediğinizde `<switches>` , izleme çıktısı, ad ile ilgili bazı yöntemlerin bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6602b-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="6602b-118">Aşağıdaki tabloda çıkış açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6602b-118">The following table describes the output:</span></span>

|<span data-ttu-id="6602b-119">Name</span><span class="sxs-lookup"><span data-stu-id="6602b-119">Name</span></span>|<span data-ttu-id="6602b-120">Çıkış kaynağı</span><span class="sxs-lookup"><span data-stu-id="6602b-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="6602b-121"><xref:System.Net.Sockets.Socket>,, <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.TcpClient> Ve sınıflarının bazı ortak yöntemleri <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="6602b-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="6602b-122"><xref:System.Net.HttpWebRequest>,, <xref:System.Net.HttpWebResponse> , Ve sınıflarının bazı genel yöntemleri <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları).</span><span class="sxs-lookup"><span data-stu-id="6602b-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="6602b-123"><xref:System.Net.HttpListener>, Ve sınıflarının bazı ortak yöntemleri <xref:System.Net.HttpListenerRequest> <xref:System.Net.HttpListenerResponse> .</span><span class="sxs-lookup"><span data-stu-id="6602b-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="6602b-124">İçindeki bazı özel ve iç Yöntemler `System.Net.Cache` .</span><span class="sxs-lookup"><span data-stu-id="6602b-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="6602b-125">,,,, <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler> Ve <xref:System.Net.Http.WebRequestHandler> sınıflarının bazı ortak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6602b-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="6602b-126">Ve sınıflarının bazı genel yöntemleri <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> .</span><span class="sxs-lookup"><span data-stu-id="6602b-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="6602b-127">İzleme çıkış öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="6602b-127">Trace output attributes</span></span>

<span data-ttu-id="6602b-128">Aşağıdaki tabloda listelenen öznitelikler izleme çıkışını yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="6602b-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="6602b-129">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="6602b-129">Attribute name</span></span>|<span data-ttu-id="6602b-130">Öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="6602b-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="6602b-131">Gerekli <xref:System.String> öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6602b-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="6602b-132">Çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6602b-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="6602b-133">Meşru değerler,,, ve ' dir `Critical` `Error` `Verbose` `Warning` `Information` .</span><span class="sxs-lookup"><span data-stu-id="6602b-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="6602b-134">Bu öznitelik, **Switches** öğesinin **Add** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6602b-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="6602b-135">**Kaynak** öğede bu öznitelik ayarlandıysa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6602b-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="6602b-136">Örnek: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="6602b-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="6602b-137">İsteğe bağlı <xref:System.Int32> öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6602b-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="6602b-138">Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6602b-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="6602b-139">Varsayılan değer 1024 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6602b-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="6602b-140">Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6602b-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="6602b-141">**Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6602b-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="6602b-142">Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="6602b-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="6602b-143">İsteğe bağlı <xref:System.String> öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6602b-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="6602b-144">`includehex`Protokol izlemelerini onaltılık ve metin biçiminde göstermek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6602b-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="6602b-145">`protocolonly`Yalnızca metni göstermek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6602b-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="6602b-146">Varsayılan değer: `includehex`.</span><span class="sxs-lookup"><span data-stu-id="6602b-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="6602b-147">Bu öznitelik, **kaynak** öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6602b-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="6602b-148">**Anahtarlar** öğesi altındaki bir öğe üzerinde bu öznitelik ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6602b-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="6602b-149">Örnek: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="6602b-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="6602b-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6602b-150">See also</span></span>

- [<span data-ttu-id="6602b-151">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="6602b-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="6602b-152">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="6602b-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="6602b-153">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6602b-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="6602b-154">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="6602b-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
