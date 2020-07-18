---
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
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441667"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="04039-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="04039-102">Configuration sections schema</span></span>

<span data-ttu-id="04039-103">Yapılandırma bölümleri şeması, yapılandırma dosyalarında özel ayarları tanımlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="04039-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="04039-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz. [.NET Framework Için yapılandırma dosyası şeması](index.md).</span><span class="sxs-lookup"><span data-stu-id="04039-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="04039-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04039-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="04039-106">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="04039-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="04039-107">**\<section>\*\*\*\*\<configSections>** ve için**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="04039-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="04039-108">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="04039-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="04039-109">**\<sectionGroup>** bekleniyor**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="04039-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="04039-110">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="04039-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="04039-111">Uygulanmayan öğeler</span><span class="sxs-lookup"><span data-stu-id="04039-111">Unimplemented elements</span></span>

<span data-ttu-id="04039-112">Aşağıdaki öğelerin etkisi yoktur ve kullanılmamalıdır:</span><span class="sxs-lookup"><span data-stu-id="04039-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
