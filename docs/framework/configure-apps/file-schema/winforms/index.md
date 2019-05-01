---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786418"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="d9e56-102">Windows Forms Yapılandırma Bölümü</span><span class="sxs-lookup"><span data-stu-id="d9e56-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="d9e56-103">Windows Forms yapılandırma ayarlarını depolamak bir Windows Forms uygulaması izin ve özelleştirilmiş uygulama ayarları gibi çoklu monitör desteği, yüksek DPI desteği ve diğer ilgili bilgileri Al önceden tanımlanmış yapılandırma ayarları.</span><span class="sxs-lookup"><span data-stu-id="d9e56-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="d9e56-104">Windows Forms uygulama yapılandırma ayarlarını bir uygulama yapılandırma dosyasına ait depolanan `System.Windows.Forms.ApplicationConfigurationSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d9e56-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9e56-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9e56-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9e56-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="d9e56-106">Attributes and elements</span></span>

<span data-ttu-id="d9e56-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9e56-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9e56-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9e56-108">Attributes</span></span>

<span data-ttu-id="d9e56-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9e56-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9e56-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d9e56-110">Child elements</span></span>

<span data-ttu-id="d9e56-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9e56-111">Element</span></span>  |<span data-ttu-id="d9e56-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9e56-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="d9e56-113">Belirtilen bir değere sahip bir yapılandırma ayarı anahtarı ekler</span><span class="sxs-lookup"><span data-stu-id="d9e56-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d9e56-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="d9e56-114">Parent elements</span></span>

<span data-ttu-id="d9e56-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9e56-115">Element</span></span>  |<span data-ttu-id="d9e56-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9e56-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="d9e56-117">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d9e56-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="d9e56-118">Kök öğe her yapılandırma dosyasında ortak dil çalışma zamanı ile Windows Forms uygulamaları tarafından kullanılan</span><span class="sxs-lookup"><span data-stu-id="d9e56-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="d9e56-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9e56-119">Remarks</span></span>

<span data-ttu-id="d9e56-120">.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9e56-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="d9e56-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Bir veya daha fazla alt öğe içerebilir [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) öğeleri, her biri belirli yapılandırma ayarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9e56-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e56-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9e56-122">See also</span></span>

- [<span data-ttu-id="d9e56-123">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d9e56-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d9e56-124">Windows Forms'ta yüksek DPI desteği</span><span class="sxs-lookup"><span data-stu-id="d9e56-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
