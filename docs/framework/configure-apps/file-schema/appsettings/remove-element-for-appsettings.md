---
title: <appSettings> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0695d5638589d1afe48553fe32b8d070e3938353
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119199"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="7b4d6-102">\<appSettings için > öğesini \<kaldırın ></span><span class="sxs-lookup"><span data-stu-id="7b4d6-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="7b4d6-103">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-103">Removes custom application settings.</span></span>

<span data-ttu-id="7b4d6-104">[ **\<yapılandırma >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7b4d6-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="7b4d6-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="7b4d6-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="7b4d6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**</span><span class="sxs-lookup"><span data-stu-id="7b4d6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7b4d6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b4d6-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="7b4d6-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b4d6-108">Attribute</span></span>

|         | <span data-ttu-id="7b4d6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b4d6-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="7b4d6-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="7b4d6-110">**key**</span></span> | <span data-ttu-id="7b4d6-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-111">Required attribute.</span></span><br><br><span data-ttu-id="7b4d6-112">Kaldırılacak anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="7b4d6-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="7b4d6-113">Parent element</span></span>

|     | <span data-ttu-id="7b4d6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b4d6-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7b4d6-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="7b4d6-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="7b4d6-116">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7b4d6-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7b4d6-117">Child elements</span></span>

<span data-ttu-id="7b4d6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-118">None</span></span>

## <a name="example"></a><span data-ttu-id="7b4d6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b4d6-119">Example</span></span>

<span data-ttu-id="7b4d6-120">Aşağıdaki örnek, `ApplicationName`için özel bir yapılandırma ayarının nasıl kaldırılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7b4d6-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="7b4d6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b4d6-121">See also</span></span>

- [<span data-ttu-id="7b4d6-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7b4d6-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
