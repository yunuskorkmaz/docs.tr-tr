---
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921270"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="e7b89-102">\<Yapılandırma > için \<assemblyBinding > öğesi</span><span class="sxs-lookup"><span data-stu-id="e7b89-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="e7b89-103">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7b89-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="e7b89-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e7b89-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="e7b89-105">&nbsp;&nbsp; **\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="e7b89-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e7b89-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7b89-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="e7b89-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7b89-107">Attribute</span></span>

|           | <span data-ttu-id="e7b89-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7b89-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e7b89-109">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="e7b89-109">**xmlns**</span></span> | <span data-ttu-id="e7b89-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7b89-110">Required attribute.</span></span><br><br><span data-ttu-id="e7b89-111">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7b89-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="e7b89-112">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7b89-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e7b89-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="e7b89-113">Parent element</span></span>

|     | <span data-ttu-id="e7b89-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7b89-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e7b89-115"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="e7b89-115">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="e7b89-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e7b89-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="e7b89-117">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="e7b89-117">Child element</span></span>

|     | <span data-ttu-id="e7b89-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7b89-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e7b89-119"> **\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="e7b89-119">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="e7b89-120">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7b89-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e7b89-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7b89-121">Remarks</span></span>

<span data-ttu-id="e7b89-122">[
          **
          \<LinkedConfiguration>** ](linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları vererek bileşen derlemelerini yönetimini basitleştirir iyi bilinen konumları, çoğaltma derleme yapılandırma ayarları yerine.</span><span class="sxs-lookup"><span data-stu-id="e7b89-122">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="e7b89-123">**
          \<LinkedConfiguration>** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e7b89-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="e7b89-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7b89-124">Example</span></span>

<span data-ttu-id="e7b89-125">Aşağıdaki örnek, yerel sabit diske bir yapılandırma dosyasının nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e7b89-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e7b89-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7b89-126">See also</span></span>

- [<span data-ttu-id="e7b89-127">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e7b89-127">Configuration file schema for the .NET Framework</span></span>](index.md)
