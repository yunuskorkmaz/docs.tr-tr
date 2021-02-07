---
description: 'Hakkında daha fazla bilgi edinin: .NET Framework için yapılandırma dosyası şeması'
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
ms.openlocfilehash: eac6d14f29f5ae0eeb65efe5a1416b8f40583be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729959"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="e9467-103">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e9467-103">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="e9467-104">Yapılandırma dosyaları, uygulamalarınız için ayarları değiştirmek ve ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="e9467-104">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="e9467-105">.NET Framework yapılandırma şeması, uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarında kullanabileceğiniz öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e9467-105">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="e9467-106">Bu bölümün içindekiler tablosu, başlatma, çalışma zamanı, ağ ve diğer yapılandırma ayarları türleri için şema hiyerarşisini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="e9467-106">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="e9467-107">Yapılandırma dosyalarının türleri, biçimi ve konumu hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../index.md).</span><span class="sxs-lookup"><span data-stu-id="e9467-107">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="e9467-108">Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız, XML hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e9467-108">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9467-109">Yapılandırma dosyalarındaki XML etiketleri ve öznitelikleri büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9467-109">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e9467-110">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="e9467-110">In this section</span></span>

<span data-ttu-id="e9467-111">[**\<configuration>** Dosyalarında](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-111">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="e9467-112">Tüm yapılandırma dosyaları için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="e9467-112">The top-level element for all configuration files.</span></span>

<span data-ttu-id="e9467-113">[**\<assemblyBinding>** Dosyalarında](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-113">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="e9467-114">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9467-114">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="e9467-115">[**\<linkedConfiguration>** Dosyalarında](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-115">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="e9467-116">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9467-116">Specifies a configuration file to include.</span></span>

<span data-ttu-id="e9467-117">[Başlangıç ayarları şeması](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-117">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="e9467-118">Ortak dil çalışma zamanının hangi sürümünü kullanacağınızı belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-118">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="e9467-119">[Çalışma zamanı ayarları şeması](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-119">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="e9467-120">Bütünleştirilmiş kod bağlamayı ve çalışma zamanı davranışını yapılandıran öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-120">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="e9467-121">[Ağ ayarları şeması](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-121">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="e9467-122">.NET Framework internet 'e nasıl bağlandığını belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-122">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="e9467-123">[Şifreleme ayarları şeması](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-123">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="e9467-124">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-124">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="e9467-125">[Yapılandırma bölümleri şeması](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-125">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="e9467-126">Özel ayarlar için yapılandırma bölümleri oluşturmak ve kullanmak için kullanılan öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-126">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="e9467-127">[İzleme ve hata ayıklama ayarları şeması](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-127">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="e9467-128">İzleme anahtarlarını ve dinleyicileri belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-128">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="e9467-129">[Derleyici ve dil sağlayıcısı ayarları şeması](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-129">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="e9467-130">Kullanılabilir dil sağlayıcıları için derleyici yapılandırması belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-130">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="e9467-131">[Uygulama ayarları şeması](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-131">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="e9467-132">Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına olanak tanıyan öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-132">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="e9467-133">[Uygulama ayarları şeması](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-133">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="e9467-134">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e9467-134">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="e9467-135">[Web ayarları şeması](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-135">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="e9467-136">ASP.NET 'ın IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-136">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="e9467-137">*Aspnet.config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9467-137">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="e9467-138">[Windows Forms yapılandırma şeması](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-138">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="e9467-139">Çoklu izleyici ve yüksek DPı desteği gibi özelleştirmeler içeren Windows Forms uygulama yapılandırması bölümündeki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-139">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="e9467-140">[WCF yapılandırma şeması](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-140">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="e9467-141">WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlayan tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e9467-141">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="e9467-142">[WCF yönerge söz dizimi](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-142">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="e9467-143">`@ServiceHost`. Svc derleyicisi tarafından kullanılan sayfaya özgü öznitelikleri tanımlayan yönergesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9467-143">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="e9467-144">[WıF yapılandırma şeması](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="e9467-144">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="e9467-145">Windows Identity Foundation (WıF) yapılandırma şemasının tüm öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e9467-145">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e9467-146">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="e9467-146">Related sections</span></span>

<span data-ttu-id="e9467-147">[Uzaktan iletişim ayarları şeması](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9467-147">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="e9467-148">Uzaktan iletişim uygulayan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9467-148">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="e9467-149">[ASP.NET ayarları şeması](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9467-149">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="e9467-150">ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9467-150">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="e9467-151">[Web Hizmetleri ayarları şeması](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9467-151">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="e9467-152">ASP.NET Web Hizmetleri ve istemcilerinin davranışını denetleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9467-152">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="e9467-153">[.NET Framework uygulamalarını yapılandırma](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9467-153">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="e9467-154">.NET Framework güvenlik, derleme bağlama ve uzaktan iletişimin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9467-154">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
