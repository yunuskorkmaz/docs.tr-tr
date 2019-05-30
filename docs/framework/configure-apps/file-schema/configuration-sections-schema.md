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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c7559a95099608ea462c838591ddb43e18d8f80c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301228"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="662c1-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="662c1-102">Configuration sections schema</span></span>

<span data-ttu-id="662c1-103">Yapılandırma bölümleri şeması, yapılandırma dosyalarında özel ayarlar tanımlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="662c1-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="662c1-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz. [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="662c1-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="662c1-105">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="662c1-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="662c1-106">[ **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="662c1-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="662c1-107">[ **\<Temizleme >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="662c1-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="662c1-108">[ **\<kaldırma >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="662c1-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="662c1-109">[ **\<Bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="662c1-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="662c1-110"> *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="662c1-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="662c1-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="662c1-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="662c1-112"> *\*\<Temizle >** için  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="662c1-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="662c1-113">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="662c1-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="662c1-114"> *\*\<Temizleme >** </span><span class="sxs-lookup"><span data-stu-id="662c1-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="662c1-115">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="662c1-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="662c1-116"> *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="662c1-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="662c1-117">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="662c1-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="662c1-118"> *\*\<kaldırma >** için  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="662c1-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="662c1-119">Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="662c1-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="662c1-120"> *\*\<Bölüm >** için  *\*\<configSections >** ve  *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="662c1-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="662c1-121">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="662c1-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="662c1-122"> *\*\<sectionGroup >** için  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="662c1-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="662c1-123">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="662c1-123">Defines a namespace for configuration sections.</span></span> |
