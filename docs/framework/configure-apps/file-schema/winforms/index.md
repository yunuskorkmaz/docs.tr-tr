---
title: "Windows Forms yapılandırma bölümü"
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
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="421c7-102">Windows Forms yapılandırma bölümü</span><span class="sxs-lookup"><span data-stu-id="421c7-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="421c7-103">Önceden tanımlanmış yapılandırma ayarları birden çok monitör desteği, yüksek DPI desteği ve diğer gibi özelleştirilmiş uygulama ayarları hakkında bilgi almak ve Windows Forms yapılandırma ayarlarını depolamak için bir Windows Forms uygulaması izin verin.</span><span class="sxs-lookup"><span data-stu-id="421c7-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="421c7-104">Windows Forms uygulama yapılandırma ayarlarını, bir uygulama yapılandırma dosyasının depolandığı `System.Windows.Forms.ApplicationConfigurationSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="421c7-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="421c7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="421c7-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="421c7-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="421c7-106">Attributes and elements</span></span>

<span data-ttu-id="421c7-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="421c7-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="421c7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="421c7-108">Attributes</span></span>

<span data-ttu-id="421c7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="421c7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="421c7-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="421c7-110">Child elements</span></span>

<span data-ttu-id="421c7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="421c7-111">Element</span></span>  |<span data-ttu-id="421c7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="421c7-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="421c7-113">Belirli bir değerle bir yapılandırma ayarı anahtar ekler</span><span class="sxs-lookup"><span data-stu-id="421c7-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="421c7-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="421c7-114">Parent elements</span></span>

<span data-ttu-id="421c7-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="421c7-115">Element</span></span>  |<span data-ttu-id="421c7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="421c7-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="421c7-117">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="421c7-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="421c7-118">Her yapılandırma dosyası kök öğesinde ortak dil çalışma zamanı ile Windows Forms uygulamaları tarafından kullanılan</span><span class="sxs-lookup"><span data-stu-id="421c7-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="421c7-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="421c7-119">Remarks</span></span>

<span data-ttu-id="421c7-120">.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="421c7-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="421c7-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Öğesi, bir veya daha fazla alt içerebilir [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) öğeleri, her biri belirli bir yapılandırma ayarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="421c7-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="421c7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="421c7-122">See also</span></span>

<span data-ttu-id="421c7-123">[Yapılandırma dosyası şeması](../index.md) </span><span class="sxs-lookup"><span data-stu-id="421c7-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="421c7-124">Windows Forms'ta yüksek DPI desteği</span><span class="sxs-lookup"><span data-stu-id="421c7-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
