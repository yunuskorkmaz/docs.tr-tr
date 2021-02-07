---
description: 'İçin: öğesi hakkında daha fazla bilgi <clear><appSettings>'
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 88c6a02441c038619cb74947c024de7712189915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699343"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="83dde-103">\<appSettings> için \<clear> öğesi</span><span class="sxs-lookup"><span data-stu-id="83dde-103">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="83dde-104">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="83dde-104">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="83dde-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="83dde-105">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="83dde-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83dde-106">Attributes</span></span>

<span data-ttu-id="83dde-107">Yok</span><span class="sxs-lookup"><span data-stu-id="83dde-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="83dde-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="83dde-108">Parent element</span></span>

|     | <span data-ttu-id="83dde-109">Description</span><span class="sxs-lookup"><span data-stu-id="83dde-109">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="83dde-110">Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="83dde-110">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="83dde-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="83dde-111">Child elements</span></span>

<span data-ttu-id="83dde-112">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="83dde-112">None</span></span>

## <a name="example"></a><span data-ttu-id="83dde-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="83dde-113">Example</span></span>

<span data-ttu-id="83dde-114">Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="83dde-114">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="83dde-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83dde-115">See also</span></span>

- [<span data-ttu-id="83dde-116">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="83dde-116">Configuration file schema for the .NET Framework</span></span>](../index.md)
