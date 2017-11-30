---
title: "&lt;assemblyBinding&gt; öğesi için &lt;yapılandırma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2753e290af60d0dcf4efaa79ff3ffffbd7305c27
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="65f2d-102">\<assemblyBinding > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="65f2d-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="65f2d-103">Derleme bağlama ilkesi yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="65f2d-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="65f2d-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="65f2d-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="65f2d-105">&nbsp;&nbsp;**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="65f2d-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="65f2d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65f2d-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="65f2d-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="65f2d-107">Attribute</span></span>

|           | <span data-ttu-id="65f2d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65f2d-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="65f2d-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="65f2d-109">**xmlns**</span></span> | <span data-ttu-id="65f2d-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="65f2d-110">Required attribute.</span></span><br><br><span data-ttu-id="65f2d-111">Derleme bağlama için gereken XML ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="65f2d-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="65f2d-112">Dize kullanma "urn: şemaları-microsoft-com:asm.v1" değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="65f2d-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="65f2d-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="65f2d-113">Parent element</span></span>

|     | <span data-ttu-id="65f2d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65f2d-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="65f2d-115">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="65f2d-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="65f2d-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="65f2d-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="65f2d-117">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="65f2d-117">Child element</span></span>

|     | <span data-ttu-id="65f2d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65f2d-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="65f2d-119">**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="65f2d-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="65f2d-120">Dahil etmek için bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="65f2d-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="65f2d-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65f2d-121">Remarks</span></span>

<span data-ttu-id="65f2d-122">[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları sağlayarak bileşen derlemeleri yönetimini basitleştirir iyi bilinen konumları yerine çoğaltma derleme yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="65f2d-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="65f2d-123">**\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="65f2d-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="65f2d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="65f2d-124">Example</span></span>

<span data-ttu-id="65f2d-125">Aşağıdaki örnek, yerel sabit diskinde bir yapılandırma dosyası dahil gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="65f2d-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="65f2d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65f2d-126">See also</span></span>

[<span data-ttu-id="65f2d-127">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="65f2d-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
