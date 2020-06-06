---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214790"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="895a1-102">\<appSettings> için \<clear> öğesi</span><span class="sxs-lookup"><span data-stu-id="895a1-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="895a1-103">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="895a1-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="895a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="895a1-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="895a1-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="895a1-105">Attributes</span></span>

<span data-ttu-id="895a1-106">Yok</span><span class="sxs-lookup"><span data-stu-id="895a1-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="895a1-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="895a1-107">Parent element</span></span>

|     | <span data-ttu-id="895a1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="895a1-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="895a1-109">Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="895a1-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="895a1-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="895a1-110">Child elements</span></span>

<span data-ttu-id="895a1-111">Yok</span><span class="sxs-lookup"><span data-stu-id="895a1-111">None</span></span>

## <a name="example"></a><span data-ttu-id="895a1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="895a1-112">Example</span></span>

<span data-ttu-id="895a1-113">Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="895a1-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="895a1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="895a1-114">See also</span></span>

- [<span data-ttu-id="895a1-115">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="895a1-115">Configuration file schema for the .NET Framework</span></span>](../index.md)
