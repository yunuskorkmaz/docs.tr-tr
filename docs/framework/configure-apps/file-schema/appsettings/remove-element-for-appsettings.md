---
title: <appSettings> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 62913face910ae9500aa5e6f2f443db67ffd4240
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301274"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="07cbd-102">\<kaldırma > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="07cbd-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="07cbd-103">Özel uygulama ayarları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="07cbd-103">Removes custom application settings.</span></span>

<span data-ttu-id="07cbd-104">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="07cbd-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="07cbd-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="07cbd-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="07cbd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="07cbd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="07cbd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07cbd-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="07cbd-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="07cbd-108">Attribute</span></span>

|         | <span data-ttu-id="07cbd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07cbd-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="07cbd-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="07cbd-110">**key**</span></span> | <span data-ttu-id="07cbd-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="07cbd-111">Required attribute.</span></span><br><br><span data-ttu-id="07cbd-112">Kaldırılacak anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07cbd-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="07cbd-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="07cbd-113">Parent element</span></span>

|     | <span data-ttu-id="07cbd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07cbd-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="07cbd-115"> *\*\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="07cbd-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="07cbd-116">Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="07cbd-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07cbd-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="07cbd-117">Child elements</span></span>

<span data-ttu-id="07cbd-118">None</span><span class="sxs-lookup"><span data-stu-id="07cbd-118">None</span></span>

## <a name="example"></a><span data-ttu-id="07cbd-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="07cbd-119">Example</span></span>

<span data-ttu-id="07cbd-120">Aşağıdaki örnek bir özel yapılandırma ayarını kaldırın gösterilmiştir `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="07cbd-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="07cbd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07cbd-121">See also</span></span>

- [<span data-ttu-id="07cbd-122">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="07cbd-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
