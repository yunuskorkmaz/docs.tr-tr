---
title: <configuration> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544699"
---
# <a name="configuration-element"></a><span data-ttu-id="e1b67-102">\<configuration> öğesi</span><span class="sxs-lookup"><span data-stu-id="e1b67-102">\<configuration> element</span></span>

<span data-ttu-id="e1b67-103">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e1b67-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="e1b67-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1b67-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="e1b67-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1b67-105">Attributes</span></span>

<span data-ttu-id="e1b67-106">Yok</span><span class="sxs-lookup"><span data-stu-id="e1b67-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e1b67-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="e1b67-107">Parent element</span></span>

<span data-ttu-id="e1b67-108">Yok</span><span class="sxs-lookup"><span data-stu-id="e1b67-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="e1b67-109">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e1b67-109">Child elements</span></span>

|     | <span data-ttu-id="e1b67-110">Description</span><span class="sxs-lookup"><span data-stu-id="e1b67-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="e1b67-111">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e1b67-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="e1b67-112">**\<startup>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="e1b67-113">Başlangıç ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="e1b67-114">**\<runtime>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="e1b67-115">Çalışma zamanı ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="e1b67-116">[**\<system.runtime.remoting>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e1b67-116">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="e1b67-117">Uzaktan iletişim ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="e1b67-118">**\<system.Net>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="e1b67-119">Ağ ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="e1b67-120">**\<cryptographySettings>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="e1b67-121">Şifre ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="e1b67-122">**\<configuration>** Bölüm Şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="e1b67-123">Yapılandırma bölümü ayarları şemasında tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="e1b67-124">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="e1b67-125">İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="e1b67-126">[ASP.NET yapılandırma ayarları şeması](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e1b67-126">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="e1b67-127">ASP.NET yapılandırma şemasında, ASP.NET Web siteleri ve uygulamaları yapılandırma öğelerini içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="e1b67-128">*Web.config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1b67-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="e1b67-129">[**\<webServices>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e1b67-129">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="e1b67-130">Web Hizmetleri ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="e1b67-131">Web ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="e1b67-132">Web ayarları şemasında, ASP.NET 'in IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="e1b67-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="e1b67-133">*aspnet.config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1b67-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e1b67-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1b67-134">Remarks</span></span>

<span data-ttu-id="e1b67-135">Her yapılandırma dosyası tam olarak bir **\<configuration>** öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="e1b67-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1b67-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b67-136">See also</span></span>

- [<span data-ttu-id="e1b67-137">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e1b67-137">Configuration file schema for the .NET Framework</span></span>](index.md)
