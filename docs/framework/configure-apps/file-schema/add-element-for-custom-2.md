---
description: 'Hakkında daha fazla bilgi edinin: <add> NameValueSectionHandler ve DictionarySectionHandler için öğesi'
title: <add> NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 5a8cf22b21370e60086408f792f8137386d07aa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713058"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="02537-103">\<add> NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="02537-103">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="02537-104">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="02537-104">Adds custom application settings.</span></span> <span data-ttu-id="02537-105">Her **\<add>** etiket bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="02537-105">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="02537-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="02537-106">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="02537-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="02537-107">Attributes</span></span>

| <span data-ttu-id="02537-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="02537-108">Attribute</span></span> | <span data-ttu-id="02537-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02537-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="02537-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="02537-110">**key**</span></span>   | <span data-ttu-id="02537-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="02537-111">Required attribute.</span></span><br><br><span data-ttu-id="02537-112">Ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="02537-112">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="02537-113">**değer**</span><span class="sxs-lookup"><span data-stu-id="02537-113">**value**</span></span> | <span data-ttu-id="02537-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="02537-114">Required attribute.</span></span><br><br><span data-ttu-id="02537-115">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02537-115">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="02537-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="02537-116">Parent element</span></span>

| <span data-ttu-id="02537-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="02537-117">Element</span></span> | <span data-ttu-id="02537-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02537-118">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="02537-119">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="02537-119">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="02537-120">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="02537-120">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="02537-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="02537-121">Child elements</span></span>

<span data-ttu-id="02537-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="02537-122">None</span></span>

## <a name="example"></a><span data-ttu-id="02537-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="02537-123">Example</span></span>

<span data-ttu-id="02537-124">Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını ve bu **\<add>** öğenin, ayarları bölümüne koymak için nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="02537-124">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="02537-125">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="02537-125">Configuration file</span></span>

<span data-ttu-id="02537-126">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="02537-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="02537-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02537-127">See also</span></span>

- [<span data-ttu-id="02537-128">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="02537-128">Configuration file schema for the .NET Framework</span></span>](index.md)
