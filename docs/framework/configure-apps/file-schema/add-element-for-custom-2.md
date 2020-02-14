---
title: NameValueSectionHandler ve DictionarySectionHandler için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215433"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="de7b7-102">NameValueSectionHandler ve DictionarySectionHandler için > öğesi \<ekleyin</span><span class="sxs-lookup"><span data-stu-id="de7b7-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="de7b7-103">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="de7b7-103">Adds custom application settings.</span></span> <span data-ttu-id="de7b7-104">Her **\<add >** etiketi bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="de7b7-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="de7b7-105">[ **\<yapılandırma >** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="de7b7-105">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="de7b7-106">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="de7b7-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="de7b7-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="de7b7-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="de7b7-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de7b7-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="de7b7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de7b7-109">Attributes</span></span>

| <span data-ttu-id="de7b7-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de7b7-110">Attribute</span></span> | <span data-ttu-id="de7b7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de7b7-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="de7b7-112">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="de7b7-112">**key**</span></span>   | <span data-ttu-id="de7b7-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de7b7-113">Required attribute.</span></span><br><br><span data-ttu-id="de7b7-114">Ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="de7b7-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="de7b7-115">**value**</span><span class="sxs-lookup"><span data-stu-id="de7b7-115">**value**</span></span> | <span data-ttu-id="de7b7-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="de7b7-116">Required attribute.</span></span><br><br><span data-ttu-id="de7b7-117">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de7b7-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="de7b7-118">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="de7b7-118">Parent element</span></span>

| <span data-ttu-id="de7b7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="de7b7-119">Element</span></span> | <span data-ttu-id="de7b7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de7b7-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="de7b7-121"> **\<sectionName >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="de7b7-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="de7b7-122"><xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de7b7-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="de7b7-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="de7b7-123">Child elements</span></span>

<span data-ttu-id="de7b7-124">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="de7b7-124">None</span></span>

## <a name="example"></a><span data-ttu-id="de7b7-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="de7b7-125">Example</span></span>

<span data-ttu-id="de7b7-126">Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını gösterir ve **\<add >** öğesini kullanarak ayarları bölümüne yerleştirir:</span><span class="sxs-lookup"><span data-stu-id="de7b7-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="de7b7-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="de7b7-127">Configuration file</span></span>

<span data-ttu-id="de7b7-128">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de7b7-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="de7b7-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de7b7-129">See also</span></span>

- [<span data-ttu-id="de7b7-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="de7b7-130">Configuration file schema for the .NET Framework</span></span>](index.md)
