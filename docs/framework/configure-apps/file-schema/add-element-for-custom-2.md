---
title: <add>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921324"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="3251b-102">\<NameValueSectionHandler ve DictionarySectionHandler için > öğesi ekleyin</span><span class="sxs-lookup"><span data-stu-id="3251b-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="3251b-103">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="3251b-103">Adds custom application settings.</span></span> <span data-ttu-id="3251b-104">**Her\<Add >** etiketi bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="3251b-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="3251b-105">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3251b-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3251b-106">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="3251b-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="3251b-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="3251b-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3251b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3251b-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="3251b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3251b-109">Attributes</span></span>

| <span data-ttu-id="3251b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3251b-110">Attribute</span></span> | <span data-ttu-id="3251b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3251b-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="3251b-112">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="3251b-112">**key**</span></span>   | <span data-ttu-id="3251b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3251b-113">Required attribute.</span></span><br><br><span data-ttu-id="3251b-114">Ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3251b-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="3251b-115">**value**</span><span class="sxs-lookup"><span data-stu-id="3251b-115">**value**</span></span> | <span data-ttu-id="3251b-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3251b-116">Required attribute.</span></span><br><br><span data-ttu-id="3251b-117">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3251b-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="3251b-118">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="3251b-118">Parent element</span></span>

| <span data-ttu-id="3251b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3251b-119">Element</span></span> | <span data-ttu-id="3251b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3251b-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="3251b-121">sectionName > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="3251b-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="3251b-122"><xref:System.Configuration.NameValueSectionHandler> Ve<xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3251b-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3251b-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3251b-123">Child elements</span></span>

<span data-ttu-id="3251b-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="3251b-124">None</span></span>

## <a name="example"></a><span data-ttu-id="3251b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3251b-125">Example</span></span>

<span data-ttu-id="3251b-126">Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını gösterir ve  **\<> Ekle** öğesini kullanarak ayarları bölümüne yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="3251b-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3251b-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="3251b-127">Configuration file</span></span>

<span data-ttu-id="3251b-128">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3251b-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3251b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3251b-129">See also</span></span>

- [<span data-ttu-id="3251b-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3251b-130">Configuration file schema for the .NET Framework</span></span>](index.md)
