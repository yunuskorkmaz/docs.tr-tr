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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="d604a-102">Nasıl yapılır: Ağ İzlemeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d604a-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="d604a-103">Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d604a-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="d604a-104">Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d604a-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="d604a-105">İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz. [ağ Izlemeyi etkinleştirme](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="d604a-105">For information about enabling tracing, see [Enabling Network Tracing](enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="d604a-106">Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="d604a-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="d604a-107">Bilgisayarda yüklü .NET Framework her sürümü için%Windir%\Microsoft.NET\Framework altındaki klasörlerde ayrı bir Machine. config dosyası vardır (örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows \ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="d604a-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="d604a-108">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d604a-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="d604a-109">Ağ izlemesini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d604a-109">To configure network tracing</span></span>  
  
- <span data-ttu-id="d604a-110">Aşağıdaki satırları uygun yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d604a-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="d604a-111">Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d604a-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="d604a-112">`<switches>` Bloğa bir ad eklediğinizde, izleme çıktısı, ad ile ilgili bazı yöntemlerin bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d604a-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="d604a-113">Aşağıdaki tabloda çıkış açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d604a-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="d604a-114">Ad</span><span class="sxs-lookup"><span data-stu-id="d604a-114">Name</span></span>|<span data-ttu-id="d604a-115">Çıkış kaynağı</span><span class="sxs-lookup"><span data-stu-id="d604a-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="d604a-116"><xref:System.Net.Sockets.Socket> ,<xref:System.Net.Sockets.TcpListener>, Ve sınıflarının<xref:System.Net.Dns> bazı ortak yöntemleri <xref:System.Net.Sockets.TcpClient></span><span class="sxs-lookup"><span data-stu-id="d604a-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="d604a-117">,,, Ve<xref:System.Net.FtpWebResponse> sınıflarının bazı genel yöntemleri ve SSL hata ayıklama bilgileri (geçersiz sertifikalar, eksik verenler listesi ve istemci sertifikası hataları). <xref:System.Net.FtpWebRequest> <xref:System.Net.HttpWebResponse> <xref:System.Net.HttpWebRequest></span><span class="sxs-lookup"><span data-stu-id="d604a-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="d604a-118"><xref:System.Net.HttpListener> ,<xref:System.Net.HttpListenerRequest>Ve sınıflarının<xref:System.Net.HttpListenerResponse> bazı ortak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d604a-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="d604a-119">İçindeki `System.Net.Cache`bazı özel ve iç Yöntemler.</span><span class="sxs-lookup"><span data-stu-id="d604a-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="d604a-120"><xref:System.Net.Http.HttpClient> ,<xref:System.Net.Http.DelegatingHandler> ,,<xref:System.Net.Http.WebRequestHandler> , Ve sınıflarının bazı ortak yöntemleri. <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler> <xref:System.Net.Http.MessageProcessingHandler></span><span class="sxs-lookup"><span data-stu-id="d604a-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="d604a-121"><xref:System.Net.WebSockets.ClientWebSocket> Ve<xref:System.Net.WebSockets.WebSocket> sınıflarının bazı genel yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d604a-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="d604a-122">Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d604a-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="d604a-123">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="d604a-123">Attribute name</span></span>|<span data-ttu-id="d604a-124">Öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="d604a-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="d604a-125">Gerekli <xref:System.String> öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d604a-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="d604a-126">Çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d604a-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="d604a-127">`Critical`Meşru değerler `Error` ,`Warning`,, ve`Information`' dir. `Verbose`</span><span class="sxs-lookup"><span data-stu-id="d604a-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="d604a-128">Bu öznitelik, örnekte gösterildiği gibi \< \<anahtarlar > öğesinin ad Ekle > öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d604a-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="d604a-129">Bu öznitelik, \<kaynak > öğesinde ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d604a-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="d604a-130">İsteğe <xref:System.Int32> bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d604a-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="d604a-131">Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d604a-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="d604a-132">Varsayılan değer 1024 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d604a-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="d604a-133">Bu öznitelik, örnekte gösterildiği gibi, \<kaynak > öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d604a-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="d604a-134">Bu öznitelik, \<anahtarlar > öğesi altındaki bir öğe üzerinde ayarlandıysa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d604a-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="d604a-135">İsteğe <xref:System.String> bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d604a-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="d604a-136">Protokol izlemelerini `includehex` onaltılık ve metin biçiminde göstermek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d604a-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="d604a-137">Yalnızca metni `protocolonly` göstermek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d604a-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="d604a-138">Varsayılan değer `includehex` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d604a-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="d604a-139">Bu öznitelik, örnekte gösterildiği gibi \<anahtarlar > öğesinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d604a-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="d604a-140">Bu öznitelik, \<kaynak > öğesinin altındaki bir öğede ayarlandıysa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d604a-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d604a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d604a-141">See also</span></span>

- [<span data-ttu-id="d604a-142">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="d604a-142">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="d604a-143">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="d604a-143">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="d604a-144">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d604a-144">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="d604a-145">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d604a-145">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
