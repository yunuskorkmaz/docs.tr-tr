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
ms.openlocfilehash: 121b1c4b124ba07ff3bd312fd3832d3da592f486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921288"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="d3615-102">\<appSettings için \<> öğesi > Kaldır</span><span class="sxs-lookup"><span data-stu-id="d3615-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="d3615-103">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d3615-103">Removes custom application settings.</span></span>

<span data-ttu-id="d3615-104">[ **\<Yapılandırma >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d3615-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="d3615-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d3615-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="d3615-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="d3615-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d3615-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3615-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="d3615-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3615-108">Attribute</span></span>

|         | <span data-ttu-id="d3615-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3615-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="d3615-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="d3615-110">**key**</span></span> | <span data-ttu-id="d3615-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d3615-111">Required attribute.</span></span><br><br><span data-ttu-id="d3615-112">Kaldırılacak anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3615-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="d3615-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="d3615-113">Parent element</span></span>

|     | <span data-ttu-id="d3615-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3615-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d3615-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="d3615-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="d3615-116">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d3615-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d3615-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d3615-117">Child elements</span></span>

<span data-ttu-id="d3615-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="d3615-118">None</span></span>

## <a name="example"></a><span data-ttu-id="d3615-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3615-119">Example</span></span>

<span data-ttu-id="d3615-120">Aşağıdaki örnek için `ApplicationName`özel bir yapılandırma ayarının nasıl kaldırılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d3615-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d3615-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3615-121">See also</span></span>

- [<span data-ttu-id="d3615-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d3615-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
