---
title: <remove> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: cf9a34e47b70aaff12b29b9c5cf944d5bb15fee9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258727"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="d4e36-102">\<kaldırma > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="d4e36-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="d4e36-103">Özel uygulama ayarları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d4e36-103">Removes custom application settings.</span></span>

<span data-ttu-id="d4e36-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d4e36-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d4e36-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d4e36-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="d4e36-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="d4e36-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d4e36-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4e36-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="d4e36-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4e36-108">Attribute</span></span>

|         | <span data-ttu-id="d4e36-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e36-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="d4e36-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="d4e36-110">**key**</span></span> | <span data-ttu-id="d4e36-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d4e36-111">Required attribute.</span></span><br><br><span data-ttu-id="d4e36-112">Kaldırılacak anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4e36-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="d4e36-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="d4e36-113">Parent element</span></span>

|     | <span data-ttu-id="d4e36-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e36-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d4e36-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="d4e36-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="d4e36-116">Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d4e36-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d4e36-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d4e36-117">Child elements</span></span>

<span data-ttu-id="d4e36-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d4e36-118">None</span></span>

## <a name="example"></a><span data-ttu-id="d4e36-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4e36-119">Example</span></span>

<span data-ttu-id="d4e36-120">Aşağıdaki örnek bir özel yapılandırma ayarını kaldırın gösterilmiştir `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="d4e36-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d4e36-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e36-121">See also</span></span>

- [<span data-ttu-id="d4e36-122">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d4e36-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
