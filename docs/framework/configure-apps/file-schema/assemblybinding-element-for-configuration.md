---
title: '&lt;assemblyBinding&gt; öğesi için &lt;yapılandırma&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6a3358b2d64ade65e641caa203e2e760dcc4be2c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="a3d54-102">\<assemblyBinding > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a3d54-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="a3d54-103">Derleme bağlama ilkesi yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3d54-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="a3d54-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a3d54-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a3d54-105">&nbsp;&nbsp;**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="a3d54-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a3d54-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3d54-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="a3d54-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3d54-107">Attribute</span></span>

|           | <span data-ttu-id="a3d54-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d54-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a3d54-109">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="a3d54-109">**xmlns**</span></span> | <span data-ttu-id="a3d54-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a3d54-110">Required attribute.</span></span><br><br><span data-ttu-id="a3d54-111">Derleme bağlama için gereken XML ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3d54-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="a3d54-112">Dize kullanma "urn: şemaları-microsoft-com:asm.v1" değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="a3d54-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a3d54-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="a3d54-113">Parent element</span></span>

|     | <span data-ttu-id="a3d54-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d54-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a3d54-115">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="a3d54-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="a3d54-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a3d54-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="a3d54-117">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="a3d54-117">Child element</span></span>

|     | <span data-ttu-id="a3d54-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d54-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a3d54-119">**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="a3d54-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="a3d54-120">Dahil etmek için bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3d54-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a3d54-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3d54-121">Remarks</span></span>

<span data-ttu-id="a3d54-122">[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları sağlayarak bileşen derlemeleri yönetimini basitleştirir iyi bilinen konumları yerine çoğaltma derleme yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="a3d54-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="a3d54-123">**\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a3d54-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="a3d54-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3d54-124">Example</span></span>

<span data-ttu-id="a3d54-125">Aşağıdaki örnek, yerel sabit diskinde bir yapılandırma dosyası dahil gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a3d54-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a3d54-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d54-126">See also</span></span>

[<span data-ttu-id="a3d54-127">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a3d54-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
