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
ms.openlocfilehash: c5146ed8326b12e90d0fe6247b0c4aba3a69dd77
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485787"
---
# <a name="configuration-element"></a><span data-ttu-id="2f6ce-102">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="2f6ce-102">\<configuration> element</span></span>

<span data-ttu-id="2f6ce-103">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="2f6ce-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="2f6ce-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2f6ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f6ce-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="2f6ce-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f6ce-106">Attributes</span></span>

<span data-ttu-id="2f6ce-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2f6ce-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="2f6ce-108">Parent element</span></span>

<span data-ttu-id="2f6ce-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="2f6ce-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2f6ce-110">Child elements</span></span>

|     | <span data-ttu-id="2f6ce-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f6ce-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2f6ce-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="2f6ce-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="2f6ce-113">Derleme bağlama ilkesini yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="2f6ce-114">**\<Başlangıç >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="2f6ce-115">Başlangıç Ayarları Şeması tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-116">**\<çalışma zamanı >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="2f6ce-117">Çalışma zamanı ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-118">**\<System.Runtime.Remoting >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-118">**\<system.runtime.remoting>** Settings Schema</span></span>](https://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="2f6ce-119">Uzaktan iletişim ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-120">**\<system.Net >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="2f6ce-121">Ağ ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-122">**\<cryptographySettings >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="2f6ce-123">Şifreleme ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-124">**\<Yapılandırma >** bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="2f6ce-125">Yapılandırma bölümü ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-126">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="2f6ce-127">İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="2f6ce-128">[ASP.NET yapılandırma ayarları şeması](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f6ce-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="2f6ce-129">ASP.NET Web siteleri ve uygulamaları yapılandırma öğeleri içeren ASP.NET yapılandırma şemadaki tüm öğelerin.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="2f6ce-130">Kullanılan *Web.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="2f6ce-131">**\<Veritabanınızdaki >** Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-131">**\<webServices>** Settings Schema</span></span>](https://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="2f6ce-132">Web Hizmetleri ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="2f6ce-133">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="2f6ce-134">Nasıl ASP.NET, IIS gibi ana bilgisayar uygulamasıyla çalışmasını yapılandırmak için öğeler içeren Web ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="2f6ce-135">Kullanılan *aspnet.config* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2f6ce-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f6ce-136">Remarks</span></span>

<span data-ttu-id="2f6ce-137">Her bir yapılandırma dosyası tam olarak bir içermelidir  **\<yapılandırma >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f6ce-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f6ce-138">See also</span></span>

[<span data-ttu-id="2f6ce-139">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="2f6ce-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
