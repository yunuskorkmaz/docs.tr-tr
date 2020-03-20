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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155485"
---
# <a name="assemblybinding-element-for-configuration"></a><span data-ttu-id="c8248-102">\<derlemeYapılandırma> \<için> öğesi bağlama</span><span class="sxs-lookup"><span data-stu-id="c8248-102">\<assemblyBinding> element for \<configuration></span></span>

<span data-ttu-id="c8248-103">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8248-103">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="c8248-104">yapılandırma &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \*\* \<montajBağlayıcı>\*\*</span><span class="sxs-lookup"><span data-stu-id="c8248-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c8248-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8248-105">Syntax</span></span>

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a><span data-ttu-id="c8248-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c8248-106">Attribute</span></span>

|           | <span data-ttu-id="c8248-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8248-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c8248-108">**Xmlns**</span><span class="sxs-lookup"><span data-stu-id="c8248-108">**xmlns**</span></span> | <span data-ttu-id="c8248-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c8248-109">Required attribute.</span></span><br><br><span data-ttu-id="c8248-110">Derleme bağlama için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8248-110">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="c8248-111">Değer olarak "urn:schemas-microsoft-com:asm.v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8248-111">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c8248-112">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="c8248-112">Parent element</span></span>

|     | <span data-ttu-id="c8248-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8248-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8248-114">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="c8248-114">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="c8248-115">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c8248-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-element"></a><span data-ttu-id="c8248-116">Alt öğe</span><span class="sxs-lookup"><span data-stu-id="c8248-116">Child element</span></span>

|     | <span data-ttu-id="c8248-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8248-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8248-118">**\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="c8248-118">**\<linkedConfiguration>**</span></span>](linkedconfiguration-element.md) | <span data-ttu-id="c8248-119">İçerecek bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8248-119">Specifies a configuration file to include.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c8248-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8248-120">Remarks</span></span>

<span data-ttu-id="c8248-121">LinkedConfiguration>öğesi, uygulama yapılandırma dosyalarının derleme yapılandırma ayarlarını çoğaltmak yerine iyi bilinen konumlarda derleme yapılandırma dosyalarını içermesi için izin vererek bileşen derlemelerinin yönetimini kolaylaştırır. [\*\* \<\*\*](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c8248-121">The [**\<linkedConfiguration>**](linkedconfiguration-element.md) element simplifies the management of component assemblies by allowing application configuration files to include assembly configuration files in well-known locations, rather than duplicating assembly configuration settings.</span></span>

> [!NOTE]
> <span data-ttu-id="c8248-122">\*\* \<Bağlantılı Yapılandırma>\*\* öğesi, Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c8248-122">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

## <a name="example"></a><span data-ttu-id="c8248-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8248-123">Example</span></span>

<span data-ttu-id="c8248-124">Aşağıdaki örnek, yerel sabit diske yapılandırma dosyasının nasıl eklenmeygerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c8248-124">The following example shows how to include a configuration file on the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c8248-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8248-125">See also</span></span>

- [<span data-ttu-id="c8248-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c8248-126">Configuration file schema for the .NET Framework</span></span>](index.md)
