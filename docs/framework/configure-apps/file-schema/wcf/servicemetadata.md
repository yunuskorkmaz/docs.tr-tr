---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4e88c6e5f03cef83e640fbca7434d10f82653f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="26fec-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="26fec-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="26fec-103">Hizmet meta verilerini ve ilişkili bilgileri yayımlanmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26fec-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="26fec-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="26fec-104">\<system.serviceModel></span></span>  
<span data-ttu-id="26fec-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="26fec-105">\<behaviors></span></span>  
<span data-ttu-id="26fec-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="26fec-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="26fec-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="26fec-107">\<behavior></span></span>  
<span data-ttu-id="26fec-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="26fec-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26fec-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26fec-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26fec-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26fec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="26fec-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26fec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26fec-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26fec-112">Attributes</span></span>  
  
|<span data-ttu-id="26fec-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26fec-113">Attribute</span></span>|<span data-ttu-id="26fec-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26fec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26fec-115">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="26fec-115">externalMetadataLocation</span></span>|<span data-ttu-id="26fec-116">Kullanıcıya otomatik olarak oluşturulan WSDL yerine WSDL ve MEX isteklerine yanıt olarak döndürülen bir WSDL dosya konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="26fec-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="26fec-117">Bu öznitelik ayarlandığında, varsayılan WSDL döndürülür.</span><span class="sxs-lookup"><span data-stu-id="26fec-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="26fec-118">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="26fec-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="26fec-119">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="26fec-119">httpGetBinding</span></span>|<span data-ttu-id="26fec-120">HTTP GET üzerinden meta veri alma işlemi için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="26fec-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="26fec-121">Bu ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26fec-121">This setting is optional.</span></span> <span data-ttu-id="26fec-122">Belirtilmezse, varsayılan bağlamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26fec-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="26fec-123">Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="26fec-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="26fec-124">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="26fec-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="26fec-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="26fec-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="26fec-126">Belirtilen bağlama adını ayarlar bir dize `httpGetBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği.</span><span class="sxs-lookup"><span data-stu-id="26fec-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="26fec-127">Aynı adı tanımlanmalıdır `<bindings>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="26fec-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="26fec-128">De</span><span class="sxs-lookup"><span data-stu-id="26fec-128">httpGetEnabled</span></span>|<span data-ttu-id="26fec-129">Hizmet meta verileri kullanarak bir HTTP/Get isteği alma için yayımlama belirtir bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="26fec-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="26fec-130">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="26fec-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="26fec-131">HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlandığında hizmet adresi adresidir artı bir "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="26fec-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="26fec-132">Örneğin, hizmet adresi "http://localhost: 8080/CalculatorService" HTTP/Get meta veri adresi ise, "http://localhost: 8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="26fec-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="26fec-133">Bu özellik ise `false`, veya hizmetinin adresini HTTP veya HTTPS bağlı değil "? wsdl" göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="26fec-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="26fec-134">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="26fec-134">httpGetUrl</span></span>|<span data-ttu-id="26fec-135">Meta verileri kullanarak bir HTTP/Get isteği alma için yayımlanan adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="26fec-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="26fec-136">Göreli URI onu işleneceğini hizmetin taban adresi gibi göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="26fec-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="26fec-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="26fec-137">httpsGetBinding</span></span>|<span data-ttu-id="26fec-138">HTTPS alma yoluyla meta veri alma işlemi için kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="26fec-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="26fec-139">Bu ayar isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26fec-139">This setting is optional.</span></span> <span data-ttu-id="26fec-140">Belirtilmezse, varsayılan bağlamaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26fec-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="26fec-141">Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="26fec-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="26fec-142">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="26fec-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="26fec-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="26fec-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="26fec-144">Belirtilen bağlama adını ayarlar bir dize `httpsGetBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği.</span><span class="sxs-lookup"><span data-stu-id="26fec-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="26fec-145">Aynı adı tanımlanmalıdır `<bindings>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="26fec-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="26fec-146">De</span><span class="sxs-lookup"><span data-stu-id="26fec-146">httpsGetEnabled</span></span>|<span data-ttu-id="26fec-147">Hizmet meta verileri kullanarak bir HTTPS/Get isteği alma için yayımlama belirtir bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="26fec-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="26fec-148">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="26fec-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="26fec-149">HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlandığında hizmet adresi adresidir artı bir "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="26fec-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="26fec-150">Örneğin, hizmet adresi "https://localhost:8080/CalculatorService" HTTP/Get meta veri adresi ise, "https://localhost:8080/CalculatorService? wsdl".</span><span class="sxs-lookup"><span data-stu-id="26fec-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="26fec-151">Bu özellik ise `false`, veya hizmetinin adresini HTTP veya HTTPS bağlı değil "? wsdl" göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="26fec-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="26fec-152">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="26fec-152">httpsGetUrl</span></span>|<span data-ttu-id="26fec-153">Meta verileri kullanarak bir HTTPS/Get isteği alma için yayımlanan adresini belirtir URI.</span><span class="sxs-lookup"><span data-stu-id="26fec-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="26fec-154">PolicyVersion</span><span class="sxs-lookup"><span data-stu-id="26fec-154">policyVersion</span></span>|<span data-ttu-id="26fec-155">Kullanılan WS-Policy belirtimi sürümünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="26fec-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="26fec-156">Bu öznitelik türünde <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="26fec-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26fec-157">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26fec-157">Child Elements</span></span>  
 <span data-ttu-id="26fec-158">Yok.</span><span class="sxs-lookup"><span data-stu-id="26fec-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26fec-159">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26fec-159">Parent Elements</span></span>  
  
