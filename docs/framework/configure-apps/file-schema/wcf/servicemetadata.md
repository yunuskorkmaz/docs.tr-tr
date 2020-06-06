---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201780"
---
# \<serviceMetadata>
<span data-ttu-id="dcef6-101">Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-101">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="dcef6-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcef6-102">Syntax</span></span>  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcef6-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcef6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="dcef6-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcef6-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dcef6-105">Attributes</span></span>  
  
|<span data-ttu-id="dcef6-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dcef6-106">Attribute</span></span>|<span data-ttu-id="dcef6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcef6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcef6-108">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="dcef6-108">externalMetadataLocation</span></span>|<span data-ttu-id="dcef6-109">Otomatik olarak oluşturulan WSDL yerine WSDL ve MEX isteklerine yanıt olarak döndürülen WSDL dosyasının konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="dcef6-109">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="dcef6-110">Bu öznitelik ayarlanmamışsa varsayılan WSDL döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dcef6-110">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="dcef6-111">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-111">The default is an empty string.</span></span>|  
|<span data-ttu-id="dcef6-112">Bilgilerinie başvuran HttpGetBinding</span><span class="sxs-lookup"><span data-stu-id="dcef6-112">httpGetBinding</span></span>|<span data-ttu-id="dcef6-113">HTTP GET aracılığıyla meta veri alımı için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dcef6-113">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="dcef6-114">Bu ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-114">This setting is optional.</span></span> <span data-ttu-id="dcef6-115">Belirtilmemişse, varsayılan bağlamalar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-115">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="dcef6-116">Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-116">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="dcef6-117">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcef6-117">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="dcef6-118">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dcef6-118">httpGetBindingConfiguration</span></span>|<span data-ttu-id="dcef6-119">`httpGetBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlamanın adını ayarlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="dcef6-119">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="dcef6-120">Bölümünde aynı ad tanımlanmalıdır `<bindings>` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-120">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="dcef6-121">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="dcef6-121">httpGetEnabled</span></span>|<span data-ttu-id="dcef6-122">Bir HTTP/GET isteği kullanılarak alma için hizmet meta verilerinin yayınlanıp yayınlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="dcef6-122">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="dcef6-123">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="dcef6-123">The default is `false`.</span></span><br /><br /> <span data-ttu-id="dcef6-124">HttpGetUrl özniteliği belirtilmemişse, meta verilerin yayımlandığı adres hizmet adresi artı "? wsdl" dir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-124">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="dcef6-125">Örneğin, hizmet adresi ise `http://localhost:8080/CalculatorService` , http/get meta veri adresi olur `http://localhost:8080/CalculatorService?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-125">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="dcef6-126">Bu özellik ise `false` veya hizmetin adresı http veya https tabanlı değilse, "? wsdl" yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-126">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="dcef6-127">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="dcef6-127">httpGetUrl</span></span>|<span data-ttu-id="dcef6-128">Bir HTTP/GET isteği kullanılarak alınması için meta verilerin yayımlanacağı adresi belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="dcef6-128">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="dcef6-129">Göreli bir URI belirtilmişse, hizmetin temel adresine göreli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-129">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="dcef6-130">Bilgilerinie başvuran HttpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="dcef6-130">httpsGetBinding</span></span>|<span data-ttu-id="dcef6-131">HTTPS GET aracılığıyla meta veri alımı için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dcef6-131">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="dcef6-132">Bu ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-132">This setting is optional.</span></span> <span data-ttu-id="dcef6-133">Belirtilmemişse, varsayılan bağlamalar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-133">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="dcef6-134">Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-134">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="dcef6-135">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcef6-135">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="dcef6-136">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dcef6-136">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="dcef6-137">`httpsGetBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlamanın adını ayarlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="dcef6-137">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="dcef6-138">Bölümünde aynı ad tanımlanmalıdır `<bindings>` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-138">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="dcef6-139">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="dcef6-139">httpsGetEnabled</span></span>|<span data-ttu-id="dcef6-140">Bir HTTPS/GET isteği kullanılarak alma için hizmet meta verilerinin yayınlanıp yayınlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="dcef6-140">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="dcef6-141">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="dcef6-141">The default is `false`.</span></span><br /><br /> <span data-ttu-id="dcef6-142">HttpsGetUrl özniteliği belirtilmemişse, meta verilerin yayımlandığı adres, hizmet adresi artı bir "? wsdl" dir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-142">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="dcef6-143">Örneğin, hizmet adresi " https://localhost:8080/CalculatorService " ise, http/get meta veri adresi " https://localhost:8080/CalculatorService?wsdl " olur.</span><span class="sxs-lookup"><span data-stu-id="dcef6-143">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="dcef6-144">Bu özellik ise `false` veya hizmetin adresı http veya https tabanlı değilse, "? wsdl" yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-144">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="dcef6-145">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="dcef6-145">httpsGetUrl</span></span>|<span data-ttu-id="dcef6-146">Bir HTTPS/GET isteği kullanılarak almak için meta verilerin yayımlanacağı adresi belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="dcef6-146">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="dcef6-147">policyVersion</span><span class="sxs-lookup"><span data-stu-id="dcef6-147">policyVersion</span></span>|<span data-ttu-id="dcef6-148">Kullanılan WS-Policy belirtiminin sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dcef6-148">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="dcef6-149">Bu öznitelik türü <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="dcef6-149">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcef6-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcef6-150">Child Elements</span></span>  
 <span data-ttu-id="dcef6-151">Yok</span><span class="sxs-lookup"><span data-stu-id="dcef6-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcef6-152">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcef6-152">Parent Elements</span></span>  
  
