---
title: <remove>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214762"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="268b7-102">\<remove>NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="268b7-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="268b7-103">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="268b7-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="268b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="268b7-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="268b7-105">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="268b7-105">Attribute</span></span>

|           | <span data-ttu-id="268b7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="268b7-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="268b7-107">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="268b7-107">**key**</span></span>   | <span data-ttu-id="268b7-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="268b7-108">Required attribute.</span></span><br><br><span data-ttu-id="268b7-109">Kaldırılacak ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="268b7-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="268b7-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="268b7-110">Parent element</span></span>

| <span data-ttu-id="268b7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="268b7-111">Element</span></span> | <span data-ttu-id="268b7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="268b7-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="268b7-113">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="268b7-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="268b7-114">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="268b7-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="268b7-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="268b7-115">Child elements</span></span>

<span data-ttu-id="268b7-116">Yok</span><span class="sxs-lookup"><span data-stu-id="268b7-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="268b7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="268b7-117">Remarks</span></span>

<span data-ttu-id="268b7-118">**\<remove>** Uygulamanızı yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan ayarları kaldırabilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="268b7-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="268b7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="268b7-119">Example</span></span>

<span data-ttu-id="268b7-120">Aşağıdaki örnek, **\<remove>** daha önce makine yapılandırma dosyasında tanımlanan ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="268b7-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="268b7-121">Aşağıdaki makine yapılandırma dosyası kodu, bölümünü bildirir **\<mySection>** ve iki ayar ekler `key1` `key2` :</span><span class="sxs-lookup"><span data-stu-id="268b7-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="268b7-122">Aşağıdaki uygulama yapılandırma dosyası kodu, bu `key2` ayarı öğesinden kaldırır **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="268b7-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="268b7-123">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="268b7-123">Configuration file</span></span>

<span data-ttu-id="268b7-124">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="268b7-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="268b7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="268b7-125">See also</span></span>

- [<span data-ttu-id="268b7-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="268b7-126">Configuration file schema for the .NET Framework</span></span>](index.md)
