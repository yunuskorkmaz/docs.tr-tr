---
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155485"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="c6562-102">\<configuration> için \<assemblyBinding> öğesi</span><span class="sxs-lookup"><span data-stu-id="c6562-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="c6562-103">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6562-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="c6562-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span><span class="sxs-lookup"><span data-stu-id="c6562-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c6562-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6562-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="c6562-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6562-106">Attribute</span></span>

|           | <span data-ttu-id="c6562-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6562-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c6562-108">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="c6562-108">**xmlns**</span></span> | <span data-ttu-id="c6562-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c6562-109">Required attribute.</span></span><br><br><span data-ttu-id="c6562-110">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6562-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="c6562-111">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6562-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c6562-112">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="c6562-112">Parent element</span></span>

|     | <span data-ttu-id="c6562-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6562-113">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="c6562-114">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c6562-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="c6562-115">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="c6562-115">Child element</span></span>

|     | <span data-ttu-id="c6562-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6562-116">Description</span></span> |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | <span data-ttu-id="c6562-117">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6562-117">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c6562-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6562-118">Remarks</span></span>

<span data-ttu-id="c6562-119">[**\<linkedConfiguration>**](linkedconfiguration-element.md)Öğesi, uygulama yapılandırma dosyalarının derleme yapılandırma ayarlarını çoğaltmak yerine, bilinen konumlarda derleme yapılandırma dosyalarını içermesini sağlayarak bileşen derlemelerinin yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c6562-119">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="c6562-120">**\<linkedConfiguration>** Windows yan yana bildirimleri olan uygulamalar için öğesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c6562-120">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="c6562-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6562-121">Example</span></span>

<span data-ttu-id="c6562-122">Aşağıdaki örnek, yerel sabit diske bir yapılandırma dosyasının nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c6562-122">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c6562-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6562-123">See also</span></span>

- [<span data-ttu-id="c6562-124">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c6562-124">Configuration file schema for the .NET Framework</span></span>](index.md)
