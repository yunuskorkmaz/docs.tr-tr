---
title: 'Nasıl yapılır: Ağ izlemeyi yapılandırma'
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
ms.openlocfilehash: 3930453e2ba3594e19d8eb7c3dfbceb49c3a1e80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540539"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="7b052-102">Nasıl yapılır: Ağ izlemeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7b052-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="7b052-103">Uygulama veya bilgisayar yapılandırma dosyası, ağ izlemelerinin biçimini ve içeriğini belirleyen ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="7b052-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="7b052-104">Bu yordamı gerçekleştirmeden önce izlemenin etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b052-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="7b052-105">İzlemeyi etkinleştirme hakkında daha fazla bilgi için bkz: [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="7b052-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="7b052-106">Bilgisayar yapılandırma dosyası machine.config, Windows'un yüklü olduğu dizinde %Windir%\Microsoft.NET\Framework klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="7b052-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="7b052-107">(Örneğin, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config veya C:\Windows\ bilgisayarda yüklü .NET Framework'ün her sürümü için %Windir%\Microsoft.NET\Framework altındaki klasörlerde ayrı bir machine.config dosyası yok Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="7b052-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="7b052-108">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b052-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="7b052-109">Ağ izlemesini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="7b052-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="7b052-110">Aşağıdaki satırları uygun yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b052-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="7b052-111">Bu ayarların değerleri ve seçenekleri aşağıdaki tablolarda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7b052-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="7b052-112">İçin bir ad eklediğinizde `<switches>` blok, izleme çıkışı adla ilgili bazı yöntemlerden alınan bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7b052-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="7b052-113">Aşağıdaki tabloda çıkış açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b052-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="7b052-114">Ad</span><span class="sxs-lookup"><span data-stu-id="7b052-114">Name</span></span>|<span data-ttu-id="7b052-115">Çıkış kaynağı</span><span class="sxs-lookup"><span data-stu-id="7b052-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="7b052-116">Bazı genel yöntemleri <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, ve <xref:System.Net.Dns> sınıfları</span><span class="sxs-lookup"><span data-stu-id="7b052-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="7b052-117">Bazı genel yöntemleri <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, ve <xref:System.Net.FtpWebResponse> sınıflar ve SSL hata ayıklama bilgileri (geçersiz sertifikaları, eksik sertifika verenler listesi ve istemci sertifikası hataları.)</span><span class="sxs-lookup"><span data-stu-id="7b052-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="7b052-118">Bazı genel yöntemleri <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, ve <xref:System.Net.HttpListenerResponse> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7b052-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="7b052-119">Bazı özel ve iç yöntemler `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="7b052-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="7b052-120">Bazı genel yöntemleri <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, ve <xref:System.Net.Http.WebRequestHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7b052-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="7b052-121">Bazı genel yöntemleri <xref:System.Net.WebSockets.ClientWebSocket> ve <xref:System.Net.WebSockets.WebSocket> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7b052-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="7b052-122">Aşağıdaki tabloda listelenen öznitelikler, izleme çıkışını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7b052-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="7b052-123">Öznitelik adı</span><span class="sxs-lookup"><span data-stu-id="7b052-123">Attribute name</span></span>|<span data-ttu-id="7b052-124">Öznitelik değeri</span><span class="sxs-lookup"><span data-stu-id="7b052-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="7b052-125">Gerekli <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7b052-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="7b052-126">Çıkışın ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7b052-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="7b052-127">Meşru değerler `Critical`, `Error`, `Verbose`, `Warning`, ve `Information`.</span><span class="sxs-lookup"><span data-stu-id="7b052-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="7b052-128">Bu özniteliği ayarlanmalıdır \<adı Ekle > öğesinin \<anahtarlar > örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="7b052-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="7b052-129">Şirket bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b052-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="7b052-130">İsteğe bağlı <xref:System.Int32> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7b052-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="7b052-131">Her satır izlemesinde yer alan ağ verilerinin en fazla bayt sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7b052-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="7b052-132">Varsayılan değer 1024'tür.</span><span class="sxs-lookup"><span data-stu-id="7b052-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="7b052-133">Bu öznitelik ayarlanmalıdır \<kaynak > örnekte gösterilen şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b052-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="7b052-134">Altındaki bir öğede bu öznitelik ayarlanırsa bir özel durum \<anahtarlar > öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b052-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="7b052-135">İsteğe bağlı <xref:System.String> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7b052-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="7b052-136">Kümesine `includehex` protokol izlemelerini onaltılık ve metin biçiminde göstermek için.</span><span class="sxs-lookup"><span data-stu-id="7b052-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="7b052-137">Kümesine `protocolonly` yalnızca metin göstermek için.</span><span class="sxs-lookup"><span data-stu-id="7b052-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="7b052-138">Varsayılan değer `includehex` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="7b052-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="7b052-139">Bu öznitelik ayarlanmalıdır \<anahtarlar > örnekte gösterilen şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b052-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="7b052-140">Altındaki bir öğede bu öznitelik ayarlanırsa bir özel durum \<kaynak > öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b052-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b052-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b052-141">See also</span></span>
- [<span data-ttu-id="7b052-142">Ağ İzlemeyi Yorumlama</span><span class="sxs-lookup"><span data-stu-id="7b052-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [<span data-ttu-id="7b052-143">.NET Framework'te Ağ İzleme</span><span class="sxs-lookup"><span data-stu-id="7b052-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)
- [<span data-ttu-id="7b052-144">Ağ İzlemeyi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7b052-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [<span data-ttu-id="7b052-145">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7b052-145">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
