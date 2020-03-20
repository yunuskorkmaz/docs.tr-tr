---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174803"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="ba6a9-102">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba6a9-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="ba6a9-103">Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyasıyla yapılandırmak, tasarım zamanında değil, dağıtım noktasında uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="ba6a9-104">Bu konu, kullanılabilir birincil teknikleri özetliyor.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="ba6a9-105">Bir WCF hizmeti .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="ba6a9-106">En yaygın olarak, Bir WCF hizmeti barındıran bir Internet Information Services (IIS) sitesi için Web.config dosyasına XML öğeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="ba6a9-107">Öğeler, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları makine bazında değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="ba6a9-108">Buna ek olarak, WCF hızlı bir hizmet için en temel özellikleri seçmek için izin birkaç sistem sağlanan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="ba6a9-109">.NET Framework 4 ile başlayan WCF, WCF yapılandırma gereksinimlerini basitleştiren yeni bir varsayılan yapılandırma modeliyle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="ba6a9-110">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma süresi hizmetinizi otomatik olarak bazı standart uç noktalar ve varsayılan bağlama/davranışla yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="ba6a9-111">Uygulamada, yapılandırma yazma WCF uygulamaları programlama önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="ba6a9-112">Daha fazla bilgi için, [Hizmetler için Bağlamaları Yapılandırma'ya](configuring-bindings-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="ba6a9-113">En sık kullanılan öğelerin listesi için [Sistem Tarafından Sağlanan Bağlamalar](system-provided-bindings.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="ba6a9-114">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ba6a9-115">Bir hizmetin iki farklı sürümü dağıtılan yan yana senaryoları dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="ba6a9-116">Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümlerinde paylaşılması ve .NET Framework'ün farklı sürümleri altında çalışıyor olmalarıdır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="ba6a9-117">System.Configuration: Web.config ve App.config</span><span class="sxs-lookup"><span data-stu-id="ba6a9-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="ba6a9-118">WCF,.NET Framework'ün System.Configuration yapılandırma sistemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ba6a9-119">Visual Studio'da bir hizmeti yapılandırırken, ayarları belirtmek için bir Web.config dosyası veya App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="ba6a9-120">Yapılandırma dosya adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="ba6a9-121">Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="ba6a9-122">Başka bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="ba6a9-123">Visual Studio'da, App.config adlı dosya son yapılandırma dosyasını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="ba6a9-124">Yapılandırma için kullanılan son ad derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="ba6a9-125">Örneğin, "Cohowinery.exe" adlı bir derlemenin "Cohowinery.exe.config" son yapılandırma dosya adı vardır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="ba6a9-126">Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="ba6a9-127">Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="ba6a9-128">App.config kullanarak, yapılandırma sistemi uygulama başlatıldığında ve yapılandırma uygulandığında App.config dosyasını Machine.config dosyasının içeriğiyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="ba6a9-129">Bu mekanizma, Makine.config dosyasında makine genelinde ayarların tanımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="ba6a9-130">App.config dosyası Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; machine.config dosyasındaki ayarları da kilitleyebilir, böylece kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="ba6a9-131">Web.config durumunda, yapılandırma sistemi, uygulama dizinine giden tüm dizinlerde Web.config dosyalarını uygulanan yapılandırmayla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="ba6a9-132">Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi <xref:System.Configuration> için ad alanındaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="ba6a9-133">Yapılandırma Dosyasının Ana Bölümleri</span><span class="sxs-lookup"><span data-stu-id="ba6a9-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="ba6a9-134">Yapılandırma dosyasındaki ana bölümler aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="ba6a9-135">Bağlamalar ve davranışbölümleri isteğe bağlıdır ve yalnızca gerekirse dahildir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="ba6a9-136">\<Hizmetler> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-136">The \<services> Element</span></span>  
 <span data-ttu-id="ba6a9-137">Öğe, `services` uygulamanın barındırılacak tüm hizmetlerinin belirtimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="ba6a9-138">.NET Framework 4'teki basitleştirilmiş yapılandırma modelinden başlayarak bu bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-138">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [<span data-ttu-id="ba6a9-139">\<hizmetler></span><span class="sxs-lookup"><span data-stu-id="ba6a9-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="ba6a9-140">Hizmet \<> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-140">The \<service> Element</span></span>  
 <span data-ttu-id="ba6a9-141">Her hizmetin şu öznitelikleri vardır:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="ba6a9-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-142">`name`.</span></span> <span data-ttu-id="ba6a9-143">Hizmet sözleşmesinin uygulanmasını sağlayan türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="ba6a9-144">Bu, ad alanı, bir dönem ve daha sonra tür adı oluşan tam nitelikli bir addır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="ba6a9-145">Örneğin, `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="ba6a9-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="ba6a9-147">`behaviors` Öğede bulunan `behavior` öğelerden birinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="ba6a9-148">Belirtilen davranış, hizmetin kimliğe bürünme izin verip vermediği gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="ba6a9-149">Değeri boş adsa veya `behaviorConfiguration` hiç sağlanmışsa, varsayılan hizmet davranışı kümesi hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="ba6a9-150">\<hizmet></span><span class="sxs-lookup"><span data-stu-id="ba6a9-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="ba6a9-151">Bitiş \<Noktası> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="ba6a9-152">Her bitiş noktası, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve sözleşme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="ba6a9-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-153">`address`.</span></span> <span data-ttu-id="ba6a9-154">Hizmetin mutlak bir adres veya hizmetin temel adresine göre verilen tek düzen kaynak tanımlayıcısını (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="ba6a9-155">Boş bir dize olarak ayarlanırsa, hizmet için oluştururken belirtilen temel <xref:System.ServiceModel.ServiceHost> adreste bitiş noktasının kullanılabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="ba6a9-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-156">`binding`.</span></span> <span data-ttu-id="ba6a9-157">Genellikle, sistem tarafından sağlanan bir <xref:System.ServiceModel.WSHttpBinding>bağlama gibi belirtir, ancak kullanıcı tanımlı bir bağlama da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="ba6a9-158">Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, hareketlerin veya akışların desteklenip desteklenmediğini veya etkinleştirilip etkinleştirilemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="ba6a9-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-159">`bindingConfiguration`.</span></span> <span data-ttu-id="ba6a9-160">Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu `binding` `bindings` öğedeki uygun öğe yi yapılandırarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="ba6a9-161">Bu öznitelik, varsayılanları değiştirmek `name` için kullanılan `binding` öğenin özniteliği ile aynı değer verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="ba6a9-162">Hiçbir ad verilmezveya bağlamada belirtilmemişse, `bindingConfiguration` bitiş noktasında bağlama türünün varsayılan bağlaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="ba6a9-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-163">`contract`.</span></span> <span data-ttu-id="ba6a9-164">Sözleşmeyi tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="ba6a9-165">Bu, `service` öğenin özniteliği tarafından belirtilen ortak dil çalışma süresi `name` (CLR) türünde uygulanan arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="ba6a9-166">\<bitiş noktası></span><span class="sxs-lookup"><span data-stu-id="ba6a9-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="ba6a9-167">Bağlamalar \<> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="ba6a9-168">Öğe, `bindings` herhangi bir hizmette tanımlanan herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="ba6a9-169">\<></span><span class="sxs-lookup"><span data-stu-id="ba6a9-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="ba6a9-170">\<Bağlayıcı> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-170">The \<binding> Element</span></span>  
 <span data-ttu-id="ba6a9-171">Öğede bulunan `binding` öğeler, sistem tarafından sağlanan bağlamalardan biri [(bkz. Sistem Sağlanan Bağlamalar)](system-provided-bindings.md)veya özel bir bağlama olabilir (bkz. [Özel Bağlamalar).](./extending/custom-bindings.md) `bindings`</span><span class="sxs-lookup"><span data-stu-id="ba6a9-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="ba6a9-172">Öğe, `binding` öğenin özniteliği belirtilen `name` `bindingConfiguration` bitiş noktası ile bağlama ilişkilendiren bir `endpoint` öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="ba6a9-173">Hiçbir ad belirtilmemişse, bu bağlama bu bağlama türünün varsayılanına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="ba6a9-174">Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için [WCF hizmetlerini yapılandırma](configuring-services.md)ya da yapılandırma ya da geliştirme bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="ba6a9-175">\<bağlayıcı></span><span class="sxs-lookup"><span data-stu-id="ba6a9-175">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="ba6a9-176">> \<Davranışları</span><span class="sxs-lookup"><span data-stu-id="ba6a9-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="ba6a9-177">Bu, bir hizmetin `behavior` davranışlarını tanımlayan öğeler için bir kapsayıcı öğesidir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="ba6a9-178">\<davranışlar></span><span class="sxs-lookup"><span data-stu-id="ba6a9-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="ba6a9-179">Davranış \<> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ba6a9-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="ba6a9-180">Her `behavior` öğe bir `name` öznitelik tarafından tanımlanır ve <`throttling`> gibi sistem tarafından sağlanan bir davranış veya özel bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="ba6a9-181">Ad verilmezse, bu davranış öğesi varsayılan hizmete veya bitiş noktası davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="ba6a9-182">\<davranış></span><span class="sxs-lookup"><span data-stu-id="ba6a9-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="ba6a9-183">Bağlama ve Davranış Yapılandırmaları Nasıl Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="ba6a9-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="ba6a9-184">WCF yapılandırmada bir başvuru sistemi kullanarak son noktalar arasında yapılandırmaları paylaşmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="ba6a9-185">Yapılandırma değerlerini doğrudan bir uç noktaya atamak yerine, bağlamayla `bindingConfiguration` ilgili yapılandırma `<binding>` değerleri bölümdeki öğelerde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="ba6a9-186">Bağlayıcı yapılandırma, bağlama üzerinde adlandırılmış bir ayar grubudur.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="ba6a9-187">Uç noktalar daha `bindingConfiguration` sonra ada göre başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="ba6a9-188">Öğenin `name` `bindingConfiguration` kümesi öğede `<binding>` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="ba6a9-189">Bağlama `name` türü kapsamında benzersiz bir dize olmalıdır—bu durumda [<temelHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)veya varsayılan bağlama başvurmak için boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="ba6a9-190">Bitiş noktası, bu dize `bindingConfiguration` özniteliği ayarlayarak yapılandırmaya bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="ba6a9-191">A, `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="ba6a9-192">Varsayılan hizmet davranışı kümesinin hizmete eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="ba6a9-193">Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaları paylaşmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="ba6a9-194">Makine genelinde kapsam gerekiyorsa, Machine.config'de bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="ba6a9-195">[Configuration Editor Aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="ba6a9-196">Davranış Birleştirme</span><span class="sxs-lookup"><span data-stu-id="ba6a9-196">Behavior Merge</span></span>  
 <span data-ttu-id="ba6a9-197">Davranış birleştirme özelliği, ortak davranış lar kümesinin tutarlı bir şekilde kullanılmasını istediğinizde davranışların yönetilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="ba6a9-198">Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışları belirtmenize ve hizmetlerin yapılandırma hiyerarşisinin birden çok düzeyinden davranışları devralmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="ba6a9-199">Bu çalışmaların nasıl çalıştığını göstermek için IIS'de aşağıdaki sanal dizin düzenine sahip olduğunuzu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="ba6a9-200">Dosyanızda `~\Web.config` aşağıdaki içerikler vardır:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="ba6a9-201">Ve bir çocuk Web.config bulunan ~\Child\Web.config aşağıdaki içeriği ile:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="ba6a9-202">~\Child\Service.svc adresinde bulunan hizmet, hem hizmetDebug hem de serviceMetadata davranışlarına sahipmiş gibi davranacaktır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="ba6a9-203">~\Service.svc adresinde bulunan hizmet yalnızca hizmet Hata Ayıklama davranışına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="ba6a9-204">Ne olur, aynı ada sahip iki davranış koleksiyonları (bu durumda boş dize) birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="ba6a9-205">Ayrıca, açık> etiketini \<kullanarak davranış koleksiyonlarını temizleyebilir ve \<kaldırma> etiketini kullanarak tek tek davranışları koleksiyondan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="ba6a9-206">Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca hizmetMetaveri davranışına sahip olmasıyla sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="ba6a9-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="ba6a9-207">Davranış birleştirme, yukarıda gösterildiği gibi adsız davranış koleksiyonları için de yapılır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="ba6a9-208">Davranış birleştirme, Web.config dosyalarının root Web.config dosyası ve machine.config ile hiyerarşik olarak birleştiği IIS barındırma ortamında çalışır. Ama aynı zamanda uygulama ortamında çalışır, burada machine.config App.config dosyası ile birleşebilir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="ba6a9-209">Davranış birleştirme yapılandırmada hem uç nokta davranışları hem de hizmet davranışları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="ba6a9-210">Alt davranış koleksiyonu, üst davranış koleksiyonunda zaten mevcut olan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="ba6a9-211">Yani bir üst davranış `<serviceMetadata httpGetEnabled="False" />` koleksiyonu vardı ve `<serviceMetadata httpGetEnabled="True" />`bir alt davranış koleksiyonu vardı , alt davranış davranış koleksiyonunda üst davranışı geçersiz kılar ve httpGetEnabled "doğru" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6a9-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba6a9-212">See also</span></span>

- [<span data-ttu-id="ba6a9-213">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba6a9-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="ba6a9-214">WCF hizmetlerinin yapılandırılması</span><span class="sxs-lookup"><span data-stu-id="ba6a9-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="ba6a9-215">\<hizmet></span><span class="sxs-lookup"><span data-stu-id="ba6a9-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="ba6a9-216">\<bağlayıcı></span><span class="sxs-lookup"><span data-stu-id="ba6a9-216">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)
