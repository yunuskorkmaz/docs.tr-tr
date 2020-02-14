---
title: <clear> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214790"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="b8176-102">\<appSettings için > öğesi \<temizleyin ></span><span class="sxs-lookup"><span data-stu-id="b8176-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="b8176-103">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="b8176-103">Clears custom application settings.</span></span>

<span data-ttu-id="b8176-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8176-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8176-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b8176-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="b8176-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**</span><span class="sxs-lookup"><span data-stu-id="b8176-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b8176-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8176-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="b8176-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8176-108">Attributes</span></span>

<span data-ttu-id="b8176-109">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b8176-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="b8176-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="b8176-110">Parent element</span></span>

|     | <span data-ttu-id="b8176-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8176-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b8176-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="b8176-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="b8176-113">Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8176-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b8176-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b8176-114">Child elements</span></span>

<span data-ttu-id="b8176-115">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b8176-115">None</span></span>

## <a name="example"></a><span data-ttu-id="b8176-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8176-116">Example</span></span>

<span data-ttu-id="b8176-117">Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b8176-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="b8176-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8176-118">See also</span></span>

- [<span data-ttu-id="b8176-119">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b8176-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
