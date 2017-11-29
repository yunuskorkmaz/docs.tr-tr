---
title: "Yapılandırma bölümleri şeması"
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c668cf3d2f2c0bcffda185cea01edfb9e55c6d6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="5a73e-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="5a73e-102">Configuration sections schema</span></span>

<span data-ttu-id="5a73e-103">Yapılandırma bölümleri şeması yapılandırma dosyalarında özel ayarlar tanımlama öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5a73e-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="5a73e-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz: [.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a73e-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="5a73e-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5a73e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5a73e-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5a73e-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="5a73e-107">[**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5a73e-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="5a73e-108">[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5a73e-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="5a73e-109">[**\<Bölüm >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="5a73e-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="5a73e-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="5a73e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a73e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5a73e-112">**\<Clear >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="5a73e-113">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="5a73e-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5a73e-114">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="5a73e-115">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="5a73e-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5a73e-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="5a73e-117">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a73e-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="5a73e-118">**\<kaldırma >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="5a73e-119">Önceden tanımlanmış bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5a73e-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="5a73e-120">**\<Bölüm >** için  **\<configSections >** ve  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="5a73e-121">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="5a73e-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="5a73e-122">**\<sectionGroup >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="5a73e-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="5a73e-123">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a73e-123">Defines a namespace for configuration sections.</span></span> |
