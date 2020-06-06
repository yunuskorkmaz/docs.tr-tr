---
title: <appSettings> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215487"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="b53a2-102">\<appSettings> için \<remove> öğesi</span><span class="sxs-lookup"><span data-stu-id="b53a2-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="b53a2-103">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b53a2-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="b53a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b53a2-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="b53a2-105">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b53a2-105">Attribute</span></span>

|         | <span data-ttu-id="b53a2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b53a2-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="b53a2-107">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="b53a2-107">**key**</span></span> | <span data-ttu-id="b53a2-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b53a2-108">Required attribute.</span></span><br><br><span data-ttu-id="b53a2-109">Kaldırılacak anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b53a2-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="b53a2-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="b53a2-110">Parent element</span></span>

|     | <span data-ttu-id="b53a2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b53a2-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="b53a2-112">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b53a2-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b53a2-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b53a2-113">Child elements</span></span>

<span data-ttu-id="b53a2-114">Yok</span><span class="sxs-lookup"><span data-stu-id="b53a2-114">None</span></span>

## <a name="example"></a><span data-ttu-id="b53a2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b53a2-115">Example</span></span>

<span data-ttu-id="b53a2-116">Aşağıdaki örnek için özel bir yapılandırma ayarının nasıl kaldırılacağını göstermektedir `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="b53a2-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="b53a2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b53a2-117">See also</span></span>

- [<span data-ttu-id="b53a2-118">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b53a2-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
