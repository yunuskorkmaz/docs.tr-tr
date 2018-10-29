---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 11d24bec46cfb190fe1a7c2a7b9ac78ac4d5e799
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200868"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="eda11-102">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eda11-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="eda11-103">Bir yapılandırma dosyası bir Windows Communication Foundation (WCF) hizmetini yapılandırma uç noktası sağlama esnekliği sunar ve hizmet davranışı veri yerine dağıtım noktasında tasarım.</span><span class="sxs-lookup"><span data-stu-id="eda11-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="eda11-104">Bu konu, birincil teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="eda11-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="eda11-105">Bir WCF Hizmeti yapılandırılabilir kullanmaktır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknoloji.</span><span class="sxs-lookup"><span data-stu-id="eda11-105">A WCF service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="eda11-106">En yaygın olarak, XML öğeleri, bir WCF hizmetini barındıran Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="eda11-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="eda11-107">Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin.</span><span class="sxs-lookup"><span data-stu-id="eda11-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="eda11-108">Ayrıca, WCF, hızlı bir şekilde bir hizmet için en temel özellikler seçmenizi sağlayacak birçok sistem tarafından sağlanan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eda11-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="eda11-109">İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, WCF yapılandırma gereksinimleri basitleştiren yeni bir varsayılan yapılandırma modeli ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="eda11-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="eda11-110">Belirli bir hizmet için herhangi bir WCF yapılandırma sağlamazsanız, çalışma zamanının bazı standart uç noktalar ve varsayılan bağlama/davranışı ile otomatik olarak hizmetinizi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="eda11-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="eda11-111">Büyük bir uygulamada, yazma yapılandırmadır WCF uygulamalarını programlama parçası.</span><span class="sxs-lookup"><span data-stu-id="eda11-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="eda11-112">Daha fazla bilgi için [hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="eda11-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="eda11-113">Yaygın olarak kullanılan öğeleri en listesi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="eda11-113">For a list of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="eda11-114">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="eda11-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eda11-115">Dağıtıldığı bir hizmeti iki farklı sürümlerini yan yana senaryoları dağıtırken, yapılandırma dosyalarında başvurulan derlemeleri kısmi adını belirtmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eda11-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="eda11-116">Yapılandırma dosyası, bir hizmetin tüm sürümleri arasında paylaşılır ve altında .NET Framework'ün farklı sürümlerini çalıştıran çünkü budur.</span><span class="sxs-lookup"><span data-stu-id="eda11-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="eda11-117">System.Configuration: Web.config ve App.config</span><span class="sxs-lookup"><span data-stu-id="eda11-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="eda11-118">WCF kullanan System.Configuration yapılandırma sistemi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eda11-118">WCF uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="eda11-119">Bir hizmet Visual Studio'da yapılandırırken, Web.config dosyası veya bir App.config dosyası ayarlarını belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="eda11-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="eda11-120">Yapılandırma dosyası adı seçimi hizmeti için seçtiğiniz barındırma ortamı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="eda11-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="eda11-121">Hizmetinizi barındırmak için IIS kullanıyorsanız, Web.config dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="eda11-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="eda11-122">Herhangi bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="eda11-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="eda11-123">Visual Studio'da App.config adlı dosyayı son yapılandırma dosyası oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eda11-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="eda11-124">Son adı gerçekte yapılandırma için kullanılan derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eda11-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="eda11-125">Örneğin, "Cohowinery.exe" adlı bir derleme "Cohowinery.exe.config" son yapılandırma dosya adı vardır.</span><span class="sxs-lookup"><span data-stu-id="eda11-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="eda11-126">Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eda11-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="eda11-127">Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="eda11-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="eda11-128">Kullanarak bir App.config dosyası yapılandırma sistemi Machine.config dosyasının içeriğini App.config dosyanızı uygulama başladığında ve yapılandırmanın uygulanması birleştirir.</span><span class="sxs-lookup"><span data-stu-id="eda11-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="eda11-129">Bu mekanizma, makine genelindeki ayarlarının Machine.config dosyasında tanımlıdır sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda11-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="eda11-130">App.config dosyası, Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; böylece bunlar alışmanız Machine.config dosyasının ayarlarında kilitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eda11-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="eda11-131">Web.config durumda yapılandırma sistemi, uygulanan yapılandırmaya uygulama dizinine öncesinde tüm dizinleri Web.config dosyalarında birleştirir.</span><span class="sxs-lookup"><span data-stu-id="eda11-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="eda11-132">Yapılandırma ve ayarlama öncelikleri hakkında daha fazla bilgi için bkz <xref:System.Configuration> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="eda11-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="eda11-133">Yapılandırma dosyasının ana bölümlerinin</span><span class="sxs-lookup"><span data-stu-id="eda11-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="eda11-134">Ana bölümleri yapılandırma dosyasında aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eda11-134">The main sections in the configuration file include the following elements.</span></span>  
  
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
>  <span data-ttu-id="eda11-135">Bağlamalar ve davranışları bölümler isteğe bağlıdır ve bu yalnızca gerekirse dahil.</span><span class="sxs-lookup"><span data-stu-id="eda11-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="eda11-136">\<Hizmetleri > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-136">The \<services> Element</span></span>  
 <span data-ttu-id="eda11-137">`services` Öğesi tüm hizmetleri uygulama konakları için özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eda11-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="eda11-138">Basitleştirilmiş yapılandırma modeli ile başlayan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eda11-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="eda11-139">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="eda11-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="eda11-140">\<Hizmet > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-140">The \<service> Element</span></span>  
 <span data-ttu-id="eda11-141">Her hizmet bu özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="eda11-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="eda11-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="eda11-142">`name`.</span></span> <span data-ttu-id="eda11-143">Bir hizmet sözleşmesinin bir uygulaması sağlayan bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="eda11-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="eda11-144">Bu ad, nokta ve tür adı sonra oluşan tam bir addır.</span><span class="sxs-lookup"><span data-stu-id="eda11-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="eda11-145">Örneğin `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="eda11-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="eda11-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="eda11-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="eda11-147">Birinin adını belirten `behavior` öğeleri bulunan `behaviors` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eda11-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="eda11-148">Belirtilen davranışını hizmete bürünme izin verip gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="eda11-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="eda11-149">Öğenin değeri adı boş veya yok ise `behaviorConfiguration` hizmet davranışları varsayılan kümesi için hizmet eklendikten sonra sağlanır.</span><span class="sxs-lookup"><span data-stu-id="eda11-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="eda11-150">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="eda11-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="eda11-151">\<Uç noktası > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="eda11-152">Bir adresi, bağlama ve bir sözleşme aşağıdaki öznitelikleri tarafından temsil edilen her uç nokta gerektirir:</span><span class="sxs-lookup"><span data-stu-id="eda11-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="eda11-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="eda11-153">`address`.</span></span> <span data-ttu-id="eda11-154">Hizmetin Tekdüzen Kaynak Tanımlayıcısı (URI), mutlak bir adres veya hizmetin taban adresi göre verilen bir olabilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="eda11-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="eda11-155">Boş dize olarak ayarlanırsa, bu uç nokta oluşturulurken belirtilen temel adresinde kullanılabilir olduğunu gösterir, <xref:System.ServiceModel.ServiceHost> hizmeti.</span><span class="sxs-lookup"><span data-stu-id="eda11-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="eda11-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="eda11-156">`binding`.</span></span> <span data-ttu-id="eda11-157">Genellikle gibi sistem tarafından sağlanan bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding>, ancak kullanıcı tanımlı bir bağlama de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eda11-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="eda11-158">Belirtilen bağlama türü taşıma, güvenlik ve kodlamayı belirler ve olup güvenilir oturumlar, işlemler veya akış desteklenen etkin veya.</span><span class="sxs-lookup"><span data-stu-id="eda11-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="eda11-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="eda11-159">`bindingConfiguration`.</span></span> <span data-ttu-id="eda11-160">Bağlama varsayılan değerlerinin değiştirilmesi gerekir, bu uygun yapılandırarak yapılabilir `binding` öğesinde `bindings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eda11-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="eda11-161">Bu öznitelik aynı değere verilmelidir `name` özniteliği `binding` varsayılan değerleri değiştirmek için kullanılan bir öğe.</span><span class="sxs-lookup"><span data-stu-id="eda11-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="eda11-162">Ad belirtilmezse, ya da hiç `bindingConfiguration` bağlamasında belirtilen bağlama türü varsayılan bağlamasının uç noktasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eda11-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="eda11-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="eda11-163">`contract`.</span></span> <span data-ttu-id="eda11-164">Sözleşme tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="eda11-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="eda11-165">Bu tarafından belirtilen ortak dil çalışma zamanı (CLR) türüne uygulanan arabirimidir `name` özniteliği `service` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eda11-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="eda11-166">\<uç noktası > öğesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="eda11-166">\<endpoint> element reference</span></span>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="eda11-167">\<Bağlamaları > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="eda11-168">`bindings` Öğesi herhangi bir hizmette tanımlanan herhangi bir uç nokta tarafından kullanılan tüm bağlamaları için özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eda11-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="eda11-169">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="eda11-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="eda11-170">\<Bağlama > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-170">The \<binding> Element</span></span>  
 <span data-ttu-id="eda11-171">`binding` İçindeki öğe `bindings` öğesi, sistem tarafından sağlanan bağlamalar birini olabilir (bakın [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) veya özel bir bağlama (bkz [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="eda11-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="eda11-172">`binding` Öğeye sahip bir `name` belirtilen uç noktası ile bağlama karşılık gelen öznitelik `bindingConfiguration` özniteliği `endpoint` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eda11-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="eda11-173">Bu bağlama varsayılan bağlama türü için karşılık gelen sonra hiçbir ad belirtilmezse.</span><span class="sxs-lookup"><span data-stu-id="eda11-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 <span data-ttu-id="eda11-174">Hizmetler ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [Windows Communication Foundation uygulamaları yapılandırma](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="eda11-174">For more information about configuring services and clients, see [Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="eda11-175">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="eda11-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="eda11-176">\<Davranışları > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="eda11-177">İçin bir kapsayıcı öğe budur `behavior` bir hizmet için davranışları tanımlayan öğeler.</span><span class="sxs-lookup"><span data-stu-id="eda11-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="eda11-178">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="eda11-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="eda11-179">\<Davranışı > öğesi</span><span class="sxs-lookup"><span data-stu-id="eda11-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="eda11-180">Her `behavior` öğesi tarafından tanımlanan bir `name` özniteliği ve ya da bir sistem tarafından sağlanan, gibi sağlar <`throttling`>, ya da özel bir davranış.</span><span class="sxs-lookup"><span data-stu-id="eda11-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="eda11-181">Adsız verilirse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="eda11-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="eda11-182">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="eda11-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="eda11-183">Bağlama ve davranışı yapılandırmaları kullanma</span><span class="sxs-lookup"><span data-stu-id="eda11-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="eda11-184">WCF yapılandırmaları yapılandırmasında bir başvuru sistemi kullanarak uç noktalar arasında paylaşmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="eda11-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="eda11-185">Yapılandırma değerleri bir uç noktaya doğrudan atamak yerine, bağlama ile ilgili yapılandırma değerleri olarak gruplandırılır `bindingConfiguration` öğelerinde `<binding>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="eda11-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="eda11-186">Bir bağlama yapılandırmasını, bağlama ayarları, adlandırılmış bir gruptur.</span><span class="sxs-lookup"><span data-stu-id="eda11-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="eda11-187">Uç noktaları sonra başvuruda `bindingConfiguration` ada göre.</span><span class="sxs-lookup"><span data-stu-id="eda11-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="eda11-188">`name` , `bindingConfiguration` Ayarlanır `<binding>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="eda11-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="eda11-189">`name` Bağlama türü kapsamında benzersiz bir dize olmalıdır; bu durumda [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), ya da varsayılan bağlama başvurmak için boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="eda11-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="eda11-190">Uç nokta bağlantılar ayarlayarak yapılandırmayı `bindingConfiguration` için bu dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="eda11-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="eda11-191">A `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="eda11-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="eda11-192">Hizmet davranışları varsayılan kümesini hizmete eklenir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eda11-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="eda11-193">Bu sistem ayarları yeniden tanımlama olmadan yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda11-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="eda11-194">Makine genelinde kapsam gerekiyorsa, Machine.config dosyasına bağlama veya davranışını yapılandırma oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eda11-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="eda11-195">[Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="eda11-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="eda11-196">Birleştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="eda11-196">Behavior Merge</span></span>  
 <span data-ttu-id="eda11-197">Davranış birleştirme özelliği, bir dizi ortak davranışları sürekli olarak kullanılacak istediğinizde davranışları yönetmek üzere kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="eda11-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="eda11-198">Bu özellik, farklı düzeylerde yapılandırma hiyerarşisinin davranışları belirtin ve birden çok yapılandırma hiyerarşi düzeylerinden davranışları devral hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda11-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="eda11-199">Göstermek için nasıl bu çalışır sahip olduğunuzu varsayar şu sanal dizin Düzen IIS içinde:</span><span class="sxs-lookup"><span data-stu-id="eda11-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="eda11-200">Ve `~\Web.config` dosya aşağıdaki içeriğe sahip:</span><span class="sxs-lookup"><span data-stu-id="eda11-200">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="eda11-201">Ve aşağıdaki içeriklerle ~\Child\Web.config Web.config konumundaki bir alt sahip:</span><span class="sxs-lookup"><span data-stu-id="eda11-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="eda11-202">~\Child\Service.svc bulunan hizmet serviceDebug ve serviceMetadata davranışlarını içermese gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="eda11-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="eda11-203">~\Service.svc bulunan hizmet yalnızca serviceDebug davranışa sahip olur.</span><span class="sxs-lookup"><span data-stu-id="eda11-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="eda11-204">(Bu örnekte boş bir dize) aynı ada sahip iki davranışı koleksiyonlar birleştirilmeden olur.</span><span class="sxs-lookup"><span data-stu-id="eda11-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="eda11-205">Davranış koleksiyonlarını kullanarak da temizleyebilirsiniz \<Temizle > etiketi ve tek tek davranışları kullanarak koleksiyondan kaldırılır \<kaldırmak > etiketi.</span><span class="sxs-lookup"><span data-stu-id="eda11-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="eda11-206">Örneğin, yalnızca serviceMetadata davranışı sahip alt aşağıdaki iki yapılandırma sonuçları hizmeti:</span><span class="sxs-lookup"><span data-stu-id="eda11-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="eda11-207">Davranış birleştirme yukarıda da gösterildiği gibi adsız davranışı koleksiyonlar için yapılan ve davranış koleksiyonları adlı.</span><span class="sxs-lookup"><span data-stu-id="eda11-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="eda11-208">IIS barındırma ortamında machine.config ve kök Web.config dosyasında ile hiyerarşik olarak Web.config dosyaları birleştirme davranışı birleştirme çalışır. Ancak, machine.config App.config dosyanızı nereye birleştirebilirsiniz uygulama ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="eda11-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="eda11-209">Uç nokta davranışları hem yapılandırma hizmet davranışları birleştirme davranışı uygular.</span><span class="sxs-lookup"><span data-stu-id="eda11-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="eda11-210">Bir alt davranışı koleksiyon üst davranışı koleksiyonda zaten var. bir davranış içeriyorsa, üst alt davranışı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="eda11-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="eda11-211">Üst davranışı koleksiyonu varsa bunu `<serviceMetadata httpGetEnabled="False" />` ve alt davranışı koleksiyonunu `<serviceMetadata httpGetEnabled="True" />`, alt davranışı, davranış koleksiyondaki üst öğe davranışı geçersiz kılarsınız ve de "true" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="eda11-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda11-212">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eda11-212">See Also</span></span>  
 [<span data-ttu-id="eda11-213">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eda11-213">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="eda11-214">Windows Communication Foundation uygulamaları için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eda11-214">Configuring Windows Communication Foundation Applications</span></span>](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="eda11-215">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="eda11-215">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="eda11-216">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="eda11-216">\<binding></span></span>](../../../docs/framework/misc/binding.md)
