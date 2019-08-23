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
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921243"
---
# <a name="configuration-element"></a><span data-ttu-id="50370-102">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="50370-102">\<configuration> element</span></span>

<span data-ttu-id="50370-103">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="50370-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="50370-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="50370-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="50370-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50370-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="50370-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="50370-106">Attributes</span></span>

<span data-ttu-id="50370-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="50370-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="50370-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="50370-108">Parent element</span></span>

<span data-ttu-id="50370-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="50370-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="50370-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="50370-110">Child elements</span></span>

|     | <span data-ttu-id="50370-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50370-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="50370-112"> **\<assemblyBinding >** </span><span class="sxs-lookup"><span data-stu-id="50370-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="50370-113">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="50370-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="50370-114">Başlangıç > ayarları şeması  **\<** </span><span class="sxs-lookup"><span data-stu-id="50370-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="50370-115">Başlangıç ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="50370-116">çalışma zamanı > ayarları şeması  **\<** </span><span class="sxs-lookup"><span data-stu-id="50370-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="50370-117">Çalışma zamanı ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="50370-118">[**System. Runtime. Remoting > ayarları şeması \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="50370-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="50370-119">Uzaktan iletişim ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="50370-120">sistem .net > ayarları şeması  **\<** </span><span class="sxs-lookup"><span data-stu-id="50370-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="50370-121">Ağ ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="50370-122">cryptographyısettings > ayarları şeması  **\<** </span><span class="sxs-lookup"><span data-stu-id="50370-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="50370-123">Şifre ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="50370-124">Yapılandırma > bölümleri şeması  **\<** </span><span class="sxs-lookup"><span data-stu-id="50370-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="50370-125">Yapılandırma bölümü ayarları şemasında tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="50370-126">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="50370-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="50370-127">İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="50370-128">[ASP.NET yapılandırma ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="50370-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="50370-129">ASP.NET yapılandırma şemasında, ASP.NET Web siteleri ve uygulamaları yapılandırma öğelerini içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="50370-130">*Web. config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50370-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="50370-131">[WebServices > ayarları şeması  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="50370-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="50370-132">Web Hizmetleri ayarları şemasındaki tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="50370-133">Web Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="50370-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="50370-134">Web ayarları şemasında, ASP.NET 'in IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler içeren tüm öğeler.</span><span class="sxs-lookup"><span data-stu-id="50370-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="50370-135">*Aspnet. config* dosyalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50370-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="50370-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50370-136">Remarks</span></span>

<span data-ttu-id="50370-137">Her yapılandırma dosyası tam olarak bir  **\<Yapılandırma >** öğesi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="50370-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="50370-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50370-138">See also</span></span>

- [<span data-ttu-id="50370-139">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="50370-139">Configuration file schema for the .NET Framework</span></span>](index.md)
