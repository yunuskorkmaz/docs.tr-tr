---
title: ".NET Framework için yapılandırma dosyası şeması"
ms.custom: 
ms.date: 05/01/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 283faabf0f23df2650f8d87fdebae1102b83235d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="263be-102">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="263be-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="263be-103">Yapılandırma dosyaları ayarlarını değiştirin ve uygulamalarınız için ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="263be-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="263be-104">.NET Framework yapılandırma şeması uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarını kullanabilirsiniz öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="263be-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="263be-105">Bu bölümde İçindekiler başlangıç, çalışma zamanı, ağ ve diğer yapılandırma ayarlarını türleri için şema hiyerarşisini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="263be-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="263be-106">Makaleyi türleri, biçimi ve yapılandırma dosyalarının konumu hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](~/docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="263be-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="263be-107">Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız XML ile edinin.</span><span class="sxs-lookup"><span data-stu-id="263be-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="263be-108">XML etiketleri ve öznitelikleri yapılandırma dosyalarında büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="263be-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="263be-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="263be-109">In this section</span></span>

<span data-ttu-id="263be-110">[**\<Yapılandırma >** öğesi](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes `<configuration>` tüm yapılandırma dosyaları için üst düzey öğe öğesi.</span><span class="sxs-lookup"><span data-stu-id="263be-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="263be-111">[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) derleme bağlama ilkesi yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="263be-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="263be-112">[**\<linkedConfiguration >** öğesi](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) dahil etmek için bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="263be-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="263be-113">[Başlangıç Ayarları Şeması](~/docs/framework/configure-apps/file-schema/startup/index.md) hangi sürümünün kullanılacağını ortak dil çalışma zamanı belirtin öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="263be-114">[Çalışma Zamanı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/runtime/index.md) derleme bağlama ve çalışma zamanı davranışını yapılandırma öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="263be-115">[Ağ Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework Internet'e nasıl bağlanacağını belirtin öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="263be-116">[Şifreleme Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleme öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="263be-117">[Yapılandırma bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) oluşturmak ve yapılandırma bölümlerinin için özel ayarları kullanmak için kullanılan öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="263be-118">[İzleme ve hata ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) izleme anahtarları ve dinleyicileri belirtin öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="263be-119">[Derleyici ve dil sağlayıcısı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/compiler/index.md) kullanılabilir dil sağlayıcısı derleyici yapılandırmayı belirtmek öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="263be-120">[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarlarını almak bir Windows Forms ya da ASP.NET uygulaması etkinleştiren öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="263be-121">[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/appsettings/index.md) dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="263be-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="263be-122">[Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) ASP.NET IIS gibi bir ana bilgisayar uygulaması ile nasıl çalışır yapılandırma öğeleri içeren Web ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="263be-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="263be-123">Kullanılan *Aspnet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="263be-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="263be-124">[Windows Forms yapılandırma şeması](winforms/index.md) tüm öğelerin birden çok monitör ve yüksek DPI desteği gibi özelleştirmeleri içeren Windows Forms uygulaması yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="263be-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="263be-125">[WCF yapılandırma şeması](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF hizmeti ve istemci uygulamaları yapılandırmanızı sağlayan tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="263be-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="263be-126">[WCF yönerge söz dizimi](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes `@ServiceHost` .svc derleyici tarafından kullanılan sayfa özel öznitelikleri tanımlar yönergesi.</span><span class="sxs-lookup"><span data-stu-id="263be-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="263be-127">[WIF yapılandırma şeması](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) yapılandırma şeması tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="263be-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="263be-128">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="263be-128">Related sections</span></span>

<span data-ttu-id="263be-129">[Uzaktan iletişim ayarları şeması](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) remoting uygulamak istemci ve sunucu uygulamaları yapılandırma öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-129">[Remoting Settings Schema](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="263be-130">[ASP.NET Ayarları Şeması](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-130">[ASP.NET Settings Schema](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="263be-131">[Web Hizmetleri ayarları şeması](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) ASP.NET Web Hizmetleri ve bunların istemcilerinin davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-131">[Web Services Settings Schema](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="263be-132">[.NET Framework uygulamalarını yapılandırma](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) güvenlik, derleme bağlama ve Uzaktan iletişim .NET Framework yapılandırmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="263be-132">[Configuring .NET Framework Apps](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
