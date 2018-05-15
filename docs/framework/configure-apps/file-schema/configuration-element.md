---
title: '&lt;Yapılandırma&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d75b25734b92df062d3dc46824da44883ab46d5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-element"></a><span data-ttu-id="c18cf-102">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="c18cf-102">\<configuration> element</span></span>

<span data-ttu-id="c18cf-103">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c18cf-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="c18cf-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="c18cf-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c18cf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c18cf-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="c18cf-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c18cf-106">Attributes</span></span>

<span data-ttu-id="c18cf-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="c18cf-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c18cf-108">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="c18cf-108">Parent element</span></span>

<span data-ttu-id="c18cf-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c18cf-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="c18cf-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c18cf-110">Child elements</span></span>

|     | <span data-ttu-id="c18cf-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c18cf-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c18cf-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="c18cf-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="c18cf-113">Derleme bağlama ilkesi yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="c18cf-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="c18cf-114">**\<Başlangıç >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="c18cf-115">Başlangıç Ayarları Şeması tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="c18cf-116">**\<çalışma zamanı >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="c18cf-117">Çalışma Zamanı Ayarları Şeması tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="c18cf-118">**\<System.Runtime.Remoting >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="c18cf-119">Uzaktan iletişim ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="c18cf-120">**\<system.Net >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="c18cf-121">Ağ ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="c18cf-122">**\<cryptographySettings >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="c18cf-123">Şifreleme ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="c18cf-124">**\<Yapılandırma >** bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="c18cf-125">Yapılandırma bölümü ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="c18cf-126">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="c18cf-127">İzleme ve hata ayıklama Ayarları Şeması tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="c18cf-128">[ASP.NET yapılandırma ayarları şeması](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="c18cf-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="c18cf-129">ASP.NET Web siteleri ve uygulamaları yapılandırma öğeleri içeren ASP.NET yapılandırma şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="c18cf-130">Kullanılan *Web.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c18cf-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="c18cf-131">**\<Webservices'a >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="c18cf-132">Web Hizmetleri ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="c18cf-133">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="c18cf-134">ASP.NET IIS gibi bir ana bilgisayar uygulaması ile nasıl çalışır yapılandırma öğeleri içeren Web ayarları şemadaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="c18cf-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="c18cf-135">Kullanılan *aspnet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="c18cf-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c18cf-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c18cf-136">Remarks</span></span>

<span data-ttu-id="c18cf-137">Her yapılandırma dosyası tam olarak bir içermelidir  **\<configuration >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="c18cf-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="c18cf-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c18cf-138">See also</span></span>

[<span data-ttu-id="c18cf-139">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c18cf-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