|<span data-ttu-id="26fec-160">Öğe</span><span class="sxs-lookup"><span data-stu-id="26fec-160">Element</span></span>|<span data-ttu-id="26fec-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26fec-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26fec-162">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="26fec-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="26fec-163">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="26fec-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26fec-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26fec-164">Remarks</span></span>  
 <span data-ttu-id="26fec-165">Bu yapılandırma öğesi, bir hizmetin meta veri yayımlama özelliklerini denetlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26fec-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="26fec-166">Olası hassas hizmeti meta verileri, için varsayılan yapılandırma, yanlışlıkla açığa çıkmasını önlemek amacıyla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri, meta veri yayımlama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="26fec-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="26fec-167">Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe.</span><span class="sxs-lookup"><span data-stu-id="26fec-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="26fec-168">Bu yapılandırma öğesini kullanarak, bu yayımlama davranışı hizmetiniz için etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26fec-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="26fec-169">Bu davranış yapılandırma ayrıntılı örnek için bkz: [meta veri yayımlama davranışı](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="26fec-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="26fec-170">İsteğe bağlı `httpGetBinding` ve `httpsGetBinding` öznitelikleri HTTP GET (veya HTTPS Al) aracılığıyla meta veri alma işlemi için kullanılan bağlamaları yapılandırma izin verir.</span><span class="sxs-lookup"><span data-stu-id="26fec-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="26fec-171">Bunlar belirtilmezse, varsayılan bağlamaları (`HttpTransportBindingElement`, HTTP söz konusu olduğunda ve `HttpsTransportBindingElement`, HTTPS söz konusu olduğunda) uygun şekilde meta veri alma işlemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26fec-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="26fec-172">Bu öznitelikler yerleşik WCF bağlamalarla kullanamazsınız dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="26fec-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="26fec-173">Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir.</span><span class="sxs-lookup"><span data-stu-id="26fec-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="26fec-174">Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="26fec-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="26fec-175">Kötü niyetli kullanıcılar için bir hizmet riskini azaltmak için Güvenli HTTP (HTTPS) mekanizması üzerinde SSL kullanılarak aktarım mümkündür.</span><span class="sxs-lookup"><span data-stu-id="26fec-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="26fec-176">Bunu yapmak için önce uygun bir X.509 sertifikası hizmetini barındıran bilgisayarda belirli bir bağlantı noktası bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26fec-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="26fec-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, hizmet yapılandırması için bu öğe ekleyin ve ayarlayın `httpsGetEnabled` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="26fec-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="26fec-178">Son olarak, ayarlamak `httpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri uç noktasının URL'sini özniteliği.</span><span class="sxs-lookup"><span data-stu-id="26fec-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="26fec-179">Örnek</span><span class="sxs-lookup"><span data-stu-id="26fec-179">Example</span></span>  
 <span data-ttu-id="26fec-180">Aşağıdaki örnek yapılandırma meta verileri kullanarak kullanıma sunmak için bir hizmet \<serviceMetadata > öğesi.</span><span class="sxs-lookup"><span data-stu-id="26fec-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="26fec-181">Kullanıma sunmak için bir uç nokta da yapılandırır `IMetadataExchange` WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme.</span><span class="sxs-lookup"><span data-stu-id="26fec-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="26fec-182">Örnek kullanır `mexHttpBinding`, kolaylık sağlamak amacıyla bağlaması standart olduğu eşdeğerdir `wsHttpBinding` kümesine güvenlik moduyla `None`.</span><span class="sxs-lookup"><span data-stu-id="26fec-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="26fec-183">"Mex" göreli adresidir kullanılan uç, hangi olduğunda çözülmüş temel Hizmetleri karşı adresi bir uç nokta adresi http://localhost/servicemodelsamples/service.svc/mex sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="26fec-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
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
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26fec-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26fec-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="26fec-185">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="26fec-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="26fec-186">Meta veri yayımlama davranışı</span><span class="sxs-lookup"><span data-stu-id="26fec-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
