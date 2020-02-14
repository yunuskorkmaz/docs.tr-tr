---
title: <remove> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215487"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="91f29-102">\<appSettings için > öğesini \<kaldırın ></span><span class="sxs-lookup"><span data-stu-id="91f29-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="91f29-103">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="91f29-103">Removes custom application settings.</span></span>

<span data-ttu-id="91f29-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91f29-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91f29-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="91f29-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="91f29-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**</span><span class="sxs-lookup"><span data-stu-id="91f29-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="91f29-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91f29-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="91f29-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91f29-108">Attribute</span></span>

|         | <span data-ttu-id="91f29-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91f29-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="91f29-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="91f29-110">**key**</span></span> | <span data-ttu-id="91f29-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="91f29-111">Required attribute.</span></span><br><br><span data-ttu-id="91f29-112">Kaldırılacak anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="91f29-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="91f29-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="91f29-113">Parent element</span></span>

|     | <span data-ttu-id="91f29-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91f29-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="91f29-115"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="91f29-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="91f29-116">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="91f29-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="91f29-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="91f29-117">Child elements</span></span>

<span data-ttu-id="91f29-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="91f29-118">None</span></span>

## <a name="example"></a><span data-ttu-id="91f29-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="91f29-119">Example</span></span>

<span data-ttu-id="91f29-120">Aşağıdaki örnek, `ApplicationName`için özel bir yapılandırma ayarının nasıl kaldırılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="91f29-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="91f29-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91f29-121">See also</span></span>

- [<span data-ttu-id="91f29-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="91f29-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
