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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674824"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="3f586-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="3f586-102">Configuration sections schema</span></span>

<span data-ttu-id="3f586-103">Yapılandırma bölümleri şeması, yapılandırma dosyalarında özel ayarlar tanımlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3f586-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="3f586-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz. [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f586-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="3f586-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3f586-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3f586-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3f586-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="3f586-107">[**\<Temizleme >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="3f586-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="3f586-108">[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="3f586-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="3f586-109">[**\<Bölüm >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="3f586-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="3f586-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="3f586-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="3f586-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f586-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3f586-112">**\<Temizle >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="3f586-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="3f586-113">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="3f586-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="3f586-114">**\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="3f586-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="3f586-115">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="3f586-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="3f586-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="3f586-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="3f586-117">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="3f586-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="3f586-118">**\<kaldırma >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="3f586-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="3f586-119">Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3f586-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="3f586-120">**\<Bölüm >** için  **\<configSections >** ve  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="3f586-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="3f586-121">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="3f586-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="3f586-122">**\<sectionGroup >** için  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="3f586-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="3f586-123">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3f586-123">Defines a namespace for configuration sections.</span></span> |
