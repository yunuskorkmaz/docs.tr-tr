---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 29792726567373c907898cf6ced9891577f11588
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141634"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="3a5c4-102">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3a5c4-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="3a5c4-103">Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyası ile yapılandırmak, dağıtım noktasında, tasarım zamanında değil, uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="3a5c4-104">Bu konu başlığı altında sunulan birincil teknikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="3a5c4-105">WCF hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="3a5c4-106">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web. config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="3a5c4-107">Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="3a5c4-108">Ayrıca, WCF, bir hizmet için en temel özellikleri hızlıca seçmenizi sağlayan, sistem tarafından sunulan çeşitli öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="3a5c4-109">WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-109">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="3a5c4-110">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı, hizmetinizi bazı standart uç noktalarla ve varsayılan bağlama/davranışla otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="3a5c4-111">Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="3a5c4-112">Daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3a5c4-112">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="3a5c4-113">En yaygın kullanılan öğelerin listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3a5c4-113">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="3a5c4-114">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a5c4-115">Bir hizmetin iki farklı sürümünün dağıtıldığı yan yana senaryolar dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="3a5c4-116">Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümleri arasında paylaşılmaları ve .NET Framework farklı sürümlerinde çalışıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="3a5c4-117">System. Configuration: Web. config ve App. config</span><span class="sxs-lookup"><span data-stu-id="3a5c4-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="3a5c4-118">WCF .NET Framework System. Configuration yapılandırma sistemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3a5c4-119">Bir hizmeti Visual Studio 'da yapılandırırken, ayarları belirtmek için bir Web. config dosyası ya da bir App. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="3a5c4-120">Yapılandırma dosyası adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="3a5c4-121">Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="3a5c4-122">Başka bir barındırma ortamı kullanıyorsanız, bir App. config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="3a5c4-123">Visual Studio 'da, son yapılandırma dosyasını oluşturmak için App. config adlı dosya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="3a5c4-124">Yapılandırma için gerçekten kullanılan son ad, derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="3a5c4-125">Örneğin, "Cohowınara. exe" adlı bir derlemenin son yapılandırma dosyası adı "Cohowınara. exe. config" vardır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="3a5c4-126">Ancak, yalnızca App. config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="3a5c4-127">Bu dosyada yapılan değişiklikler derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="3a5c4-128">App. config dosyasını kullanarak, yapılandırma sistemi App. config dosyasını, uygulama başladığında ve yapılandırma uygulandığında Machine. config dosyasının içeriğiyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="3a5c4-129">Bu mekanizma, Machine. config dosyasında makine genelindeki ayarların tanımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="3a5c4-130">Machine. config dosyasının ayarlarını geçersiz kılmak için App. config dosyası kullanılabilir; Ayrıca, Machine. config dosyasındaki ayarları, kullanıldıkları şekilde de kilitle.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="3a5c4-131">Web. config durumunda, yapılandırma sistemi tüm dizinlerde Web. config dosyalarını, uygulanan yapılandırma ile uygulama dizinine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="3a5c4-132">Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi için, <xref:System.Configuration> ad alanındaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="3a5c4-133">Yapılandırma dosyasının ana bölümleri</span><span class="sxs-lookup"><span data-stu-id="3a5c4-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="3a5c4-134">Yapılandırma dosyasındaki ana bölümler aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="3a5c4-135">Bağlamalar ve davranışlar bölümleri isteğe bağlıdır ve yalnızca gerekli olduğunda dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="3a5c4-136">\<Services > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-136">The \<services> Element</span></span>  
 <span data-ttu-id="3a5c4-137">`services` öğesi, uygulamanın barındırdığı tüm hizmetlere ilişkin belirtimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="3a5c4-138">.NET Framework 4 ' te Basitleştirilmiş yapılandırma modeliyle başlayarak bu bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-138">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [<span data-ttu-id="3a5c4-139">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-139">\<services></span></span>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="3a5c4-140">\<Service > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-140">The \<service> Element</span></span>  
 <span data-ttu-id="3a5c4-141">Her hizmet şu özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="3a5c4-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-142">`name`.</span></span> <span data-ttu-id="3a5c4-143">Hizmet sözleşmesinin bir uygulamasını sağlayan türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="3a5c4-144">Bu, ad alanı, nokta ve daha sonra tür adından oluşan tam nitelikli bir addır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="3a5c4-145">Örneğin `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="3a5c4-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="3a5c4-147">`behaviors` öğesinde bulunan `behavior` öğelerinden birinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="3a5c4-148">Belirtilen davranış, hizmetin kimliğe bürünmeye izin verip etmeyeceğini gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="3a5c4-149">Değeri boş bir ad ise veya `behaviorConfiguration` sağlanmazsa, varsayılan hizmet davranışı kümesi hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="3a5c4-150">\<Hizmeti ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-150">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="3a5c4-151">\<uç noktası > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="3a5c4-152">Her uç nokta, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve bir sözleşme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="3a5c4-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-153">`address`.</span></span> <span data-ttu-id="3a5c4-154">Hizmetin temel adresine göreli olarak verilen mutlak bir adres veya hizmet olan Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="3a5c4-155">Boş bir dizeye ayarlanırsa, uç noktanın hizmet için <xref:System.ServiceModel.ServiceHost> oluşturulurken belirtilen temel adreste kullanılabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="3a5c4-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-156">`binding`.</span></span> <span data-ttu-id="3a5c4-157">Genellikle <xref:System.ServiceModel.WSHttpBinding>gibi sistem tarafından sağlanmış bir bağlamayı belirtir, ancak kullanıcı tanımlı bağlamayı da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="3a5c4-158">Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, işlemlerin veya akışın desteklenip desteklenmediğini ya da etkin olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="3a5c4-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-159">`bindingConfiguration`.</span></span> <span data-ttu-id="3a5c4-160">Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu, `bindings` öğesinde uygun `binding` öğesi yapılandırılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="3a5c4-161">Bu özniteliğe, varsayılan değerleri değiştirmek için kullanılan `binding` öğesinin `name` özniteliğiyle aynı değer verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="3a5c4-162">Hiçbir ad verilmezse veya bağlamada hiçbir `bindingConfiguration` belirtilmemişse, son noktada bağlama türünün varsayılan bağlaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="3a5c4-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-163">`contract`.</span></span> <span data-ttu-id="3a5c4-164">Sözleşmeyi tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="3a5c4-165">Bu, `service` öğesinin `name` özniteliği tarafından belirtilen ortak dil çalışma zamanı (CLR) türünde uygulanan arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="3a5c4-166">uç nokta > \<</span><span class="sxs-lookup"><span data-stu-id="3a5c4-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="3a5c4-167">\<bağlamaları > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="3a5c4-168">`bindings` öğesi, herhangi bir hizmette tanımlı herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="3a5c4-169">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-169">\<bindings></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="3a5c4-170">\<bağlama > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-170">The \<binding> Element</span></span>  
 <span data-ttu-id="3a5c4-171">`bindings` öğesinde bulunan `binding` öğeleri, sistem tarafından belirtilen bağlamalardan biri olabilir ( [sistem tarafından belirtilen bağlamaları](system-provided-bindings.md)görebilir) veya özel bir bağlama (bkz. [Özel Bağlamalar](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="3a5c4-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="3a5c4-172">`binding` öğesinde, bağlamayı `endpoint` öğesinin `bindingConfiguration` özniteliğinde belirtilen uç noktayla ilişkilendiren bir `name` özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="3a5c4-173">Ad belirtilmemişse, o bağlama o bağlama türünün varsayılan değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="3a5c4-174">Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="3a5c4-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="3a5c4-175">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="3a5c4-175">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="3a5c4-176">\<davranışlar > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="3a5c4-177">Bu, bir hizmetin davranışlarını tanımlayan `behavior` öğeleri için bir kapsayıcı öğesidir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="3a5c4-178">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-178">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="3a5c4-179">\<Behavior > öğesi</span><span class="sxs-lookup"><span data-stu-id="3a5c4-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="3a5c4-180">Her `behavior` öğesi bir `name` özniteliğiyle tanımlanır ve <`throttling`> veya özel bir davranış gibi sistem tarafından sağlanan bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="3a5c4-181">Ad verilmezse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="3a5c4-182">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-182">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="3a5c4-183">Bağlama ve davranış yapılandırmalarının kullanımı</span><span class="sxs-lookup"><span data-stu-id="3a5c4-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="3a5c4-184">WCF, yapılandırmada bir başvuru sistemi kullanarak uç noktalar arasında yapılandırmaların paylaşılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="3a5c4-185">Yapılandırma değerlerini bir uç noktaya doğrudan atamak yerine, bağlama ilgili yapılandırma değerleri `<binding>` bölümündeki `bindingConfiguration` öğelerinde gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="3a5c4-186">Bağlama yapılandırması, bağlamada adlandırılmış bir ayar grubudur.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="3a5c4-187">Uç noktalar daha sonra ada göre `bindingConfiguration` başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="3a5c4-188">`bindingConfiguration` `name` `<binding>` öğesinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="3a5c4-189">`name`, bağlama türünün kapsamı içinde benzersiz bir dize olmalıdır — bu durumda, [< basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)ya da varsayılan bağlamaya başvuracak boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="3a5c4-190">Uç nokta, `bindingConfiguration` özniteliğini bu dizeye ayarlayarak yapılandırmaya bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="3a5c4-191">`behaviorConfiguration`, aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="3a5c4-192">Varsayılan hizmet davranışı kümesinin hizmete eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="3a5c4-193">Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaların paylaşmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="3a5c4-194">Makine genelindeki kapsam gerekliyse, Machine. config içinde bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App. config dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="3a5c4-195">[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md) , yapılandırmaların oluşturulmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="3a5c4-196">Davranış birleştirme</span><span class="sxs-lookup"><span data-stu-id="3a5c4-196">Behavior Merge</span></span>  
 <span data-ttu-id="3a5c4-197">Davranış birleştirme özelliği, bir dizi ortak davranışın sürekli olarak kullanılmasını istediğinizde davranışları yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="3a5c4-198">Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışlar belirtmenizi sağlar ve hizmetlerin, yapılandırma hiyerarşisinin birden fazla düzeyinden davranışları devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="3a5c4-199">Bunun nasıl çalıştığını görmek için, IIS 'de aşağıdaki sanal dizin düzenine sahip olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="3a5c4-200">`~\Web.config` dosyanız aşağıdaki içeriğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="3a5c4-201">Ve şu içeriklerle ~ \Child\Web.config konumunda bulunan bir alt Web. config dosyası vardır:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="3a5c4-202">~ \Child\service.exe konumunda bulunan hizmet, hem serviceDebug hem de serviceMetadata davranışlarına sahip olsa da çalışır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="3a5c4-203">~ \Service.exe yolunda bulunan hizmette yalnızca serviceDebug davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="3a5c4-204">Ne olacağı, aynı ada sahip iki davranış koleksiyonunun (Bu durumda boş dize) birleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="3a5c4-205">Ayrıca, \<Remove > etiketini kullanarak \<Clear > etiketini kullanarak ve tek davranışları koleksiyondan kaldırdığınızda, davranış koleksiyonlarını temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="3a5c4-206">Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca serviceMetadata davranışına sahip olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="3a5c4-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="3a5c4-207">Davranış birleştirme yukarıda ve adlandırılmış davranış koleksiyonları da gösterildiği gibi adsız davranış koleksiyonları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="3a5c4-208">Davranış birleştirme, Web. config dosyalarının kök Web. config dosyası ve Machine. config ile hiyerarşik olarak birleştirileyeceği IIS barındırma ortamında çalışmaktadır. Ancak bu, Machine. config 'in App. config dosyasıyla birleştirilebileceği uygulama ortamında da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="3a5c4-209">Davranış birleştirme, yapılandırma içindeki uç nokta davranışları ve hizmet davranışları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="3a5c4-210">Bir alt davranış koleksiyonu, üst davranış koleksiyonunda zaten bulunan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="3a5c4-211">Bu nedenle, bir üst davranış koleksiyonu `<serviceMetadata httpGetEnabled="False" />` ve bir alt davranış koleksiyonu `<serviceMetadata httpGetEnabled="True" />`olsaydı, alt davranış davranış koleksiyonundaki üst davranışı geçersiz kılar ve httpGetEnabled "true" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5c4-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a5c4-212">See also</span></span>

- [<span data-ttu-id="3a5c4-213">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3a5c4-213">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="3a5c4-214">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3a5c4-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="3a5c4-215">\<Hizmeti ></span><span class="sxs-lookup"><span data-stu-id="3a5c4-215">\<service></span></span>](../configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="3a5c4-216">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="3a5c4-216">\<binding></span></span>](../configure-apps/file-schema/wcf/bindings.md)
