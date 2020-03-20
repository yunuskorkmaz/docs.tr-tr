---
title: <configSections> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154536"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="d5ae8-102">\<configSections \<> için> öğeyi kaldırmak</span><span class="sxs-lookup"><span data-stu-id="d5ae8-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="d5ae8-103">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="d5ae8-104">[**\<yapılandırma>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5ae8-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="d5ae8-105">&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="d5ae8-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="d5ae8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="d5ae8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d5ae8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5ae8-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="d5ae8-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d5ae8-108">Attribute</span></span>

|           | <span data-ttu-id="d5ae8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5ae8-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d5ae8-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="d5ae8-110">**name**</span></span>  | <span data-ttu-id="d5ae8-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-111">Required attribute.</span></span><br><br><span data-ttu-id="d5ae8-112">Kaldırılacak bölüm veya bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d5ae8-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="d5ae8-113">Parent element</span></span>

|     | <span data-ttu-id="d5ae8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5ae8-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d5ae8-115">\*\* \<configSections>\*\* Öğe</span><span class="sxs-lookup"><span data-stu-id="d5ae8-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d5ae8-116">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d5ae8-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d5ae8-117">Child elements</span></span>

<span data-ttu-id="d5ae8-118">None</span><span class="sxs-lookup"><span data-stu-id="d5ae8-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d5ae8-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5ae8-119">Remarks</span></span>

<span data-ttu-id="d5ae8-120">Yapılandırma dosyası \*\* \<\*\* hiyerarşisinde daha yüksek bir düzeyde tanımlanan bölümleri ve bölüm gruplarını uygulamanızdan kaldırmak için kaldır>öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d5ae8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5ae8-121">Example</span></span>

<span data-ttu-id="d5ae8-122">Aşağıdaki örnek, makine yapılandırma dosyasında daha önce tanımlanmış bir bölümü kaldırmak için uygulama yapılandırma dosyasındaki \*\* \<kaldırma>\*\* öğesini nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d5ae8-123">Aşağıdaki makine yapılandırma dosya kodu bölüm \*\* \<örnekBölüm>\*\* bildirir:</span><span class="sxs-lookup"><span data-stu-id="d5ae8-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="d5ae8-124">Aşağıdaki uygulama yapılandırma dosya kodu \*\* \<örnekBölüm>\*\* bölümünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="d5ae8-125">Kaldırıldıktan sonra, uygulama \*\* \<örnekBölüm>'ndaki \*\*ayarları alamıyor.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d5ae8-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="d5ae8-126">Configuration file</span></span>

<span data-ttu-id="d5ae8-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ae8-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5ae8-128">See also</span></span>

- [<span data-ttu-id="d5ae8-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d5ae8-129">Configuration file schema for the .NET Framework</span></span>](index.md)
