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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039155"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="d8ae0-102">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d8ae0-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="d8ae0-103">Yapılandırma dosyaları, uygulamalarınız için ayarları değiştirmek ve ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="d8ae0-104">.NET Framework yapılandırma şeması, uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarında kullanabileceğiniz öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="d8ae0-105">Bu bölümün içindekiler tablosu, başlatma, çalışma zamanı, ağ ve diğer yapılandırma ayarları türleri için şema hiyerarşisini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="d8ae0-106">Yapılandırma dosyalarının türleri, biçimi ve konumu hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../index.md).</span><span class="sxs-lookup"><span data-stu-id="d8ae0-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="d8ae0-107">Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız, XML hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8ae0-108">Yapılandırma dosyalarındaki XML etiketleri ve öznitelikleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d8ae0-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="d8ae0-109">In this section</span></span>

<span data-ttu-id="d8ae0-110">[**\<configuration>** Dosyalarında](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="d8ae0-111">Tüm yapılandırma dosyaları için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="d8ae0-112">[**\<assemblyBinding>** Dosyalarında](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="d8ae0-113">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="d8ae0-114">[**\<linkedConfiguration>** Dosyalarında](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="d8ae0-115">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="d8ae0-116">[Başlangıç ayarları şeması](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="d8ae0-117">Ortak dil çalışma zamanının hangi sürümünü kullanacağınızı belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="d8ae0-118">[Çalışma zamanı ayarları şeması](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="d8ae0-119">Bütünleştirilmiş kod bağlamayı ve çalışma zamanı davranışını yapılandıran öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="d8ae0-120">[Ağ ayarları şeması](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="d8ae0-121">.NET Framework internet 'e nasıl bağlandığını belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="d8ae0-122">[Şifreleme ayarları şeması](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="d8ae0-123">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="d8ae0-124">[Yapılandırma bölümleri şeması](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="d8ae0-125">Özel ayarlar için yapılandırma bölümleri oluşturmak ve kullanmak için kullanılan öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="d8ae0-126">[İzleme ve hata ayıklama ayarları şeması](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="d8ae0-127">İzleme anahtarlarını ve dinleyicileri belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="d8ae0-128">[Derleyici ve dil sağlayıcısı ayarları şeması](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="d8ae0-129">Kullanılabilir dil sağlayıcıları için derleyici yapılandırması belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="d8ae0-130">[Uygulama ayarları şeması](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="d8ae0-131">Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına olanak tanıyan öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="d8ae0-132">[Uygulama ayarları şeması](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="d8ae0-133">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="d8ae0-134">[Web ayarları şeması](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="d8ae0-135">ASP.NET 'ın IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="d8ae0-136">*Aspnet. config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="d8ae0-137">[Windows Forms yapılandırma şeması](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="d8ae0-138">Çoklu izleyici ve yüksek DPı desteği gibi özelleştirmeler içeren Windows Forms uygulama yapılandırması bölümündeki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="d8ae0-139">[WCF yapılandırma şeması](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="d8ae0-140">WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlayan tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="d8ae0-141">[WCF yönerge söz dizimi](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="d8ae0-142">`@ServiceHost`. Svc derleyicisi tarafından kullanılan sayfaya özgü öznitelikleri tanımlayan yönergesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="d8ae0-143">[WıF yapılandırma şeması](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="d8ae0-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="d8ae0-144">Windows Identity Foundation (WıF) yapılandırma şemasının tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d8ae0-145">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="d8ae0-145">Related sections</span></span>

<span data-ttu-id="d8ae0-146">[Uzaktan iletişim ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8ae0-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="d8ae0-147">Uzaktan iletişim uygulayan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="d8ae0-148">[ASP.NET ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8ae0-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="d8ae0-149">ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="d8ae0-150">[Web Hizmetleri ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8ae0-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="d8ae0-151">ASP.NET Web Hizmetleri ve istemcilerinin davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="d8ae0-152">[.NET Framework uygulamalarını yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8ae0-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="d8ae0-153">.NET Framework güvenlik, derleme bağlama ve uzaktan iletişimin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d8ae0-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
