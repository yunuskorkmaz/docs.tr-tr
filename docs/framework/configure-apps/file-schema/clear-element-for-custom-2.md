---
description: 'Hakkında daha fazla bilgi edinin: <clear> NameValueSectionHandler ve DictionarySectionHandler için öğesi'
title: <clear> NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: 896aa7e8f0e3b41574538fcd9e4be9d6155da889
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699239"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="029d4-103">\<clear> NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="029d4-103">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="029d4-104">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="029d4-104">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="029d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="029d4-105">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="029d4-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="029d4-106">Attributes</span></span>

<span data-ttu-id="029d4-107">Yok</span><span class="sxs-lookup"><span data-stu-id="029d4-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="029d4-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="029d4-108">Parent element</span></span>

|     | <span data-ttu-id="029d4-109">Description</span><span class="sxs-lookup"><span data-stu-id="029d4-109">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="029d4-110">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="029d4-110">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="029d4-111">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="029d4-111">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="029d4-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="029d4-112">Child elements</span></span>

<span data-ttu-id="029d4-113">Yok</span><span class="sxs-lookup"><span data-stu-id="029d4-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="029d4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="029d4-114">Remarks</span></span>

<span data-ttu-id="029d4-115">**\<clear>** Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış tüm ayarları kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="029d4-115">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="029d4-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="029d4-116">Example</span></span>

<span data-ttu-id="029d4-117">Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve **\<clear>** daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="029d4-117">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="029d4-118">Aşağıdaki makine yapılandırma dosyası kodu şu bölümü bildirir **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="029d4-118">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="029d4-119">Aşağıdaki uygulama yapılandırma dosyası kodu, tüm ayarlarını öğesinden kaldırır **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="029d4-119">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="029d4-120">Uygulama, **\<mySection>** makine yapılandırma dosyasının bölümünde ' de belirtilen ayarlardan hiçbirini alamıyor.</span><span class="sxs-lookup"><span data-stu-id="029d4-120">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="029d4-121">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="029d4-121">Configuration file</span></span>

<span data-ttu-id="029d4-122">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="029d4-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="029d4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="029d4-123">See also</span></span>

- [<span data-ttu-id="029d4-124">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="029d4-124">Configuration file schema for the .NET Framework</span></span>](index.md)
