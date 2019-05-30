---
title: <add> NameValueSectionHandler ve DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 3bbe4ad6559e324db5853b95e797f50a7b908dcb
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301426"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="0692c-102">\<Ekle > NameValueSectionHandler ve DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="0692c-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="0692c-103">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="0692c-103">Adds custom application settings.</span></span> <span data-ttu-id="0692c-104">Her **\<Ekle >** /etiketinde bir anahtar/değer çifti.</span><span class="sxs-lookup"><span data-stu-id="0692c-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="0692c-105">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0692c-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0692c-106">&nbsp;&nbsp;[ **\<sectionName >** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="0692c-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="0692c-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="0692c-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0692c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0692c-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="0692c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0692c-109">Attributes</span></span>

| <span data-ttu-id="0692c-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0692c-110">Attribute</span></span> | <span data-ttu-id="0692c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0692c-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0692c-112">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="0692c-112">**key**</span></span>   | <span data-ttu-id="0692c-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0692c-113">Required attribute.</span></span><br><br><span data-ttu-id="0692c-114">Ayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0692c-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="0692c-115">**value**</span><span class="sxs-lookup"><span data-stu-id="0692c-115">**value**</span></span> | <span data-ttu-id="0692c-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0692c-116">Required attribute.</span></span><br><br><span data-ttu-id="0692c-117">Bir ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0692c-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0692c-118">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="0692c-118">Parent element</span></span>

| <span data-ttu-id="0692c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0692c-119">Element</span></span> | <span data-ttu-id="0692c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0692c-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="0692c-121"> *\*\<sectionName >** öğesi</span><span class="sxs-lookup"><span data-stu-id="0692c-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="0692c-122">Ayarları kullanan özel yapılandırma bölümleri tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="0692c-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0692c-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0692c-123">Child elements</span></span>

<span data-ttu-id="0692c-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="0692c-124">None</span></span>

## <a name="example"></a><span data-ttu-id="0692c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0692c-125">Example</span></span>

<span data-ttu-id="0692c-126">Aşağıdaki örnek bir özel bir yapılandırma bölümünü tanımlama ve kullanma işlemi gösterilmektedir  **\<Ekle >** ayarları bölümüne yerleştirmek için öğe:</span><span class="sxs-lookup"><span data-stu-id="0692c-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="0692c-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="0692c-127">Configuration file</span></span>

<span data-ttu-id="0692c-128">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="0692c-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0692c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0692c-129">See also</span></span>

- [<span data-ttu-id="0692c-130">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0692c-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
