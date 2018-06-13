---
title: '&lt;Clear&gt; öğesi için &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 42a44d66a3f70d0572484adf4c8dd946edf2297f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752253"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="4afff-102">\<Clear > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="4afff-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="4afff-103">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="4afff-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="4afff-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4afff-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="4afff-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4afff-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="4afff-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="4afff-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4afff-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4afff-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="4afff-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4afff-108">Attribute</span></span>

|           | <span data-ttu-id="4afff-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4afff-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4afff-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="4afff-110">**name**</span></span>  | <span data-ttu-id="4afff-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4afff-111">Required attribute.</span></span><br><br><span data-ttu-id="4afff-112">Bölüm veya kaldırmak için bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4afff-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4afff-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="4afff-113">Parent element</span></span>

|     | <span data-ttu-id="4afff-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4afff-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4afff-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="4afff-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="4afff-116">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4afff-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="4afff-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4afff-117">Child elements</span></span>

<span data-ttu-id="4afff-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4afff-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4afff-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4afff-119">Remarks</span></span>

<span data-ttu-id="4afff-120">**\<Temizleyin >** uygulamanızdan geçerli yapılandırma dosyası veya yapılandırma dosyası hiyerarşisinde daha yüksek düzeyde daha önce tanımlanan öğeyi kaldırır tüm bölümler ve bölüm grupları.</span><span class="sxs-lookup"><span data-stu-id="4afff-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4afff-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4afff-121">Example</span></span>

<span data-ttu-id="4afff-122">Bu örnek bir uygulama yapılandırma dosyasını ve makine yapılandırma dosyasını tanımlar ve nasıl kullanılacağını gösterir  **\<temizleyin >** önceden tanımlanmış bir bölümü temizlemek için bir uygulama yapılandırma dosyasında öğesi makine yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4afff-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4afff-123">İki bölüm, aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<sampleSection >** ve  **\<anotherSampleSection >**, önce uygulamayı okuyun, yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="4afff-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="4afff-124">Aşağıdaki uygulama yapılandırma dosyası kodu daha önce bildirilen tüm bölümleri temizler.</span><span class="sxs-lookup"><span data-stu-id="4afff-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="4afff-125">Uygulama kullanın veya makine yapılandırma dosyasında bildirilen bölümlerden birine ayarlarında alın.</span><span class="sxs-lookup"><span data-stu-id="4afff-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="4afff-126">Ancak, ayarlarından kullanabilirsiniz  **\<anotherSection >** sonra geldiğinden  **\<temizleyin >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="4afff-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4afff-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="4afff-127">Configuration file</span></span>

<span data-ttu-id="4afff-128">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="4afff-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4afff-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4afff-129">See also</span></span>

[<span data-ttu-id="4afff-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4afff-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
