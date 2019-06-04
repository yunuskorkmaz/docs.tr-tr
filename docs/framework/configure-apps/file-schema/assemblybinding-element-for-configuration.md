---
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: f5992a6085c32d37f56319cf8b2c361542c441e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674837"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="a7e46-102">\<assemblyBinding > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a7e46-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="a7e46-103">Derleme bağlama ilkesini yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e46-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="a7e46-104">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a7e46-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a7e46-105">&nbsp;&nbsp; **\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="a7e46-105">&nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a7e46-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e46-106">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="a7e46-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a7e46-107">Attribute</span></span>

|           | <span data-ttu-id="a7e46-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e46-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a7e46-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="a7e46-109">**xmlns**</span></span> | <span data-ttu-id="a7e46-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a7e46-110">Required attribute.</span></span><br><br><span data-ttu-id="a7e46-111">Derleme bağlama için gerekli XML ad alanı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e46-111">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="a7e46-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span><span class="sxs-lookup"><span data-stu-id="a7e46-112">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a7e46-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="a7e46-113">Parent element</span></span>

|     | <span data-ttu-id="a7e46-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e46-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a7e46-115"> *\*\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="a7e46-115">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="a7e46-116">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a7e46-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="a7e46-117">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="a7e46-117">Child element</span></span>

|     | <span data-ttu-id="a7e46-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e46-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a7e46-119"> *\*\<linkedConfiguration>** </span><span class="sxs-lookup"><span data-stu-id="a7e46-119">**\<linkedConfiguration>**</span></span>](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | <span data-ttu-id="a7e46-120">Dahil edilecek bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e46-120">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="a7e46-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7e46-121">Remarks</span></span>

<span data-ttu-id="a7e46-122">[ **\<LinkedConfiguration>** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları vererek bileşen derlemelerini yönetimini basitleştirir iyi bilinen konumları, çoğaltma derleme yapılandırma ayarları yerine.</span><span class="sxs-lookup"><span data-stu-id="a7e46-122">The [**\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="a7e46-123">**\<LinkedConfiguration>** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a7e46-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="a7e46-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7e46-124">Example</span></span>

<span data-ttu-id="a7e46-125">Aşağıdaki örnek bir yapılandırma dosyasını yerel sabit diskte nasıl ekleyeceğinizi gösterir:</span><span class="sxs-lookup"><span data-stu-id="a7e46-125">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a7e46-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e46-126">See also</span></span>

- [<span data-ttu-id="a7e46-127">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a7e46-127">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
