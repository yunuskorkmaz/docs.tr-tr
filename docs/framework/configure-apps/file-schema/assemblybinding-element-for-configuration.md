---
description: 'İçin: öğesi hakkında daha fazla bilgi <assemblyBinding><configuration>'
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 5cc3fc7cccd4b9dc7b62815734ff76e32e2243d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730115"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="4a62d-103">\<configuration> için \<assemblyBinding> öğesi</span><span class="sxs-lookup"><span data-stu-id="4a62d-103">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="4a62d-104">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a62d-104">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="4a62d-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="4a62d-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4a62d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a62d-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="4a62d-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a62d-107">Attribute</span></span>

|           | <span data-ttu-id="4a62d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a62d-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4a62d-109">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="4a62d-109">**xmlns**</span></span> | <span data-ttu-id="4a62d-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4a62d-110">Required attribute.</span></span><br><br><span data-ttu-id="4a62d-111">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a62d-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="4a62d-112">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4a62d-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4a62d-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="4a62d-113">Parent element</span></span>

|     | <span data-ttu-id="4a62d-114">Description</span><span class="sxs-lookup"><span data-stu-id="4a62d-114">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="4a62d-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4a62d-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="4a62d-116">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="4a62d-116">Child element</span></span>

|     | <span data-ttu-id="4a62d-117">Description</span><span class="sxs-lookup"><span data-stu-id="4a62d-117">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="4a62d-118">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a62d-118">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4a62d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a62d-119">Remarks</span></span>

<span data-ttu-id="4a62d-120">[**\<linkedConfiguration>**](linkedconfiguration-element.md)Öğesi, uygulama yapılandırma dosyalarının derleme yapılandırma ayarlarını çoğaltmak yerine, bilinen konumlarda derleme yapılandırma dosyalarını içermesini sağlayarak bileşen derlemelerinin yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="4a62d-120">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="4a62d-121">**\<linkedConfiguration>** Windows yan yana bildirimleri olan uygulamalar için öğesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4a62d-121">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="4a62d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a62d-122">Example</span></span>

<span data-ttu-id="4a62d-123">Aşağıdaki örnek, yerel sabit diske bir yapılandırma dosyasının nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="4a62d-123">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4a62d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a62d-124">See also</span></span>

- [<span data-ttu-id="4a62d-125">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4a62d-125">Configuration file schema for the .NET Framework</span></span>](index.md)
