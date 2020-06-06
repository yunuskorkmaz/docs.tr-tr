---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151838"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="5e9a4-102">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="5e9a4-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="5e9a4-103">Windows Forms yapılandırma ayarları, Windows Forms uygulamanın çok Monitor desteği, yüksek DPı desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="5e9a4-104">Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma dosyasının `System.Windows.Forms.ApplicationConfigurationSection` öğesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e9a4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e9a4-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e9a4-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5e9a4-106">Attributes and elements</span></span>

<span data-ttu-id="5e9a4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e9a4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e9a4-108">Attributes</span></span>

<span data-ttu-id="5e9a4-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e9a4-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5e9a4-110">Child elements</span></span>

<span data-ttu-id="5e9a4-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e9a4-111">Element</span></span>  |<span data-ttu-id="5e9a4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9a4-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="5e9a4-113">Belirtilen değere sahip bir yapılandırma ayarı anahtarı ekler</span><span class="sxs-lookup"><span data-stu-id="5e9a4-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="5e9a4-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5e9a4-114">Parent elements</span></span>

<span data-ttu-id="5e9a4-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e9a4-115">Element</span></span>  |<span data-ttu-id="5e9a4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9a4-116">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="5e9a4-117">Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe</span><span class="sxs-lookup"><span data-stu-id="5e9a4-117">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="5e9a4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e9a4-118">Remarks</span></span>

<span data-ttu-id="5e9a4-119">.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-119">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="5e9a4-120">`<System.Windows.Forms.ApplicationConfigurationSection>`Öğesi [`<add>`](windows-forms-add-configuration-element.md) , her biri belirli bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-120">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e9a4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9a4-121">See also</span></span>

- [<span data-ttu-id="5e9a4-122">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5e9a4-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5e9a4-123">Windows Forms yüksek DPı desteği</span><span class="sxs-lookup"><span data-stu-id="5e9a4-123">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
