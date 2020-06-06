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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154536"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="90cdc-102">\<configSections> için \<remove> öğesi</span><span class="sxs-lookup"><span data-stu-id="90cdc-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="90cdc-103">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="90cdc-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="90cdc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90cdc-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="90cdc-105">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="90cdc-105">Attribute</span></span>

|           | <span data-ttu-id="90cdc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90cdc-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="90cdc-107">**ada**</span><span class="sxs-lookup"><span data-stu-id="90cdc-107">**name**</span></span>  | <span data-ttu-id="90cdc-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="90cdc-108">Required attribute.</span></span><br><br><span data-ttu-id="90cdc-109">Kaldırılacak bölüm veya bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="90cdc-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="90cdc-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="90cdc-110">Parent element</span></span>

|     | <span data-ttu-id="90cdc-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90cdc-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="90cdc-112">**\<configSections>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="90cdc-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="90cdc-113">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="90cdc-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="90cdc-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="90cdc-114">Child elements</span></span>

<span data-ttu-id="90cdc-115">Yok</span><span class="sxs-lookup"><span data-stu-id="90cdc-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="90cdc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90cdc-116">Remarks</span></span>

<span data-ttu-id="90cdc-117">**\<remove>** Uygulamanızı yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan bölümleri ve bölüm gruplarını kaldırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90cdc-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="90cdc-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="90cdc-118">Example</span></span>

<span data-ttu-id="90cdc-119">Aşağıdaki örnek, **\<remove>** daha önce makine yapılandırma dosyasında tanımlanan bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="90cdc-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="90cdc-120">Aşağıdaki makine yapılandırma dosyası kodu şu bölümü bildirir **\<sampleSection>** :</span><span class="sxs-lookup"><span data-stu-id="90cdc-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="90cdc-121">Aşağıdaki uygulama yapılandırma dosyası kodu **\<sampleSection>** bölümünü kaldırır.</span><span class="sxs-lookup"><span data-stu-id="90cdc-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="90cdc-122">Kaldırma işleminden sonra uygulama, içindeki ayarları alamaz **\<sampleSection>** .</span><span class="sxs-lookup"><span data-stu-id="90cdc-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="90cdc-123">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="90cdc-123">Configuration file</span></span>

<span data-ttu-id="90cdc-124">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="90cdc-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="90cdc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90cdc-125">See also</span></span>

- [<span data-ttu-id="90cdc-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="90cdc-126">Configuration file schema for the .NET Framework</span></span>](index.md)
