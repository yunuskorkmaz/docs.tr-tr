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
ms.openlocfilehash: 12f328d58ef568c78d1e2c8a8ff564839cba9f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="a542c-102">Nasıl yapılır: ağ İzlemeyi Yapılandır</span><span class="sxs-lookup"><span data-stu-id="a542c-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="a542c-103">Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="a542c-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="a542c-104">Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a542c-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="a542c-105">İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz: [etkinleştirme ağ izleme](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="a542c-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="a542c-106">Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="a542c-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="a542c-107">Her (örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows\ bilgisayarınızda yüklü .NET Framework sürümü için %Windir%\Microsoft.NET\Framework altında klasörlerde ayrı machine.config dosyasının yok Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="a542c-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="a542c-108">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a542c-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="a542c-109">Ağ izlemesini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="a542c-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="a542c-110">Aşağıdaki satırları uygun yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a542c-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="a542c-111">Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a542c-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="a542c-112">Bir ad eklediğinizde `<switches>` bloğu, izleme çıktısı bazı yöntemler adına ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a542c-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="a542c-113">Aşağıdaki tabloda çıkış açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a542c-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="a542c-114">Ad</span><span class="sxs-lookup"><span data-stu-id="a542c-114">Name</span></span>|<span data-ttu-id="a542c-115">Çıkış kaynağı</span><span class="sxs-lookup"><span data-stu-id="a542c-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="a542c-116">Bazı genel yöntemini <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, ve <xref:System.Net.Dns> sınıfları</span><span class="sxs-lookup"><span data-stu-id="a542c-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="a542c-117">Bazı genel yöntemini <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FtpWebResponse> sınıfları ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifika hataları.)</span><span class="sxs-lookup"><span data-stu-id="a542c-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="a542c-118">Bazı genel yöntemini <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, ve <xref:System.Net.HttpListenerResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a542c-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="a542c-119">Bazı özel ve iç yöntemler `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="a542c-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="a542c-120">Bazı genel yöntemini <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, ve <xref:System.Net.Http.WebRequestHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a542c-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="a542c-121">Bazı genel yöntemini <xref:System.Net.WebSockets.ClientWebSocket> ve <xref:System.Net.WebSockets.WebSocket> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a542c-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="a542c-122">Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a542c-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="a542c-123">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="a542c-123">Attribute name</span></span>|<span data-ttu-id="a542c-124">Öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="a542c-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="a542c-125">Gerekli <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a542c-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="a542c-126">Çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a542c-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="a542c-127">Yasal değerler `Critical`, `Error`, `Verbose`, `Warning`, ve `Information`.</span><span class="sxs-lookup"><span data-stu-id="a542c-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="a542c-128">Bu özniteliği üzerinde ayarlanmalıdır \<ad ekleyin > öğesinin \<anahtarları > örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="a542c-129">Üzerinde bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="a542c-130">İsteğe bağlı <xref:System.Int32> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a542c-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="a542c-131">Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a542c-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="a542c-132">Varsayılan değer 1024'tür.</span><span class="sxs-lookup"><span data-stu-id="a542c-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="a542c-133">Bu öznitelik üzerinde ayarlamalısınız \<kaynak > örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="a542c-134">Bu öznitelik altında bir öğede ayarlanırsa bir özel durum \<anahtarları > öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="a542c-135">İsteğe bağlı <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a542c-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="a542c-136">Kümesine `includehex` Protokolü izlemeleri onaltılık ve metin biçiminde göstermek için.</span><span class="sxs-lookup"><span data-stu-id="a542c-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="a542c-137">Kümesine `protocolonly` yalnızca metin göstermek için.</span><span class="sxs-lookup"><span data-stu-id="a542c-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="a542c-138">Varsayılan değer `includehex` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a542c-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="a542c-139">Bu öznitelik üzerinde ayarlamalısınız \<anahtarları > örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="a542c-140">Bu öznitelik altında bir öğede ayarlanırsa bir özel durum \<kaynak > öğesi.</span><span class="sxs-lookup"><span data-stu-id="a542c-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a542c-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a542c-141">See Also</span></span>  
 [<span data-ttu-id="a542c-142">Ağ izleme yorumlama</span><span class="sxs-lookup"><span data-stu-id="a542c-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="a542c-143">.NET Framework'te ağ izleme</span><span class="sxs-lookup"><span data-stu-id="a542c-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="a542c-144">Ağ izlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a542c-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="a542c-145">İzleme ve izleme giriş</span><span class="sxs-lookup"><span data-stu-id="a542c-145">Introduction to Instrumentation and Tracing</span></span>](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
