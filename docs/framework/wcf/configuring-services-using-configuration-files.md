---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 68b427a81104d0f5102915002025103ef8d35dc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928587"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="2e5cf-102">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2e5cf-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="2e5cf-103">Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyası ile yapılandırmak, dağıtım noktasında, tasarım zamanında değil, uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="2e5cf-104">Bu konu başlığı altında sunulan birincil teknikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="2e5cf-105">WCF hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="2e5cf-106">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web. config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="2e5cf-107">Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="2e5cf-108">Ayrıca, WCF, bir hizmet için en temel özellikleri hızlıca seçmenizi sağlayan, sistem tarafından sunulan çeşitli öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="2e5cf-109">İle [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]başlayarak, WCF, WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="2e5cf-110">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı, hizmetinizi bazı standart uç noktalarla ve varsayılan bağlama/davranışla otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="2e5cf-111">Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="2e5cf-112">Daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2e5cf-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="2e5cf-113">En yaygın kullanılan öğelerin listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="2e5cf-113">For a list of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="2e5cf-114">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2e5cf-115">Bir hizmetin iki farklı sürümünün dağıtıldığı yan yana senaryolar dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="2e5cf-116">Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümleri arasında paylaşılmaları ve .NET Framework farklı sürümlerinde çalışıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="2e5cf-117">System. Configuration: Web. config ve App. config</span><span class="sxs-lookup"><span data-stu-id="2e5cf-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="2e5cf-118">WCF .NET Framework System. Configuration yapılandırma sistemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2e5cf-119">Bir hizmeti Visual Studio 'da yapılandırırken, ayarları belirtmek için bir Web. config dosyası ya da bir App. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="2e5cf-120">Yapılandırma dosyası adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="2e5cf-121">Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="2e5cf-122">Başka bir barındırma ortamı kullanıyorsanız, bir App. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="2e5cf-123">Visual Studio 'da, son yapılandırma dosyasını oluşturmak için App. config adlı dosya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="2e5cf-124">Yapılandırma için gerçekten kullanılan son ad, derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="2e5cf-125">Örneğin, "Cohowınara. exe" adlı bir derlemenin son yapılandırma dosyası adı "Cohowınara. exe. config" vardır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="2e5cf-126">Ancak, yalnızca App. config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="2e5cf-127">Bu dosyada yapılan değişiklikler derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="2e5cf-128">App. config dosyasını kullanarak, yapılandırma sistemi App. config dosyasını, uygulama başladığında ve yapılandırma uygulandığında Machine. config dosyasının içeriğiyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="2e5cf-129">Bu mekanizma, Machine. config dosyasında makine genelindeki ayarların tanımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="2e5cf-130">Machine. config dosyasının ayarlarını geçersiz kılmak için App. config dosyası kullanılabilir; Ayrıca, Machine. config dosyasındaki ayarları, kullanıldıkları şekilde de kilitle.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="2e5cf-131">Web. config durumunda, yapılandırma sistemi tüm dizinlerde Web. config dosyalarını, uygulanan yapılandırma ile uygulama dizinine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="2e5cf-132">Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi için bkz. <xref:System.Configuration> ad alanındaki konular.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="2e5cf-133">Yapılandırma dosyasının ana bölümleri</span><span class="sxs-lookup"><span data-stu-id="2e5cf-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="2e5cf-134">Yapılandırma dosyasındaki ana bölümler aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="2e5cf-135">Bağlamalar ve davranışlar bölümleri isteğe bağlıdır ve yalnızca gerekli olduğunda dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="2e5cf-136">\<Hizmetler > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-136">The \<services> Element</span></span>  
 <span data-ttu-id="2e5cf-137">`services` Öğesi, uygulamanın barındırdığı tüm hizmetlere ilişkin belirtimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="2e5cf-138">' Deki [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]Basitleştirilmiş yapılandırma modeliyle başlayarak, bu bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="2e5cf-139">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="2e5cf-140">\<Service > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-140">The \<service> Element</span></span>  
 <span data-ttu-id="2e5cf-141">Her hizmet şu özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="2e5cf-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-142">`name`.</span></span> <span data-ttu-id="2e5cf-143">Hizmet sözleşmesinin bir uygulamasını sağlayan türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="2e5cf-144">Bu, ad alanı, nokta ve daha sonra tür adından oluşan tam nitelikli bir addır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="2e5cf-145">Örneğin `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="2e5cf-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="2e5cf-147">Öğesinde`behaviors` bulunan `behavior` öğelerden birinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="2e5cf-148">Belirtilen davranış, hizmetin kimliğe bürünmeye izin verip etmeyeceğini gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="2e5cf-149">Değeri boş bir ad ise veya Hayır `behaviorConfiguration` sağlanmazsa, varsayılan hizmet davranışı kümesi hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="2e5cf-150">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="2e5cf-151">\<Uç nokta > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="2e5cf-152">Her uç nokta, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve bir sözleşme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="2e5cf-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-153">`address`.</span></span> <span data-ttu-id="2e5cf-154">Hizmetin temel adresine göreli olarak verilen mutlak bir adres veya hizmet olan Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="2e5cf-155">Boş bir dizeye ayarlanırsa, uç noktanın hizmet <xref:System.ServiceModel.ServiceHost> için oluşturulurken belirtilen temel adreste kullanılabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="2e5cf-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-156">`binding`.</span></span> <span data-ttu-id="2e5cf-157">Genellikle gibi <xref:System.ServiceModel.WSHttpBinding>sistem tarafından sağlanmış bir bağlamayı belirtir, ancak kullanıcı tanımlı bağlamayı da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="2e5cf-158">Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, işlemlerin veya akışın desteklenip desteklenmediğini ya da etkin olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="2e5cf-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-159">`bindingConfiguration`.</span></span> <span data-ttu-id="2e5cf-160">Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu, `binding` `bindings` öğesinde uygun öğe yapılandırılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="2e5cf-161">Bu özniteliğe, varsayılan değerleri değiştirmek için kullanılan `name` `binding` öğesinin özniteliğiyle aynı değer verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="2e5cf-162">Hiçbir ad verilmezse veya bağlamada hiçbir `bindingConfiguration` değer belirtilmemişse, bağlantı türü için varsayılan bağlama uç noktada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="2e5cf-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-163">`contract`.</span></span> <span data-ttu-id="2e5cf-164">Sözleşmeyi tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="2e5cf-165">Bu, `name` `service` öğesinin özniteliği tarafından belirtilen ortak dil çalışma zamanı (CLR) türünde uygulanan arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="2e5cf-166">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="2e5cf-167">\<Bindings > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="2e5cf-168">Öğesi `bindings` , herhangi bir hizmette tanımlı herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="2e5cf-169">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="2e5cf-170">\<Bağlama > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-170">The \<binding> Element</span></span>  
 <span data-ttu-id="2e5cf-171">Öğesinde yer [](../../../docs/framework/wcf/extending/custom-bindings.md)alan öğeler, sistem tarafından belirtilen bağlamalardan biri olabilir ( [sistem tarafından belirtilen bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)görebilir) veya özel bir bağlama (bkz. özel bağlamalar). `binding` `bindings`</span><span class="sxs-lookup"><span data-stu-id="2e5cf-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="2e5cf-172">Öğesi, `bindingConfiguration` bağlamayı öğenin`endpoint` özniteliğinde belirtilen uç noktayla ilişkilendiren bir `name` özniteliğe sahiptir. `binding`</span><span class="sxs-lookup"><span data-stu-id="2e5cf-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="2e5cf-173">Ad belirtilmemişse, o bağlama o bağlama türünün varsayılan değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="2e5cf-174">Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="2e5cf-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="2e5cf-175">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="2e5cf-176">\<Davranışlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="2e5cf-177">Bu, bir hizmetin davranışlarını tanımlayan `behavior` öğeler için bir kapsayıcı öğesidir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="2e5cf-178">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="2e5cf-179">\<Davranış > öğesi</span><span class="sxs-lookup"><span data-stu-id="2e5cf-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="2e5cf-180">Her `behavior` öğe bir `name` öznitelik tarafından tanımlanır ve <`throttling`> ya da özel bir davranış gibi sistem tarafından sağlanan bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="2e5cf-181">Ad verilmezse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="2e5cf-182">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="2e5cf-183">Bağlama ve davranış yapılandırmalarının kullanımı</span><span class="sxs-lookup"><span data-stu-id="2e5cf-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="2e5cf-184">WCF, yapılandırmada bir başvuru sistemi kullanarak uç noktalar arasında yapılandırmaların paylaşılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="2e5cf-185">Yapılandırma değerlerini bir uç noktaya doğrudan atamak yerine, bağlama ilgili yapılandırma değerleri, `bindingConfiguration` `<binding>` bölümündeki öğelerde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="2e5cf-186">Bağlama yapılandırması, bağlamada adlandırılmış bir ayar grubudur.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="2e5cf-187">Uç noktalar daha sonra adına `bindingConfiguration` göre başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2e5cf-188">`name` Öğesiöğesinde`<binding>` ayarlanır. `bindingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="2e5cf-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="2e5cf-189">Bağlama türünün kapsamı içinde benzersiz bir dize [\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) `name` olmalıdır — bu durumda < BasicHttpBinding veya varsayılan bağlamaya başvuracak boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="2e5cf-190">Uç nokta, `bindingConfiguration` özniteliğini bu dizeye ayarlayarak yapılandırmaya bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="2e5cf-191">`behaviorConfiguration` , Aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2e5cf-192">Varsayılan hizmet davranışı kümesinin hizmete eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="2e5cf-193">Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaların paylaşmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="2e5cf-194">Makine genelindeki kapsam gerekliyse, Machine. config içinde bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App. config dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="2e5cf-195">[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) , yapılandırmaların oluşturulmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="2e5cf-196">Davranış birleştirme</span><span class="sxs-lookup"><span data-stu-id="2e5cf-196">Behavior Merge</span></span>  
 <span data-ttu-id="2e5cf-197">Davranış birleştirme özelliği, bir dizi ortak davranışın sürekli olarak kullanılmasını istediğinizde davranışları yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="2e5cf-198">Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışlar belirtmenizi sağlar ve hizmetlerin, yapılandırma hiyerarşisinin birden fazla düzeyinden davranışları devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="2e5cf-199">Bunun nasıl çalıştığını görmek için, IIS 'de aşağıdaki sanal dizin düzenine sahip olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="2e5cf-200">`~\Web.config` Ve dosyanız aşağıdaki içeriğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-200">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2e5cf-201">Ve şu içeriklerle ~ \Child\Web.config konumunda bulunan bir alt Web. config dosyası vardır:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2e5cf-202">~ \Child\service.exe konumunda bulunan hizmet, hem serviceDebug hem de serviceMetadata davranışlarına sahip olsa da çalışır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="2e5cf-203">~ \Service.exe yolunda bulunan hizmette yalnızca serviceDebug davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="2e5cf-204">Ne olacağı, aynı ada sahip iki davranış koleksiyonunun (Bu durumda boş dize) birleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="2e5cf-205">Ayrıca, \< \<Remove > etiketini kullanarak, Clear > etiketini kullanarak ve tek davranışları koleksiyondan kaldırarak davranış koleksiyonlarını temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="2e5cf-206">Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca serviceMetadata davranışına sahip olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="2e5cf-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2e5cf-207">Davranış birleştirme yukarıda ve adlandırılmış davranış koleksiyonları da gösterildiği gibi adsız davranış koleksiyonları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="2e5cf-208">Davranış birleştirme, Web. config dosyalarının kök Web. config dosyası ve Machine. config ile hiyerarşik olarak birleştirileyeceği IIS barındırma ortamında çalışmaktadır. Ancak bu, Machine. config 'in App. config dosyasıyla birleştirilebileceği uygulama ortamında da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="2e5cf-209">Davranış birleştirme, yapılandırma içindeki uç nokta davranışları ve hizmet davranışları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="2e5cf-210">Bir alt davranış koleksiyonu, üst davranış koleksiyonunda zaten bulunan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="2e5cf-211">Bu nedenle `<serviceMetadata httpGetEnabled="True" />`, bir üst davranış koleksiyonu `<serviceMetadata httpGetEnabled="False" />` ve bir alt davranış koleksiyonu varsa, alt davranış davranış koleksiyonundaki üst davranışı geçersiz kılar ve HttpGetEnabled "true" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e5cf-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e5cf-212">See also</span></span>

- [<span data-ttu-id="2e5cf-213">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2e5cf-213">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="2e5cf-214">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2e5cf-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="2e5cf-215">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-215">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="2e5cf-216">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2e5cf-216">\<binding></span></span>](../../../docs/framework/misc/binding.md)
