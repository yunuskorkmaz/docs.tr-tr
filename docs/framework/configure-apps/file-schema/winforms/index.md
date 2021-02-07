---
description: 'Daha fazla bilgi edinin: Windows Forms yapılandırma bölümü'
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: f1eaf2d74c7645d6cf4580d75e23d8910628cce0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697770"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="62ec5-103">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="62ec5-103">Windows Forms Configuration Section</span></span>

<span data-ttu-id="62ec5-104">Windows Forms yapılandırma ayarları, Windows Forms uygulamanın çok Monitor desteği, yüksek DPı desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="62ec5-104">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="62ec5-105">Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma dosyasının `System.Windows.Forms.ApplicationConfigurationSection` öğesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="62ec5-105">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="62ec5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="62ec5-106">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62ec5-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="62ec5-107">Attributes and elements</span></span>

<span data-ttu-id="62ec5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62ec5-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="62ec5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="62ec5-109">Attributes</span></span>

<span data-ttu-id="62ec5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="62ec5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62ec5-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="62ec5-111">Child elements</span></span>

<span data-ttu-id="62ec5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="62ec5-112">Element</span></span>  |<span data-ttu-id="62ec5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62ec5-113">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="62ec5-114">Belirtilen değere sahip bir yapılandırma ayarı anahtarı ekler</span><span class="sxs-lookup"><span data-stu-id="62ec5-114">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="62ec5-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="62ec5-115">Parent elements</span></span>

<span data-ttu-id="62ec5-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="62ec5-116">Element</span></span>  |<span data-ttu-id="62ec5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62ec5-117">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="62ec5-118">Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe</span><span class="sxs-lookup"><span data-stu-id="62ec5-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="62ec5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62ec5-119">Remarks</span></span>

<span data-ttu-id="62ec5-120">.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="62ec5-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="62ec5-121">`<System.Windows.Forms.ApplicationConfigurationSection>`Öğesi [`<add>`](windows-forms-add-configuration-element.md) , her biri belirli bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="62ec5-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="62ec5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62ec5-122">See also</span></span>

- [<span data-ttu-id="62ec5-123">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="62ec5-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="62ec5-124">Windows Forms yüksek DPı desteği</span><span class="sxs-lookup"><span data-stu-id="62ec5-124">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
