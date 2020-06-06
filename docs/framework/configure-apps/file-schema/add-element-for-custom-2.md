---
title: <add>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215433"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="b58c9-102">\<add>NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="b58c9-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="b58c9-103">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="b58c9-103">Adds custom application settings.</span></span> <span data-ttu-id="b58c9-104">Her **\<add>** etiket bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="b58c9-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="b58c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b58c9-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="b58c9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b58c9-106">Attributes</span></span>

| <span data-ttu-id="b58c9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b58c9-107">Attribute</span></span> | <span data-ttu-id="b58c9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b58c9-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b58c9-109">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="b58c9-109">**key**</span></span>   | <span data-ttu-id="b58c9-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b58c9-110">Required attribute.</span></span><br><br><span data-ttu-id="b58c9-111">Ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b58c9-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="b58c9-112">**deeri**</span><span class="sxs-lookup"><span data-stu-id="b58c9-112">**value**</span></span> | <span data-ttu-id="b58c9-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b58c9-113">Required attribute.</span></span><br><br><span data-ttu-id="b58c9-114">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b58c9-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b58c9-115">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="b58c9-115">Parent element</span></span>

| <span data-ttu-id="b58c9-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b58c9-116">Element</span></span> | <span data-ttu-id="b58c9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b58c9-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="b58c9-118">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="b58c9-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="b58c9-119">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="b58c9-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b58c9-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b58c9-120">Child elements</span></span>

<span data-ttu-id="b58c9-121">Yok</span><span class="sxs-lookup"><span data-stu-id="b58c9-121">None</span></span>

## <a name="example"></a><span data-ttu-id="b58c9-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b58c9-122">Example</span></span>

<span data-ttu-id="b58c9-123">Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını ve bu **\<add>** öğenin, ayarları bölümüne koymak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b58c9-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="b58c9-124">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="b58c9-124">Configuration file</span></span>

<span data-ttu-id="b58c9-125">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b58c9-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="b58c9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b58c9-126">See also</span></span>

- [<span data-ttu-id="b58c9-127">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b58c9-127">Configuration file schema for the .NET Framework</span></span>](index.md)
