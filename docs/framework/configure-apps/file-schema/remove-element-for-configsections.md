---
title: <configSections> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f57dc9279c107ce751f71c2998670ab992db162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118430"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="ba05c-102">\<configSections için > öğesini \<kaldırın ></span><span class="sxs-lookup"><span data-stu-id="ba05c-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="ba05c-103">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ba05c-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="ba05c-104">[ **\<yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ba05c-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="ba05c-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ba05c-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="ba05c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**</span><span class="sxs-lookup"><span data-stu-id="ba05c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ba05c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba05c-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="ba05c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba05c-108">Attribute</span></span>

|           | <span data-ttu-id="ba05c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba05c-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ba05c-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="ba05c-110">**name**</span></span>  | <span data-ttu-id="ba05c-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ba05c-111">Required attribute.</span></span><br><br><span data-ttu-id="ba05c-112">Kaldırılacak bölüm veya bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba05c-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ba05c-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="ba05c-113">Parent element</span></span>

|     | <span data-ttu-id="ba05c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba05c-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ba05c-115"> **\<configSections >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ba05c-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="ba05c-116">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba05c-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ba05c-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ba05c-117">Child elements</span></span>

<span data-ttu-id="ba05c-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba05c-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ba05c-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba05c-119">Remarks</span></span>

<span data-ttu-id="ba05c-120">Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış bölümleri ve bölüm gruplarını kaldırmak için **\<remove >** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba05c-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ba05c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba05c-121">Example</span></span>

<span data-ttu-id="ba05c-122">Aşağıdaki örnek, daha önce makine yapılandırma dosyasında tanımlanan bir bölümü kaldırmak üzere bir uygulama yapılandırma dosyasında **\<remove >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba05c-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ba05c-123">Aşağıdaki makine yapılandırma dosyası kodu, **\<samplesection >** bölümünü bildirir:</span><span class="sxs-lookup"><span data-stu-id="ba05c-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="ba05c-124">Aşağıdaki uygulama yapılandırma dosyası kodu **\<samplesection >** bölümünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ba05c-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="ba05c-125">Kaldırma işleminden sonra uygulama, **\<sampleSection**içindeki ayarları alamaz.</span><span class="sxs-lookup"><span data-stu-id="ba05c-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ba05c-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="ba05c-126">Configuration file</span></span>

<span data-ttu-id="ba05c-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba05c-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba05c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba05c-128">See also</span></span>

- [<span data-ttu-id="ba05c-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ba05c-129">Configuration file schema for the .NET Framework</span></span>](index.md)
