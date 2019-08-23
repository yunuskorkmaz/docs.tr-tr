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
ms.openlocfilehash: 120733873a7ea29303fe7f82c4c324d411532897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921203"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="4546f-102">Yapılandırma bölümleri şeması</span><span class="sxs-lookup"><span data-stu-id="4546f-102">Configuration sections schema</span></span>

<span data-ttu-id="4546f-103">Yapılandırma bölümleri şeması, yapılandırma dosyalarında özel ayarları tanımlayan öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4546f-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="4546f-104">Yapılandırma dosyaları ve şemaları hakkında genel bilgi için bkz. [.NET Framework Için yapılandırma dosyası şeması](index.md).</span><span class="sxs-lookup"><span data-stu-id="4546f-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="4546f-105">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4546f-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4546f-106">[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4546f-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="4546f-107">[ **\<> Temizle**](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="4546f-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="4546f-108">[ **\<> Kaldır**](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="4546f-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="4546f-109">[ **\<Bölüm >** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="4546f-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="4546f-110"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="4546f-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="4546f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4546f-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4546f-112">configSections için > Temizle  **\<** >  **\<** </span><span class="sxs-lookup"><span data-stu-id="4546f-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4546f-113">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="4546f-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="4546f-114"> **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="4546f-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="4546f-115">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="4546f-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="4546f-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="4546f-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="4546f-117">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4546f-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="4546f-118">configSections > için  **\<> Kaldır**  **\<** </span><span class="sxs-lookup"><span data-stu-id="4546f-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="4546f-119">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4546f-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="4546f-120">**configSections > \<** **ve sectionGroupiçinBölüm>\<>**  **\<** </span><span class="sxs-lookup"><span data-stu-id="4546f-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="4546f-121">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="4546f-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="4546f-122">configSections için sectionGroup >  **\<** >  **\<** </span><span class="sxs-lookup"><span data-stu-id="4546f-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4546f-123">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4546f-123">Defines a namespace for configuration sections.</span></span> |
