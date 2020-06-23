---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
description: WCF hizmeti için bir yapılandırma dosyasının Dağıtım sırasında Endpoint ve hizmet davranışı verileri sağlama esnekliğini nasıl sağladığını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 1a3266ad8890436c9be9d0f2b231aeaca0f9236e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245433"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="122ae-103">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="122ae-103">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="122ae-104">Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyası ile yapılandırmak, dağıtım noktasında, tasarım zamanında değil, uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="122ae-104">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="122ae-105">Bu konu başlığı altında sunulan birincil teknikler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="122ae-105">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="122ae-106">WCF hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-106">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="122ae-107">En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="122ae-107">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="122ae-108">Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="122ae-108">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="122ae-109">Ayrıca, WCF, bir hizmet için en temel özellikleri hızlıca seçmenizi sağlayan, sistem tarafından sunulan çeşitli öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="122ae-109">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="122ae-110">WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir.</span><span class="sxs-lookup"><span data-stu-id="122ae-110">Starting with .NET Framework 4, WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="122ae-111">Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı, hizmetinizi bazı standart uç noktalarla ve varsayılan bağlama/davranışla otomatik olarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="122ae-111">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="122ae-112">Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="122ae-112">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="122ae-113">Daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="122ae-113">For more information, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="122ae-114">En yaygın kullanılan öğelerin listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="122ae-114">For a list of the most commonly used elements, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="122ae-115">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="122ae-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="122ae-116">Bir hizmetin iki farklı sürümünün dağıtıldığı yan yana senaryolar dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="122ae-116">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="122ae-117">Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümleri arasında paylaşılmaları ve .NET Framework farklı sürümlerinde çalışıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-117">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="122ae-118">System.Configurlama: Web.config ve App.config</span><span class="sxs-lookup"><span data-stu-id="122ae-118">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="122ae-119">WCF, .NET Framework System.Configuration yapılandırma sistemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="122ae-119">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="122ae-120">Bir hizmeti Visual Studio 'da yapılandırırken, ayarları belirtmek için bir Web.config dosyası ya da bir App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="122ae-120">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="122ae-121">Yapılandırma dosyası adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="122ae-121">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="122ae-122">Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="122ae-122">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="122ae-123">Başka bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.</span><span class="sxs-lookup"><span data-stu-id="122ae-123">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="122ae-124">Visual Studio 'da App.config adlı dosya, son yapılandırma dosyasını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="122ae-124">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="122ae-125">Yapılandırma için gerçekten kullanılan son ad, derleme adına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="122ae-125">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="122ae-126">Örneğin, "Cohowinery.exe" adlı bir derlemenin son yapılandırma dosyası adı "Cohowinery.exe.config" vardır.</span><span class="sxs-lookup"><span data-stu-id="122ae-126">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="122ae-127">Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="122ae-127">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="122ae-128">Bu dosyada yapılan değişiklikler derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="122ae-128">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="122ae-129">App.config kullanarak, yapılandırma sistemi, uygulama başladığında ve yapılandırma uygulandığında App.config dosyasını Machine.config dosyanın içeriğiyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="122ae-129">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="122ae-130">Bu mekanizma, Machine.config dosyasında makine genelindeki ayarların tanımlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="122ae-130">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="122ae-131">App.config dosyası, Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; Ayrıca, Machine.config dosyadaki ayarları, bunların kullanılması için de kilitle.</span><span class="sxs-lookup"><span data-stu-id="122ae-131">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="122ae-132">Web.config durumda, yapılandırma sistemi tüm dizinlerde bulunan Web.config dosyalarını, uygulanan yapılandırmayla uygulama dizinine en başta birleştirir.</span><span class="sxs-lookup"><span data-stu-id="122ae-132">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="122ae-133">Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi için bkz. ad alanındaki konular <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="122ae-133">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="122ae-134">Yapılandırma dosyasının ana bölümleri</span><span class="sxs-lookup"><span data-stu-id="122ae-134">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="122ae-135">Yapılandırma dosyasındaki ana bölümler aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="122ae-135">The main sections in the configuration file include the following elements.</span></span>  
  
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
> <span data-ttu-id="122ae-136">Bağlamalar ve davranışlar bölümleri isteğe bağlıdır ve yalnızca gerekli olduğunda dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-136">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="122ae-137">\<services>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-137">The \<services> Element</span></span>  
 <span data-ttu-id="122ae-138">`services`Öğesi, uygulamanın barındırdığı tüm hizmetlere ilişkin belirtimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="122ae-138">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="122ae-139">.NET Framework 4 ' te Basitleştirilmiş yapılandırma modeliyle başlayarak bu bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="122ae-139">Starting with the simplified configuration model in .NET Framework 4, this section is optional.</span></span>  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="122ae-140">\<service>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-140">The \<service> Element</span></span>  
 <span data-ttu-id="122ae-141">Her hizmet şu özniteliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="122ae-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="122ae-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="122ae-142">`name`.</span></span> <span data-ttu-id="122ae-143">Hizmet sözleşmesinin bir uygulamasını sağlayan türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="122ae-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="122ae-144">Bu, ad alanı, nokta ve daha sonra tür adından oluşan tam nitelikli bir addır.</span><span class="sxs-lookup"><span data-stu-id="122ae-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="122ae-145">Örneğin, `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="122ae-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="122ae-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="122ae-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="122ae-147">`behavior`Öğesinde bulunan öğelerden birinin adını belirtir `behaviors` .</span><span class="sxs-lookup"><span data-stu-id="122ae-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="122ae-148">Belirtilen davranış, hizmetin kimliğe bürünmeye izin verip etmeyeceğini gibi eylemleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="122ae-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="122ae-149">Değeri boş bir ad ise veya Hayır sağlanmazsa, `behaviorConfiguration` varsayılan hizmet davranışı kümesi hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="122ae-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="122ae-150">\<endpoint>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-150">The \<endpoint> Element</span></span>  
 <span data-ttu-id="122ae-151">Her uç nokta, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve bir sözleşme gerektirir:</span><span class="sxs-lookup"><span data-stu-id="122ae-151">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="122ae-152">`address`.</span><span class="sxs-lookup"><span data-stu-id="122ae-152">`address`.</span></span> <span data-ttu-id="122ae-153">Hizmetin temel adresine göreli olarak verilen mutlak bir adres veya hizmet olan Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="122ae-153">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="122ae-154">Boş bir dizeye ayarlanırsa, uç noktanın hizmet için oluşturulurken belirtilen temel adreste kullanılabilir olduğunu gösterir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="122ae-154">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="122ae-155">`binding`.</span><span class="sxs-lookup"><span data-stu-id="122ae-155">`binding`.</span></span> <span data-ttu-id="122ae-156">Genellikle gibi sistem tarafından sağlanmış bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding> , ancak kullanıcı tanımlı bağlamayı da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-156">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="122ae-157">Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, işlemlerin veya akışın desteklenip desteklenmediğini ya da etkin olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="122ae-157">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="122ae-158">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="122ae-158">`bindingConfiguration`.</span></span> <span data-ttu-id="122ae-159">Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu, öğesinde uygun öğe yapılandırılarak yapılabilir `binding` `bindings` .</span><span class="sxs-lookup"><span data-stu-id="122ae-159">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="122ae-160">Bu özniteliğe, `name` `binding` varsayılan değerleri değiştirmek için kullanılan öğesinin özniteliğiyle aynı değer verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="122ae-160">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="122ae-161">Hiçbir ad verilmezse veya bağlamada hiçbir değer `bindingConfiguration` belirtilmemişse, bağlantı türü için varsayılan bağlama uç noktada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="122ae-161">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="122ae-162">`contract`.</span><span class="sxs-lookup"><span data-stu-id="122ae-162">`contract`.</span></span> <span data-ttu-id="122ae-163">Sözleşmeyi tanımlayan arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="122ae-163">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="122ae-164">Bu, öğesinin özniteliği tarafından belirtilen ortak dil çalışma zamanı (CLR) türünde uygulanan arabirimdir `name` `service` .</span><span class="sxs-lookup"><span data-stu-id="122ae-164">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="122ae-165">\<bindings>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-165">The \<bindings> Element</span></span>  
 <span data-ttu-id="122ae-166">`bindings`Öğesi, herhangi bir hizmette tanımlı herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="122ae-166">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="122ae-167">\<binding>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-167">The \<binding> Element</span></span>  
 <span data-ttu-id="122ae-168">`binding`Öğesinde yer alan öğeler, `bindings` sistem tarafından belirtilen bağlamalardan biri olabilir ( [sistem tarafından belirtilen bağlamaları](system-provided-bindings.md)görebilir) veya özel bir bağlama (bkz. [Özel Bağlamalar](./extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="122ae-168">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](system-provided-bindings.md)) or a custom binding (see [Custom Bindings](./extending/custom-bindings.md)).</span></span> <span data-ttu-id="122ae-169">`binding`Öğesi, `name` bağlamayı öğenin özniteliğinde belirtilen uç noktayla ilişkilendiren bir özniteliğe sahiptir `bindingConfiguration` `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="122ae-169">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="122ae-170">Ad belirtilmemişse, o bağlama o bağlama türünün varsayılan değerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="122ae-170">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="122ae-171">Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="122ae-171">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="122ae-172">\<behaviors>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-172">The \<behaviors> Element</span></span>  
 <span data-ttu-id="122ae-173">Bu, `behavior` bir hizmetin davranışlarını tanımlayan öğeler için bir kapsayıcı öğesidir.</span><span class="sxs-lookup"><span data-stu-id="122ae-173">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="122ae-174">\<behavior>Öğe</span><span class="sxs-lookup"><span data-stu-id="122ae-174">The \<behavior> Element</span></span>  
 <span data-ttu-id="122ae-175">Her `behavior` öğe bir öznitelik tarafından tanımlanır `name` ve <`throttling`> ya da özel bir davranış gibi sistem tarafından sağlanan bir davranış sağlar.</span><span class="sxs-lookup"><span data-stu-id="122ae-175">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="122ae-176">Ad verilmezse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="122ae-176">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="122ae-177">Bağlama ve davranış yapılandırmalarının kullanımı</span><span class="sxs-lookup"><span data-stu-id="122ae-177">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="122ae-178">WCF, yapılandırmada bir başvuru sistemi kullanarak uç noktalar arasında yapılandırmaların paylaşılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="122ae-178">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="122ae-179">Yapılandırma değerlerini bir uç noktaya doğrudan atamak yerine, bağlama ilgili yapılandırma değerleri, `bindingConfiguration` bölümündeki öğelerde gruplandırılır `<binding>` .</span><span class="sxs-lookup"><span data-stu-id="122ae-179">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="122ae-180">Bağlama yapılandırması, bağlamada adlandırılmış bir ayar grubudur.</span><span class="sxs-lookup"><span data-stu-id="122ae-180">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="122ae-181">Uç noktalar daha sonra `bindingConfiguration` adına göre başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-181">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
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
  
 <span data-ttu-id="122ae-182">`name` `bindingConfiguration` `<binding>` Öğesi öğesinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="122ae-182">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="122ae-183">`name`Bağlama türünün kapsamı içinde benzersiz bir dize olmalıdır — bu durumda [<\> BasicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)veya varsayılan bağlamaya başvuracak boş bir değer.</span><span class="sxs-lookup"><span data-stu-id="122ae-183">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="122ae-184">Uç nokta, özniteliğini bu dizeye ayarlayarak yapılandırmaya bağlanır `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="122ae-184">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="122ae-185">`behaviorConfiguration`, Aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="122ae-185">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="122ae-186">Varsayılan hizmet davranışı kümesinin hizmete eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="122ae-186">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="122ae-187">Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaların paylaşmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="122ae-187">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="122ae-188">Makine genelindeki kapsam gerekliyse, Machine.config bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="122ae-188">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="122ae-189">[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) , yapılandırmaların oluşturulmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="122ae-189">The [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="122ae-190">Davranış birleştirme</span><span class="sxs-lookup"><span data-stu-id="122ae-190">Behavior Merge</span></span>  
 <span data-ttu-id="122ae-191">Davranış birleştirme özelliği, bir dizi ortak davranışın sürekli olarak kullanılmasını istediğinizde davranışları yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="122ae-191">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="122ae-192">Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışlar belirtmenizi sağlar ve hizmetlerin, yapılandırma hiyerarşisinin birden fazla düzeyinden davranışları devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="122ae-192">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="122ae-193">Bunun nasıl çalıştığını görmek için, IIS 'de aşağıdaki sanal dizin düzenine sahip olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="122ae-193">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="122ae-194">Ve `~\Web.config` dosyanız aşağıdaki içeriğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="122ae-194">And your `~\Web.config` file has the following contents:</span></span>  
  
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
  
 <span data-ttu-id="122ae-195">Ve aşağıdaki içeriklerle ~\Child\Web.config konumunda bulunan bir alt Web.config vardır:</span><span class="sxs-lookup"><span data-stu-id="122ae-195">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
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
  
 <span data-ttu-id="122ae-196">~ \Child\service.exe konumunda bulunan hizmet, hem serviceDebug hem de serviceMetadata davranışlarına sahip olsa da çalışır.</span><span class="sxs-lookup"><span data-stu-id="122ae-196">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="122ae-197">~ \Service.exe yolunda bulunan hizmette yalnızca serviceDebug davranışı olur.</span><span class="sxs-lookup"><span data-stu-id="122ae-197">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="122ae-198">Ne olacağı, aynı ada sahip iki davranış koleksiyonunun (Bu durumda boş dize) birleştirilmesidir.</span><span class="sxs-lookup"><span data-stu-id="122ae-198">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="122ae-199">Ayrıca, etiketini kullanarak \<clear> ve ' yi kullanarak tek davranışları koleksiyondan kaldırarak davranış koleksiyonlarını temizleyebilirsiniz \<remove> .</span><span class="sxs-lookup"><span data-stu-id="122ae-199">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="122ae-200">Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca serviceMetadata davranışına sahip olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="122ae-200">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
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
  
 <span data-ttu-id="122ae-201">Davranış birleştirme yukarıda ve adlandırılmış davranış koleksiyonları da gösterildiği gibi adsız davranış koleksiyonları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="122ae-201">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="122ae-202">Davranış birleştirme, Web.config dosyalarının kök Web.config dosyası ve machine.config hiyerarşik olarak birleştirileyeceği IIS barındırma ortamında çalışmaktadır. Ancak, machine.config App.config dosyayla birleştirebildiği uygulama ortamında da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="122ae-202">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="122ae-203">Davranış birleştirme, yapılandırma içindeki uç nokta davranışları ve hizmet davranışları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="122ae-203">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="122ae-204">Bir alt davranış koleksiyonu, üst davranış koleksiyonunda zaten bulunan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="122ae-204">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="122ae-205">Bu nedenle, bir üst davranış koleksiyonu `<serviceMetadata httpGetEnabled="False" />` ve bir alt davranış koleksiyonu varsa `<serviceMetadata httpGetEnabled="True" />` , alt davranış davranış koleksiyonundaki üst davranışı geçersiz kılar ve httpGetEnabled "true" olacaktır.</span><span class="sxs-lookup"><span data-stu-id="122ae-205">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122ae-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="122ae-206">See also</span></span>

- [<span data-ttu-id="122ae-207">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="122ae-207">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="122ae-208">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="122ae-208">Configuring WCF services</span></span>](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
