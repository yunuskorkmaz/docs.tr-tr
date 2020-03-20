---
title: Yapılandırma bölümleri şema
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: 28f936e6fd7c9e7f6f895396df8e8b8d36ab9139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155329"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="f66a4-102">Yapılandırma bölümleri şema</span><span class="sxs-lookup"><span data-stu-id="f66a4-102">Configuration sections schema</span></span>

<span data-ttu-id="f66a4-103">Yapılandırma bölümleri şema yapılandırma dosyalarında özel ayarları tanımlayan öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="f66a4-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="f66a4-104">Yapılandırma dosyaları ve şemalar hakkında genel bilgi için [.NET Framework için Yapılandırma dosyası şemasına](index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f66a4-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="f66a4-105">[**\<konfigürasyon>** ](configuration-element.md) 
 [\*\* \<ConfigSections>\*\*](configsections-element-for-configuration.md) 
 [\*\* \<net>\*\*](clear-element-for-configsections.md) 
 [\*\* \<bölüm>\*\*](remove-element-for-configsections.md) 
 [\*\* \<bölümgrup>\*\*](sectiongroup-element-for-configsections.md)>
 [\*\* \<kaldırmak \*\*](section-element.md)</span><span class="sxs-lookup"><span data-stu-id="f66a4-105">[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<clear>**](clear-element-for-configsections.md)
[**\<remove>**](remove-element-for-configsections.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>

|     | <span data-ttu-id="f66a4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f66a4-106">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f66a4-107">configSections>için \*\* \<\*\* \*\* \<açık>\*\*</span><span class="sxs-lookup"><span data-stu-id="f66a4-107">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="f66a4-108">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="f66a4-108">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="f66a4-109">**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="f66a4-109">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="f66a4-110">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="f66a4-110">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="f66a4-111">**\<configBölüm>**</span><span class="sxs-lookup"><span data-stu-id="f66a4-111">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="f66a4-112">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f66a4-112">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="f66a4-113">configSections>için \*\* \<\*\* \*\* \<>kaldırmak\*\*</span><span class="sxs-lookup"><span data-stu-id="f66a4-113">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="f66a4-114">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f66a4-114">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="f66a4-115">bölüm>\*\* \<için configSections>\*\* ve \*\* \<bölümGrup>\*\* \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="f66a4-115">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="f66a4-116">Yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f66a4-116">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="f66a4-117">bölümGrup>için \*\* \<\*\* \*\* \<configSections>\*\*</span><span class="sxs-lookup"><span data-stu-id="f66a4-117">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="f66a4-118">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f66a4-118">Defines a namespace for configuration sections.</span></span> |
