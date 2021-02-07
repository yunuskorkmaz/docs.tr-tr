---
description: 'İçin: öğesi hakkında daha fazla bilgi <remove><appSettings>'
title: <appSettings> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: a67003d310377ee4b896843003306201353dae91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699278"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="5d0ec-103">\<appSettings> için \<remove> öğesi</span><span class="sxs-lookup"><span data-stu-id="5d0ec-103">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="5d0ec-104">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5d0ec-104">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5d0ec-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d0ec-105">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="5d0ec-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5d0ec-106">Attribute</span></span>

|         | <span data-ttu-id="5d0ec-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d0ec-107">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="5d0ec-108">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="5d0ec-108">**key**</span></span> | <span data-ttu-id="5d0ec-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5d0ec-109">Required attribute.</span></span><br><br><span data-ttu-id="5d0ec-110">Kaldırılacak anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d0ec-110">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="5d0ec-111">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="5d0ec-111">Parent element</span></span>

|     | <span data-ttu-id="5d0ec-112">Description</span><span class="sxs-lookup"><span data-stu-id="5d0ec-112">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="5d0ec-113">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5d0ec-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5d0ec-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5d0ec-114">Child elements</span></span>

<span data-ttu-id="5d0ec-115">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5d0ec-115">None</span></span>

## <a name="example"></a><span data-ttu-id="5d0ec-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d0ec-116">Example</span></span>

<span data-ttu-id="5d0ec-117">Aşağıdaki örnek için özel bir yapılandırma ayarının nasıl kaldırılacağını göstermektedir `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="5d0ec-117">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="5d0ec-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d0ec-118">See also</span></span>

- [<span data-ttu-id="5d0ec-119">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5d0ec-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
