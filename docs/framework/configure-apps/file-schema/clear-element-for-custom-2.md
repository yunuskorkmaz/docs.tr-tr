---
title: NameValueSectionHandler ve DictionarySectionHandler için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e27bb7e21baf2eb4990d0107db4aae1b5f9a7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119068"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="538b7-102">NameValueSectionHandler ve DictionarySectionHandler için \<Clear > öğesi</span><span class="sxs-lookup"><span data-stu-id="538b7-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="538b7-103">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="538b7-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="538b7-104">[ **\<yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="538b7-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="538b7-105">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="538b7-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="538b7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**</span><span class="sxs-lookup"><span data-stu-id="538b7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="538b7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="538b7-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="538b7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="538b7-108">Attributes</span></span>

<span data-ttu-id="538b7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="538b7-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="538b7-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="538b7-110">Parent element</span></span>

|     | <span data-ttu-id="538b7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="538b7-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="538b7-112"> **\<sectionName >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="538b7-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="538b7-113"><xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="538b7-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="538b7-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="538b7-114">Child elements</span></span>

<span data-ttu-id="538b7-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="538b7-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="538b7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="538b7-116">Remarks</span></span>

<span data-ttu-id="538b7-117">Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış tüm ayarları kaldırmak için **\<clear >** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="538b7-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="538b7-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="538b7-118">Example</span></span>

<span data-ttu-id="538b7-119">Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında **\<clear >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="538b7-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="538b7-120">Aşağıdaki makine yapılandırma dosyası kodu, **\<mysection >** bölümünü bildirir:</span><span class="sxs-lookup"><span data-stu-id="538b7-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="538b7-121">Aşağıdaki uygulama yapılandırma dosyası kodu, tüm ayarları **\<mySection >** kaldırır.</span><span class="sxs-lookup"><span data-stu-id="538b7-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="538b7-122">Uygulama, makine yapılandırma dosyasının **\<mySection >** bölümünde belirtilen ayarlardan hiçbirini alamıyor.</span><span class="sxs-lookup"><span data-stu-id="538b7-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="538b7-123">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="538b7-123">Configuration file</span></span>

<span data-ttu-id="538b7-124">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="538b7-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="538b7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="538b7-125">See also</span></span>

- [<span data-ttu-id="538b7-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="538b7-126">Configuration file schema for the .NET Framework</span></span>](index.md)
