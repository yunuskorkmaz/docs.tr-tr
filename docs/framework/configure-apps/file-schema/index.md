---
title: .NET Framework için yapılandırma dosyası şeması
ms.date: 05/01/2017
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
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921034"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="8b4e2-102">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="8b4e2-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="8b4e2-103">Yapılandırma dosyaları, uygulamalarınız için ayarları değiştirmek ve ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="8b4e2-104">.NET Framework yapılandırma şeması, uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarında kullanabileceğiniz öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="8b4e2-105">Bu bölümün içindekiler tablosu, başlatma, çalışma zamanı, ağ ve diğer yapılandırma ayarları türleri için şema hiyerarşisini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="8b4e2-106">Yapılandırma dosyalarının türleri, biçimi ve konumu hakkında daha fazla bilgi için, [uygulamaları yapılandırma](../index.md)makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](../index.md).</span></span> <span data-ttu-id="8b4e2-107">Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız, XML hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b4e2-108">Yapılandırma dosyalarındaki XML etiketleri ve öznitelikleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8b4e2-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="8b4e2-109">In this section</span></span>

<span data-ttu-id="8b4e2-110">[**yapılandırma >\<** öğesi](configuration-element.md) Tüm yapılandırma dosyaları için en üst düzey öğe olan öğesiniaçıklar.`<configuration>`</span><span class="sxs-lookup"><span data-stu-id="8b4e2-110">[**\<configuration>** Element](configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="8b4e2-111">[assemblyBinding > öğesi, yapılandırma düzeyinde derleme bağlama ilkesini belirtir.  **\<** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="8b4e2-111">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="8b4e2-112">[linkedconfiguration > öğesi, dahil edilecek bir yapılandırma dosyasını belirtir.  **\<** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b4e2-112">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="8b4e2-113">[Başlangıç ayarları şeması](./startup/index.md) Hangi ortak dil çalışma zamanı sürümünün kullanılacağını belirten öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-113">[Startup Settings Schema](./startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="8b4e2-114">[Çalışma zamanı ayarları şeması](./runtime/index.md) Derleme bağlamayı ve çalışma zamanı davranışını yapılandıran öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-114">[Runtime Settings Schema](./runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="8b4e2-115">[Ağ ayarları şeması](./network/index.md) .NET Framework Internet 'e nasıl bağlandığını belirten öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-115">[Network Settings Schema](./network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="8b4e2-116">[Şifreleme ayarları şeması](./cryptography/index.md) Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-116">[Cryptography Settings Schema](./cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="8b4e2-117">[Yapılandırma bölümleri şeması](configuration-sections-schema.md) Özel ayarlar için yapılandırma bölümlerinin oluşturulması ve kullanılması için kullanılan öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-117">[Configuration Sections Schema](configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="8b4e2-118">[İzleme ve hata ayıklama ayarları şeması](./trace-debug/index.md) İzleme anahtarlarını ve dinleyicileri belirten öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-118">[Trace and Debug Settings Schema](./trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="8b4e2-119">[Derleyici ve dil sağlayıcısı ayarları şeması](./compiler/index.md) Kullanılabilir dil sağlayıcıları için derleyici yapılandırması belirten öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-119">[Compiler and Language Provider Settings Schema](./compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="8b4e2-120">[Uygulama ayarları şeması](application-settings-schema.md) Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasını ve almasına olanak sağlayan öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-120">[Application Settings Schema](application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="8b4e2-121">[Uygulama ayarları şeması](./appsettings/index.md) Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-121">[App Settings Schema](./appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="8b4e2-122">[Web ayarları şeması](./web/index.md) Web ayarları şemasında, ASP.NET 'in IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-122">[Web Settings Schema](./web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="8b4e2-123">*Aspnet. config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="8b4e2-124">[Windows Forms yapılandırma şeması](winforms/index.md) Çoklu izleyici ve yüksek DPı desteği gibi özelleştirmeler içeren Windows Forms uygulama yapılandırması bölümündeki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="8b4e2-125">[WCF yapılandırma şeması](./wcf/index.md) WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlayan tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-125">[WCF Configuration Schema](./wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="8b4e2-126">[WCF yönerge söz dizimi](./wcf-directive/index.md) . Svc derleyicisi tarafından kullanılan sayfaya özgü öznitelikleri tanımlayan yönergesiniaçıklar.`@ServiceHost`</span><span class="sxs-lookup"><span data-stu-id="8b4e2-126">[WCF Directive Syntax](./wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="8b4e2-127">[WIF yapılandırma şeması](windows-identity-foundation/index.md) Windows Identity Foundation (WıF) yapılandırma şemasının tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8b4e2-128">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="8b4e2-128">Related sections</span></span>

<span data-ttu-id="8b4e2-129">[Uzaktan Iletişim ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Uzaktan iletişim uygulayan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="8b4e2-130">[ASP.NET ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="8b4e2-131">[Web Hizmetleri ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) ASP.NET Web Hizmetleri ve istemcilerinin davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="8b4e2-132">[.NET Framework uygulamalarını yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) .NET Framework güvenlik, derleme bağlama ve uzaktan iletişimin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b4e2-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
