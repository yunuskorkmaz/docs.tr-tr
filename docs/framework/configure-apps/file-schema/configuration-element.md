---
description: 'Daha fazla bilgi edinin: <configuration> öğesi'
title: <configuration> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: ee48a45ddb987201e84213a0d7674da004951ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699005"
---
# <a name="configuration-element"></a><span data-ttu-id="4b1fb-103">\<configuration> öğesi</span><span class="sxs-lookup"><span data-stu-id="4b1fb-103">\<configuration> element</span></span>

<span data-ttu-id="4b1fb-104">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-104">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="4b1fb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b1fb-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="4b1fb-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b1fb-106">Attributes</span></span>

<span data-ttu-id="4b1fb-107">Yok</span><span class="sxs-lookup"><span data-stu-id="4b1fb-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4b1fb-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="4b1fb-108">Parent element</span></span>

<span data-ttu-id="4b1fb-109">Yok</span><span class="sxs-lookup"><span data-stu-id="4b1fb-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="4b1fb-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4b1fb-110">Child elements</span></span>

|     | <span data-ttu-id="4b1fb-111">Description</span><span class="sxs-lookup"><span data-stu-id="4b1fb-111">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="4b1fb-112">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-112">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="4b1fb-113">**\<startup>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-113">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="4b1fb-114">Başlangıç ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-114">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-115">**\<runtime>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-115">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="4b1fb-116">Çalışma zamanı ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-116">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="4b1fb-117">[**\<system.runtime.remoting>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b1fb-117">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="4b1fb-118">Uzaktan iletişim ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-118">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-119">**\<system.Net>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-119">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="4b1fb-120">Ağ ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-120">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-121">**\<cryptographySettings>** Ayarlar Şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-121">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="4b1fb-122">Şifre ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-122">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-123">**\<configuration>** Bölüm Şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-123">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="4b1fb-124">Yapılandırma bölümü ayarları şemasında tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-124">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-125">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-125">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="4b1fb-126">İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-126">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="4b1fb-127">[ASP.NET yapılandırma ayarları şeması](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b1fb-127">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="4b1fb-128">ASP.NET yapılandırma şemasında, ASP.NET Web siteleri ve uygulamaları yapılandırma öğelerini içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-128">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="4b1fb-129">*Web.config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-129">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="4b1fb-130">[**\<webServices>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b1fb-130">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="4b1fb-131">Web Hizmetleri ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-131">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="4b1fb-132">Web ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-132">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="4b1fb-133">Web ayarları şemasında, ASP.NET 'in IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-133">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="4b1fb-134">*aspnet.config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-134">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4b1fb-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b1fb-135">Remarks</span></span>

<span data-ttu-id="4b1fb-136">Her yapılandırma dosyası tam olarak bir **\<configuration>** öğe içermelidir.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-136">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b1fb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b1fb-137">See also</span></span>

- [<span data-ttu-id="4b1fb-138">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4b1fb-138">Configuration file schema for the .NET Framework</span></span>](index.md)
