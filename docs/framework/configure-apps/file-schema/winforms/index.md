---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4a54df0b6301f1aae14d5561c91c6792cb0a1620
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109820"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="4faa6-102">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="4faa6-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="4faa6-103">Windows Forms yapılandırma ayarları, Windows Forms uygulamanın çok Monitor desteği, yüksek DPı desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4faa6-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="4faa6-104">Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma dosyasının `System.Windows.Forms.ApplicationConfigurationSection` öğesinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="4faa6-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="4faa6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4faa6-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4faa6-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4faa6-106">Attributes and elements</span></span>

<span data-ttu-id="4faa6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4faa6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4faa6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4faa6-108">Attributes</span></span>

<span data-ttu-id="4faa6-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4faa6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4faa6-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4faa6-110">Child elements</span></span>

<span data-ttu-id="4faa6-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="4faa6-111">Element</span></span>  |<span data-ttu-id="4faa6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4faa6-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="4faa6-113">Belirtilen değere sahip bir yapılandırma ayarı anahtarı ekler</span><span class="sxs-lookup"><span data-stu-id="4faa6-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="4faa6-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4faa6-114">Parent elements</span></span>

<span data-ttu-id="4faa6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4faa6-115">Element</span></span>  |<span data-ttu-id="4faa6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4faa6-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="4faa6-117">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4faa6-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="4faa6-118">Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe</span><span class="sxs-lookup"><span data-stu-id="4faa6-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="4faa6-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4faa6-119">Remarks</span></span>

<span data-ttu-id="4faa6-120">.NET Framework 4,7 ' den başlayarak `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4faa6-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="4faa6-121">`<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, her biri belirli bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe [`<add>`](windows-forms-add-configuration-element.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4faa6-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="4faa6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4faa6-122">See also</span></span>

- [<span data-ttu-id="4faa6-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4faa6-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4faa6-124">Windows Forms yüksek DPı desteği</span><span class="sxs-lookup"><span data-stu-id="4faa6-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