|<span data-ttu-id="dcef6-153">Öğe</span><span class="sxs-lookup"><span data-stu-id="dcef6-153">Element</span></span>|<span data-ttu-id="dcef6-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcef6-154">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dcef6-155">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-155">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcef6-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcef6-156">Remarks</span></span>  
 <span data-ttu-id="dcef6-157">Bu yapılandırma öğesi, bir hizmetin meta veri yayımlama özelliklerini denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-157">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="dcef6-158">Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-158">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="dcef6-159">Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dcef6-159">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="dcef6-160">Bu yapılandırma öğesini kullanarak hizmetiniz için bu yayımlama davranışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcef6-160">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="dcef6-161">Bu davranışı yapılandırmanın ayrıntılı bir örneği için bkz. [meta veri yayımlama davranışı](../../../wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="dcef6-161">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="dcef6-162">İsteğe bağlı `httpGetBinding` ve `httpsGetBinding` ÖZNITELIKLERI, http get (veya https Get) aracılığıyla meta veri alımı için kullanılan bağlamaları yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-162">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="dcef6-163">Bu değerler belirtilmemişse, varsayılan bağlamalar ( `HttpTransportBindingElement` http durumunda ve `HttpsTransportBindingElement` https durumunda), uygun şekilde meta veri alımı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-163">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="dcef6-164">Bu öznitelikleri yerleşik WCF bağlamaları ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dcef6-164">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="dcef6-165">Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-165">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="dcef6-166">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .</span><span class="sxs-lookup"><span data-stu-id="dcef6-166">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="dcef6-167">Bir hizmetin kötü amaçlı kullanıcılara maruz kalmasını azaltmak için, HTTP (HTTPS) üzerinden SSL (HTTPS) mekanizmasını kullanarak aktarımı güvenli hale getirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="dcef6-167">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="dcef6-168">Bunu yapmak için, önce uygun bir X. 509.952 sertifikasını hizmeti barındıran bilgisayardaki belirli bir bağlantı noktasına bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dcef6-168">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="dcef6-169">(Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).) İkinci olarak, bu öğeyi hizmet yapılandırmasına ekleyin ve `httpsGetEnabled` özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-169">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="dcef6-170">Son olarak, `httpsGetUrl` Aşağıdaki örnekte gösterildiği gibi, özniteliğini hizmet meta veri uç noktasının URL 'si olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dcef6-170">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a><span data-ttu-id="dcef6-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcef6-171">Example</span></span>  
 <span data-ttu-id="dcef6-172">Aşağıdaki örnek, öğesini kullanarak meta verileri açığa çıkarmak için bir hizmet yapılandırır \<serviceMetadata> .</span><span class="sxs-lookup"><span data-stu-id="dcef6-172">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="dcef6-173">Ayrıca, bir uç noktasını bir `IMetadataExchange` WS-MetadataExchange (MEX) protokolünün bir uygulama olarak kullanıma sunmak için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="dcef6-173">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="dcef6-174">Örnek, `mexHttpBinding` `wsHttpBinding` güvenlik modu olarak ayarlanmış olan öğesine eşdeğer bir standart bağlama olan öğesini kullanır `None` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-174">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="dcef6-175">Uç noktada "mex" göreli adresi kullanılır. bu durum, hizmet tabanı adresine karşı çözümlenirse, bir uç nokta adresinde oluşur `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="dcef6-175">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="dcef6-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcef6-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="dcef6-177">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="dcef6-177">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dcef6-178">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="dcef6-178">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
