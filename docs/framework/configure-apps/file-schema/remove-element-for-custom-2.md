---
title: '&lt;kaldırma&gt; NameValueSectionHandler ve DictionarySectionHandler öğesi'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 61f1c98d3f12b5aa1d25595ca28328602683b073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742919"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="1c619-102">\<kaldırma > öğesi NameValueSectionHandler ve DictionarySectionHandler için</span><span class="sxs-lookup"><span data-stu-id="1c619-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="1c619-103">Önceden tanımlanmış bir ayar kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c619-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="1c619-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1c619-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1c619-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="1c619-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="1c619-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="1c619-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1c619-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c619-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="1c619-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c619-108">Attribute</span></span>

|           | <span data-ttu-id="1c619-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c619-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1c619-110">**Anahtarı**</span><span class="sxs-lookup"><span data-stu-id="1c619-110">**key**</span></span>   | <span data-ttu-id="1c619-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1c619-111">Required attribute.</span></span><br><br><span data-ttu-id="1c619-112">Kaldırmak için ayarının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c619-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1c619-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="1c619-113">Parent element</span></span>

| <span data-ttu-id="1c619-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c619-114">Element</span></span> | <span data-ttu-id="1c619-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c619-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="1c619-116">**\<sectionName >** öğesi</span><span class="sxs-lookup"><span data-stu-id="1c619-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="1c619-117">Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1c619-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1c619-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1c619-118">Child elements</span></span>

<span data-ttu-id="1c619-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c619-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="1c619-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c619-120">Remarks</span></span>

<span data-ttu-id="1c619-121">Kullanabileceğiniz  **\<kaldırma >** öğesi yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanan uygulamanızın ayarlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c619-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="1c619-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c619-122">Example</span></span>

<span data-ttu-id="1c619-123">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="1c619-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="1c619-124">Bölümü aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<mySection >** ve iki ayarları ekler `key1` ve `key2`, ona:</span><span class="sxs-lookup"><span data-stu-id="1c619-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="1c619-125">Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır `key2` setting from  **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="1c619-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="1c619-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="1c619-126">Configuration file</span></span>

<span data-ttu-id="1c619-127">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="1c619-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c619-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c619-128">See also</span></span>

[<span data-ttu-id="1c619-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1c619-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
