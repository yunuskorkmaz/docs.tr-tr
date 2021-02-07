---
description: 'Daha fazla bilgi edinin: yapılandırma bölümleri şeması'
title: Yapılandırma bölümleri şeması
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: f16ca16417da0b3ee7a7d0a5ebdd1a446ec0714a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698966"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="85537-103">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="85537-103">Configuration sections schema</span></span>

<span data-ttu-id="85537-104">Yapılandırma bölümleri şeması, yapılandırma dosyalarında özel ayarları tanımlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="85537-104">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="85537-105">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz. [.NET Framework Için yapılandırma dosyası şeması](index.md).</span><span class="sxs-lookup"><span data-stu-id="85537-105">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="85537-106">Description</span><span class="sxs-lookup"><span data-stu-id="85537-106">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="85537-107">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="85537-107">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="85537-108">**\<section>\*\*\*\*\<configSections>** ve için **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="85537-108">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="85537-109">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="85537-109">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="85537-110">**\<sectionGroup>** bekleniyor **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="85537-110">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="85537-111">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85537-111">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="85537-112">Uygulanmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="85537-112">Unimplemented elements</span></span>

<span data-ttu-id="85537-113">Aşağıdaki öğelerin etkisi yoktur ve kullanılmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="85537-113">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
