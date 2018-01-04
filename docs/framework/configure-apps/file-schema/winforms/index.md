---
title: "Windows Forms Yapılandırma Bölümü"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="56902-102">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="56902-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="56902-103">Önceden tanımlanmış yapılandırma ayarları birden çok monitör desteği, yüksek DPI desteği ve diğer gibi özelleştirilmiş uygulama ayarları hakkında bilgi almak ve Windows Forms yapılandırma ayarlarını depolamak için bir Windows Forms uygulaması izin verin.</span><span class="sxs-lookup"><span data-stu-id="56902-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="56902-104">Windows Forms uygulama yapılandırma ayarlarını, bir uygulama yapılandırma dosyasının depolandığı `System.Windows.Forms.ApplicationConfigurationSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="56902-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="56902-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56902-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56902-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="56902-106">Attributes and elements</span></span>

<span data-ttu-id="56902-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="56902-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="56902-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="56902-108">Attributes</span></span>

<span data-ttu-id="56902-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="56902-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56902-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="56902-110">Child elements</span></span>

<span data-ttu-id="56902-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="56902-111">Element</span></span>  |<span data-ttu-id="56902-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56902-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="56902-113">Belirli bir değerle bir yapılandırma ayarı anahtar ekler</span><span class="sxs-lookup"><span data-stu-id="56902-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="56902-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="56902-114">Parent elements</span></span>

<span data-ttu-id="56902-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="56902-115">Element</span></span>  |<span data-ttu-id="56902-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56902-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="56902-117">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="56902-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="56902-118">Her yapılandırma dosyası kök öğesinde ortak dil çalışma zamanı ile Windows Forms uygulamaları tarafından kullanılan</span><span class="sxs-lookup"><span data-stu-id="56902-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="56902-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56902-119">Remarks</span></span>

<span data-ttu-id="56902-120">.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="56902-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="56902-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Öğesi, bir veya daha fazla alt içerebilir [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) öğeleri, her biri belirli bir yapılandırma ayarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="56902-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="56902-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56902-122">See also</span></span>

<span data-ttu-id="56902-123">[Yapılandırma dosyası şeması](../index.md) </span><span class="sxs-lookup"><span data-stu-id="56902-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="56902-124">Windows Forms'ta yüksek DPI desteği</span><span class="sxs-lookup"><span data-stu-id="56902-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
