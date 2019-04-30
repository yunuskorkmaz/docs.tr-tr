---
title: <appSettings> için <remove> öğesi
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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705395"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="9b704-102">\<kaldırma > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="9b704-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="9b704-103">Özel uygulama ayarları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9b704-103">Removes custom application settings.</span></span>

<span data-ttu-id="9b704-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9b704-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9b704-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9b704-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="9b704-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="9b704-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9b704-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b704-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="9b704-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9b704-108">Attribute</span></span>

|         | <span data-ttu-id="9b704-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b704-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="9b704-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="9b704-110">**key**</span></span> | <span data-ttu-id="9b704-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9b704-111">Required attribute.</span></span><br><br><span data-ttu-id="9b704-112">Kaldırılacak anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b704-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="9b704-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="9b704-113">Parent element</span></span>

|     | <span data-ttu-id="9b704-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b704-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9b704-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="9b704-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="9b704-116">Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="9b704-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9b704-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9b704-117">Child elements</span></span>

<span data-ttu-id="9b704-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="9b704-118">None</span></span>

## <a name="example"></a><span data-ttu-id="9b704-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b704-119">Example</span></span>

<span data-ttu-id="9b704-120">Aşağıdaki örnek bir özel yapılandırma ayarını kaldırın gösterilmiştir `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="9b704-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9b704-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b704-121">See also</span></span>

- [<span data-ttu-id="9b704-122">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9b704-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
