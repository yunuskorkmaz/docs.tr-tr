---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e76e11ef8bb39d72cb16655c948354bc326e75bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913093"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="0fe6b-102">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="0fe6b-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="0fe6b-103">Windows Forms yapılandırma ayarları, Windows Forms uygulamanın çok Monitor desteği, yüksek DPı desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="0fe6b-104">Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma dosyasının `System.Windows.Forms.ApplicationConfigurationSection` öğesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fe6b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fe6b-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fe6b-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0fe6b-106">Attributes and elements</span></span>

<span data-ttu-id="0fe6b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fe6b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0fe6b-108">Attributes</span></span>

<span data-ttu-id="0fe6b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fe6b-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0fe6b-110">Child elements</span></span>

<span data-ttu-id="0fe6b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="0fe6b-111">Element</span></span>  |<span data-ttu-id="0fe6b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fe6b-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="0fe6b-113">Belirtilen değere sahip bir yapılandırma ayarı anahtarı ekler</span><span class="sxs-lookup"><span data-stu-id="0fe6b-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="0fe6b-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0fe6b-114">Parent elements</span></span>

<span data-ttu-id="0fe6b-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="0fe6b-115">Element</span></span>  |<span data-ttu-id="0fe6b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fe6b-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="0fe6b-117">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0fe6b-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="0fe6b-118">Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe</span><span class="sxs-lookup"><span data-stu-id="0fe6b-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="0fe6b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fe6b-119">Remarks</span></span>

<span data-ttu-id="0fe6b-120">.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="0fe6b-121">Öğesi, her biri belirli bir yapılandırma ayarını [`<add>`](windows-forms-add-configuration-element.md) tanımlayan bir veya daha fazla alt öğe içerebilir. `<System.Windows.Forms.ApplicationConfigurationSection>`</span><span class="sxs-lookup"><span data-stu-id="0fe6b-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe6b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fe6b-122">See also</span></span>

- [<span data-ttu-id="0fe6b-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="0fe6b-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0fe6b-124">Windows Forms yüksek DPı desteği</span><span class="sxs-lookup"><span data-stu-id="0fe6b-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
