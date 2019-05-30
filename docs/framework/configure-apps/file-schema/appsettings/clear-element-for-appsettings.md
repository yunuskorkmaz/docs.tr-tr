---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301296"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="80995-102">\<Temizle > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="80995-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="80995-103">Özel uygulama ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="80995-103">Clears custom application settings.</span></span>

<span data-ttu-id="80995-104">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="80995-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="80995-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="80995-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="80995-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="80995-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="80995-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80995-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="80995-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80995-108">Attributes</span></span>

<span data-ttu-id="80995-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="80995-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="80995-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="80995-110">Parent element</span></span>

|     | <span data-ttu-id="80995-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80995-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="80995-112"> *\*\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="80995-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="80995-113">Dosya yolları, XML Web hizmeti URL'leri ya da başka bir özel uygulama yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="80995-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="80995-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="80995-114">Child elements</span></span>

<span data-ttu-id="80995-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="80995-115">None</span></span>

## <a name="example"></a><span data-ttu-id="80995-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="80995-116">Example</span></span>

<span data-ttu-id="80995-117">Aşağıdaki örnek, özel yapılandırma ayarlarına sıfırlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="80995-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="80995-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80995-118">See also</span></span>

- [<span data-ttu-id="80995-119">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="80995-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
