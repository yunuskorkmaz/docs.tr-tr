---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088732"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="99f34-102">\<appSettings için > öğesi \<temizleyin ></span><span class="sxs-lookup"><span data-stu-id="99f34-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="99f34-103">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="99f34-103">Clears custom application settings.</span></span>

<span data-ttu-id="99f34-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="99f34-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99f34-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="99f34-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="99f34-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**</span><span class="sxs-lookup"><span data-stu-id="99f34-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="99f34-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99f34-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="99f34-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99f34-108">Attributes</span></span>

<span data-ttu-id="99f34-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="99f34-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="99f34-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="99f34-110">Parent element</span></span>

|     | <span data-ttu-id="99f34-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f34-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="99f34-112"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="99f34-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="99f34-113">Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="99f34-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="99f34-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="99f34-114">Child elements</span></span>

<span data-ttu-id="99f34-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="99f34-115">None</span></span>

## <a name="example"></a><span data-ttu-id="99f34-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="99f34-116">Example</span></span>

<span data-ttu-id="99f34-117">Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="99f34-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="99f34-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f34-118">See also</span></span>

- [<span data-ttu-id="99f34-119">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="99f34-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
