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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: edd2b2e11b02d69b7bba7c3cc7d8a9a0814e0c51
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743517"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="88b69-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="88b69-102">Configuration sections schema</span></span>

<span data-ttu-id="88b69-103">Yapılandırma bölümleri şeması yapılandırma dosyalarında özel ayarlar tanımlama öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="88b69-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="88b69-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz: [.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="88b69-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="88b69-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="88b69-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="88b69-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="88b69-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="88b69-107">[**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="88b69-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="88b69-108">[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="88b69-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="88b69-109">[**\<Bölüm >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="88b69-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="88b69-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="88b69-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="88b69-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88b69-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="88b69-112">**\<Clear >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="88b69-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="88b69-113">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="88b69-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="88b69-114">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="88b69-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="88b69-115">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="88b69-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="88b69-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="88b69-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="88b69-117">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="88b69-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="88b69-118">**\<kaldırma >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="88b69-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="88b69-119">Önceden tanımlanmış bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="88b69-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="88b69-120">**\<Bölüm >** için  **\<configSections >** ve  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="88b69-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="88b69-121">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="88b69-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="88b69-122">**\<sectionGroup >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="88b69-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="88b69-123">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="88b69-123">Defines a namespace for configuration sections.</span></span> |
