---
title: <configSections> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155433"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="da535-102">\<configSections \<> için net> eleman</span><span class="sxs-lookup"><span data-stu-id="da535-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="da535-103">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="da535-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="da535-104">&nbsp; &nbsp; &nbsp; &nbsp; \*\* \<\*\* [\*\* \<konsinyon\*\*](configsections-element-for-configuration.md)>&nbsp; &nbsp;yapılandırmaBölümleri>açık>[\*\* \<\*\*](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="da535-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="da535-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da535-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="da535-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="da535-106">Attribute</span></span>

|           | <span data-ttu-id="da535-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da535-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="da535-108">**Adı**</span><span class="sxs-lookup"><span data-stu-id="da535-108">**name**</span></span>  | <span data-ttu-id="da535-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="da535-109">Required attribute.</span></span><br><br><span data-ttu-id="da535-110">Kaldırılacak bölüm veya bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da535-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="da535-111">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="da535-111">Parent element</span></span>

|     | <span data-ttu-id="da535-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da535-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="da535-113">\*\* \<configSections>\*\* Öğe</span><span class="sxs-lookup"><span data-stu-id="da535-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="da535-114">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="da535-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="da535-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="da535-115">Child elements</span></span>

<span data-ttu-id="da535-116">None</span><span class="sxs-lookup"><span data-stu-id="da535-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="da535-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da535-117">Remarks</span></span>

<span data-ttu-id="da535-118">\*\* \<Açık>\*\* öğesi, geçerli yapılandırma dosyasında veya yapılandırma dosyası hiyerarşisinde daha önce tanımlanan tüm bölümleri ve bölüm gruplarını uygulamanızdan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="da535-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="da535-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="da535-119">Example</span></span>

<span data-ttu-id="da535-120">Bu örnek, bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve makine yapılandırma dosyasında daha önce tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasındaki \*\* \<açık>\*\* öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da535-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="da535-121">Aşağıdaki makine yapılandırma dosya kodu iki bölüm bildirir, \*\* \<örnekBölüm>\*\* ve \*\* \<başka ÖrnekBölüm>\*\*, hangi uygulama yapılandırma dosyası önce okunur:</span><span class="sxs-lookup"><span data-stu-id="da535-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="da535-122">Aşağıdaki uygulama yapılandırma dosya kodu, daha önce bildirilen tüm bölümleri temizler.</span><span class="sxs-lookup"><span data-stu-id="da535-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="da535-123">Uygulama, makine yapılandırma dosyasında bildirilen bölümlerin herhangi birinde ayarları kullanamaz veya alamaz.</span><span class="sxs-lookup"><span data-stu-id="da535-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="da535-124">Ancak, \*\* \<net>\*\* öğesi sonra gelir, çünkü \*\* \<başka bir Bölüm>\*\* ayarları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da535-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="da535-125">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="da535-125">Configuration file</span></span>

<span data-ttu-id="da535-126">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da535-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="da535-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da535-127">See also</span></span>

- [<span data-ttu-id="da535-128">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="da535-128">Configuration file schema for the .NET Framework</span></span>](index.md)
