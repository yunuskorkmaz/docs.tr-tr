---
title: <clear>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214752"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6b1f3-102">\<clear>NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="6b1f3-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6b1f3-103">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="6b1f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b1f3-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="6b1f3-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b1f3-105">Attributes</span></span>

<span data-ttu-id="6b1f3-106">Yok</span><span class="sxs-lookup"><span data-stu-id="6b1f3-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6b1f3-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="6b1f3-107">Parent element</span></span>

|     | <span data-ttu-id="6b1f3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b1f3-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="6b1f3-109">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6b1f3-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="6b1f3-110">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="6b1f3-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6b1f3-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6b1f3-111">Child elements</span></span>

<span data-ttu-id="6b1f3-112">Yok</span><span class="sxs-lookup"><span data-stu-id="6b1f3-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6b1f3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b1f3-113">Remarks</span></span>

<span data-ttu-id="6b1f3-114">**\<clear>** Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış tüm ayarları kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="6b1f3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b1f3-115">Example</span></span>

<span data-ttu-id="6b1f3-116">Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve **\<clear>** daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="6b1f3-117">Aşağıdaki makine yapılandırma dosyası kodu şu bölümü bildirir **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="6b1f3-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="6b1f3-118">Aşağıdaki uygulama yapılandırma dosyası kodu, tüm ayarlarını öğesinden kaldırır **\<mySection>** .</span><span class="sxs-lookup"><span data-stu-id="6b1f3-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="6b1f3-119">Uygulama, **\<mySection>** makine yapılandırma dosyasının bölümünde ' de belirtilen ayarlardan hiçbirini alamıyor.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6b1f3-120">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="6b1f3-120">Configuration file</span></span>

<span data-ttu-id="6b1f3-121">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b1f3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b1f3-122">See also</span></span>

- [<span data-ttu-id="6b1f3-123">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6b1f3-123">Configuration file schema for the .NET Framework</span></span>](index.md)
