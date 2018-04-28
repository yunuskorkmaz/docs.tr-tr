---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f1c7449372ad012280b360c09017a15733fb95b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="cb63d-102">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cb63d-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="cb63d-103">Yapılandırma bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmeti bir yapılandırma dosyası ile tasarım zamanında yerine dağıtım noktasında uç noktası ve hizmet davranışı verileri sağlayan esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-103">Configuring a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="cb63d-104">Bu konu, birincil teknikleri özetler.</span><span class="sxs-lookup"><span data-stu-id="cb63d-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="cb63d-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetidir yapılandırılabilir kullanarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknolojisi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="cb63d-106">XML öğeleri barındıran Internet Information Services (IIS) sitesi için Web.config dosyasının en yaygın olarak eklenen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="cb63d-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="cb63d-107">Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin.</span><span class="sxs-lookup"><span data-stu-id="cb63d-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="cb63d-108">Ayrıca, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hızlı bir şekilde bir hizmeti için en temel özellikleri seçmenize olanak birkaç sistem tarafından sağlanan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-108">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="cb63d-109">İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kolaylaştıran yeni bir varsayılan yapılandırma modeli ile birlikte gelen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="cb63d-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="cb63d-110">Herhangi bir sağlamazsanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma çalışma zamanı belirli bir hizmet için bazı standart uç noktaları ve varsayılan bağlama/davranışı hizmetinizi otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="cb63d-111">Uygulamada, yazma yapılandırma programlama önemli bir parçası olan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-111">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="cb63d-112"> [Hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb63d-112"> [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="cb63d-113">Öğeleri listesini en sık kullanılan için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="cb63d-113">For a list of of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="cb63d-114"> Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="cb63d-114"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb63d-115">Bir hizmeti iki farklı sürümü dağıtıldığı yan yana senaryoları dağıtırken, yapılandırma dosyalarını başvurulan derlemelerin kısmi adını belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="cb63d-116">Bu yapılandırma dosyası, bir hizmetin tüm sürümleri arasında paylaşılır ve altında .NET Framework'ün farklı sürümlerini çalıştıran kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="cb63d-117">System.Configuration: Web.config ve App.config</span><span class="sxs-lookup"><span data-stu-id="cb63d-117">System.Configuration: Web.config and App.config</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="cb63d-118"> System.Configuration yapılandırma sistemini kullanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb63d-118"> uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="cb63d-119">Visual Studio'da bir hizmeti yapılandırma sırasında bir Web.config dosyası ya da bir App.config dosyası ayarlarını belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb63d-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="cb63d-120">Yapılandırma dosyasının adını seçimi hizmeti için seçtiğiniz barındırma ortamı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="cb63d-121">Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb63d-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="cb63d-122">Herhangi bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="cb63d-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="cb63d-123">Visual Studio'da App.config adlı dosyayı son yapılandırma dosyası oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="cb63d-124">Gerçekte yapılandırma için kullanılan son adı derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="cb63d-125">Örneğin, "Cohowinery.exe" adlı bir derleme "Cohowinery.exe.config" bir son yapılandırma dosya adına sahip.</span><span class="sxs-lookup"><span data-stu-id="cb63d-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="cb63d-126">Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="cb63d-127">Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="cb63d-128">Kullanarak bir App.config dosyası yapılandırma sistemi App.config dosyası Machine.config dosyasının içeriği ile uygulama başlar ve yapılandırmanın uygulanması birleştirir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="cb63d-129">Bu mekanizma Machine.config dosyasında tanımlanmış için makine genelinde ayarlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="cb63d-130">App.config dosyasını Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; Böylece kullanılan Machine.config dosyasının ayarlarında kilitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb63d-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="cb63d-131">Web.config durumda uygulama dizinine uygulanan yapılandırmaya baştaki tüm dizinleri Web.config dosyalarında yapılandırma sistemi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="cb63d-132"> Yapılandırma ve ayarı öncelikleri bkz konularında <xref:System.Configuration> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cb63d-132"> configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="cb63d-133">Yapılandırma dosyasının ana bölümleri</span><span class="sxs-lookup"><span data-stu-id="cb63d-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="cb63d-134">Yapılandırma dosyasındaki ana bölümleri aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
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
>  <span data-ttu-id="cb63d-135">Bağlamalar ve davranışları bölümler isteğe bağlı olan ve bu gerekli olursa yalnızca.</span><span class="sxs-lookup"><span data-stu-id="cb63d-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="cb63d-136">\<Hizmetleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-136">The \<services> Element</span></span>  
 <span data-ttu-id="cb63d-137">`services` Öğesi tüm hizmetleri uygulama konakları özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="cb63d-138">Basitleştirilmiş yapılandırma modele itibaren [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu bölümde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="cb63d-139">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="cb63d-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="cb63d-140">\<Hizmet > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-140">The \<service> Element</span></span>  
 <span data-ttu-id="cb63d-141">Her hizmet bu özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cb63d-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="cb63d-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-142">`name`.</span></span> <span data-ttu-id="cb63d-143">Bir hizmet sözleşmesini uygulaması sağlar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="cb63d-144">Bu ad, bir süre ve tür adı sonra oluşan tam bir addır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="cb63d-145">Örneğin `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="cb63d-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="cb63d-147">Birinin adını belirtir `behavior` öğeleri bulunan `behaviors` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="cb63d-148">Belirtilen davranışını hizmet kimliğe bürünme izin verip gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="cb63d-149">Öğenin değeri adı boş veya Hayır ise `behaviorConfiguration` hizmet davranışları varsayılan kümesini hizmete eklendikten sonra sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="cb63d-150">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="cb63d-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="cb63d-151">\<Uç noktası > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="cb63d-152">Bir adresi, bağlama ve bir sözleşme aşağıdaki öznitelikleri tarafından temsil edilen her uç nokta gerektiriyor:</span><span class="sxs-lookup"><span data-stu-id="cb63d-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="cb63d-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-153">`address`.</span></span> <span data-ttu-id="cb63d-154">Hizmetin Tekdüzen Kaynak Tanımlayıcısı (URI), mutlak bir adres veya hizmetin taban adresi göre verilen biri olabilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="cb63d-155">Boş bir dize olarak ayarlandıysa, bu uç noktası oluşturulurken belirtilen temel adresinde kullanılabilir olduğunu gösterir <xref:System.ServiceModel.ServiceHost> hizmeti.</span><span class="sxs-lookup"><span data-stu-id="cb63d-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="cb63d-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-156">`binding`.</span></span> <span data-ttu-id="cb63d-157">Genellikle gibi sistem tarafından sağlanan bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding>, ancak kullanıcı tanımlı bir bağlama de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb63d-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="cb63d-158">Belirtilen bağlama taşıma, güvenlik ve kullanılan kodlama türünü belirler ve güvenilir oturumlar, işlemler veya akış desteklenen etkin mı.</span><span class="sxs-lookup"><span data-stu-id="cb63d-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="cb63d-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-159">`bindingConfiguration`.</span></span> <span data-ttu-id="cb63d-160">Varsayılan değerleri bağlaması değiştirilmesi gerekir, bu uygun yapılandırarak yapılabilir `binding` öğesinde `bindings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="cb63d-161">Bu öznitelik ile aynı değere verilmelidir `name` özniteliği `binding` varsayılanları değiştirmek için kullanılan öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="cb63d-162">Ad belirtilmezse ya da hiç `bindingConfiguration` bağlama türü varsayılan bağlamasının uç kullanılır bağlamasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="cb63d-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="cb63d-163">`contract`.</span></span> <span data-ttu-id="cb63d-164">Sözleşmesini tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="cb63d-165">Bu tarafından belirtilen ortak dil çalışma zamanı (CLR) türüne uygulanan arabirimidir `name` özniteliği `service` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="cb63d-166">\<uç noktası > öğesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb63d-166">\<endpoint> element reference</span></span>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="cb63d-167">\<Bağlamaları > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="cb63d-168">`bindings` Öğesi içinde herhangi bir hizmeti tanımlanan herhangi bir uç nokta tarafından kullanılan tüm bağlamaları özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="cb63d-169">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="cb63d-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="cb63d-170">\<Bağlama > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-170">The \<binding> Element</span></span>  
 <span data-ttu-id="cb63d-171">`binding` İçindeki öğe `bindings` öğesi, sistem tarafından sağlanan bağlamalar birini olabilir (bakın [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) veya özel bağlama (bkz [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="cb63d-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="cb63d-172">`binding` Öğeye sahip bir `name` belirtilen uç noktası ile bağlama karşılık gelen öznitelik `bindingConfiguration` özniteliği `endpoint` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="cb63d-173">Bu bağlama, bağlama türü varsayılan olarak karşılık gelen sonra ad belirtilmezse.</span><span class="sxs-lookup"><span data-stu-id="cb63d-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="cb63d-174"> Hizmetler ve istemcileri yapılandırmak, bkz: [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="cb63d-174"> configuring services and clients, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="cb63d-175">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb63d-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="cb63d-176">\<Davranışları > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="cb63d-177">Bu kapsayıcı için bir unsurdur `behavior` bir hizmet için davranışları tanımlamak öğeleri.</span><span class="sxs-lookup"><span data-stu-id="cb63d-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="cb63d-178">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="cb63d-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="cb63d-179">\<Davranışı > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb63d-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="cb63d-180">Her `behavior` öğesi tarafından tanımlanan bir `name` özniteliği ve ya da bir sistem tarafından sağlanan davranışı gibi sağlar <`throttling`>, veya özel bir davranış.</span><span class="sxs-lookup"><span data-stu-id="cb63d-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="cb63d-181">Ad belirtilmezse bu davranışı öğesi varsayılan hizmet veya uç noktası davranışı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="cb63d-182">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="cb63d-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="cb63d-183">Bağlama ve davranış yapılandırmalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="cb63d-183">How to Use Binding and Behavior Configurations</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="cb63d-184"> yapılandırmaları başvuru sistemi yapılandırmayla uç noktalar arasında paylaşmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-184"> makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="cb63d-185">Yapılandırma değerlerini bir bitiş noktasına doğrudan atamak yerine, bağlama ile ilgili yapılandırma değerlerini gruplandırılmıştır `bindingConfiguration` öğelerinde `<binding>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="cb63d-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="cb63d-186">Bağlama yapılandırması, bir bağlama ayarlarını adlandırılmış grubudur.</span><span class="sxs-lookup"><span data-stu-id="cb63d-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="cb63d-187">Uç noktalar sonra başvuru `bindingConfiguration` ada göre.</span><span class="sxs-lookup"><span data-stu-id="cb63d-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
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
  
 <span data-ttu-id="cb63d-188">`name` , `bindingConfiguration` Kümesinde `<binding>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="cb63d-189">`name` Bağlama türü kapsamında benzersiz bir dize olması gerekir; bu durumda [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), ya da varsayılan bağlama başvurmak için boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="cb63d-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="cb63d-190">Uç noktası bağlantıları ayarlayarak yapılandırma `bindingConfiguration` özniteliği bu dize.</span><span class="sxs-lookup"><span data-stu-id="cb63d-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="cb63d-191">A `behaviorConfiguration` aynı şekilde, aşağıdaki örnekte gösterildiği gibi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="cb63d-192">Hizmet davranışları varsayılan kümesini hizmetine eklendiğinde unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cb63d-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="cb63d-193">Bu sistem ayarlarını tanımlayarak olmadan ortak yapılandırmaları paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="cb63d-194">Makine genelinde kapsam gerekiyorsa, bağlama veya davranışını yapılandırma Machine.config içinde oluşturun. Yapılandırma ayarları tüm App.config dosyaları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="cb63d-195">[Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmak kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="cb63d-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="cb63d-196">Davranış birleştirme</span><span class="sxs-lookup"><span data-stu-id="cb63d-196">Behavior Merge</span></span>  
 <span data-ttu-id="cb63d-197">Davranış birleştirme özelliği, sürekli olarak kullanılacak ortak davranışları kümesi istediğinizde davranışlarını yönetmek üzere kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="cb63d-198">Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerde davranışları belirtmek ve Hizmetleri, birden çok yapılandırma hiyerarşisini düzeylerinden davranışları devralmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="cb63d-199">Göstermek için nasıl bu works sahip olduğunuzu varsayar aşağıdaki sanal dizin düzeni IIS'de:</span><span class="sxs-lookup"><span data-stu-id="cb63d-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="cb63d-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="cb63d-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="cb63d-201">Ve ~\Web.config dosyanız aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="cb63d-201">And your ~\Web.config file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="cb63d-202">Ve Web.config aşağıdaki içeriğe sahip ~\Child\Web.config konumunda bulunan alt vardır:</span><span class="sxs-lookup"><span data-stu-id="cb63d-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="cb63d-203">~\Child\Service.svc bulunan hizmet serviceDebug ve serviceMetadata davranışları içermese gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="cb63d-204">~\Service.svc bulunan hizmet serviceDebug davranışı yalnızca sahip olur.</span><span class="sxs-lookup"><span data-stu-id="cb63d-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="cb63d-205">(Bu durumda boş dize) aynı ada sahip iki davranış koleksiyonları birleştirilir olur.</span><span class="sxs-lookup"><span data-stu-id="cb63d-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="cb63d-206">Kullanarak davranış koleksiyonları temizleyebilirsiniz \<temizleyin > etiketi ve kullanarak tek tek davranışları koleksiyondan kaldırıldı \<kaldırma > etiketi.</span><span class="sxs-lookup"><span data-stu-id="cb63d-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="cb63d-207">Örneğin, aşağıdaki iki yapılandırma sonuçlarında alt yalnızca serviceMetadata davranışı sahip hizmeti:</span><span class="sxs-lookup"><span data-stu-id="cb63d-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="cb63d-208">Davranış birleştirme yukarıda gösterildiği gibi adsız davranışı koleksiyonlar için yapılan ve davranış koleksiyonları adlı.</span><span class="sxs-lookup"><span data-stu-id="cb63d-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="cb63d-209">Davranış birleştirme ortamında hangi Web.config dosyaları birleştirme hiyerarşik olarak machine.config ve kök Web.config dosyasında barındıran IIS çalışır. Ancak, uygulama ortamında machine.config App.config dosyası ile burada birleştirebilirsiniz çalışır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="cb63d-210">Uç nokta davranışları ve hizmet davranışları yapılandırma davranışı birleştirme uygular.</span><span class="sxs-lookup"><span data-stu-id="cb63d-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="cb63d-211">Bir alt davranışı koleksiyon üst davranışı koleksiyonda zaten bir davranış içeriyorsa, alt davranışı üst geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="cb63d-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="cb63d-212">Bir üst davranışı koleksiyon sahipse, bu nedenle `<serviceMetadata httpGetEnabled="False" />` ve alt davranışı koleksiyonunu `<serviceMetadata httpGetEnabled="True" />`, alt davranışı davranışı koleksiyonundaki üst davranışı geçersiz kılarsınız ve de "true" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cb63d-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb63d-213">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb63d-213">See Also</span></span>  
 [<span data-ttu-id="cb63d-214">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cb63d-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="cb63d-215">Windows Communication Foundation uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cb63d-215">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="cb63d-216">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="cb63d-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="cb63d-217">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="cb63d-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
