---
title: 'Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4faf42d3be4f76e5908068b1c2f88d7803ae18df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979348"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="99928-102">Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları</span><span class="sxs-lookup"><span data-stu-id="99928-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="99928-103">.NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamalarında [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama için güvenli bir şekilde filtre iletileri <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama:</span><span class="sxs-lookup"><span data-stu-id="99928-103">In Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="99928-104">Birini veya her ikisini aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="99928-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="99928-105">İleti filtresini çağırarak ekler <xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99928-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="99928-106">İleti filtresini çağırarak kaldırır <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99928-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="99928-107">yöntem.</span><span class="sxs-lookup"><span data-stu-id="99928-107">method.</span></span>

- <span data-ttu-id="99928-108">**Ve** pompalara iletileri çağırarak <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99928-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="99928-109">Etki</span><span class="sxs-lookup"><span data-stu-id="99928-109">Impact</span></span>

<span data-ttu-id="99928-110">Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99928-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>

<span data-ttu-id="99928-111">Bazı durumlarda bu tür uygulamaları .NET Framework'ün önceki sürümlerini hedefleyen Windows Forms uygulamaları için throw bir <xref:System.IndexOutOfRangeException> özel durum olduğunda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrılır</span><span class="sxs-lookup"><span data-stu-id="99928-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="99928-112">Azaltma</span><span class="sxs-lookup"><span data-stu-id="99928-112">Mitigation</span></span>

<span data-ttu-id="99928-113">Bu değişiklik, istenmeyen ise, uygulamalar hedef [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümü için aşağıdaki yapılandırma ayarı ekleyerek dışında tercih edebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="99928-113">If this change is undesirable, apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="99928-114">Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümünü, bu davranış için aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="99928-114">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="99928-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99928-115">See also</span></span>

- [<span data-ttu-id="99928-116">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="99928-116">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
