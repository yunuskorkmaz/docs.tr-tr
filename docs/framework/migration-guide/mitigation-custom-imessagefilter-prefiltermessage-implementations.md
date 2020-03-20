---
title: 'Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400122"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="32fdc-102">Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="32fdc-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="32fdc-103">.NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> Forms uygulamalarında, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama çağrıldığında özel bir uygulama iletileri güvenli bir şekilde filtreleyebilir:</span><span class="sxs-lookup"><span data-stu-id="32fdc-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="32fdc-104">Aşağıdakilerden biri veya her ikisi de:</span><span class="sxs-lookup"><span data-stu-id="32fdc-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="32fdc-105"><xref:System.Windows.Forms.Application.AddMessageFilter%2A> Yöntemi arayarak bir ileti filtresi ekler.</span><span class="sxs-lookup"><span data-stu-id="32fdc-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="32fdc-106">Yöntemi çağırarak ileti filtresini <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> kaldırır.</span><span class="sxs-lookup"><span data-stu-id="32fdc-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="32fdc-107">Yöntem.</span><span class="sxs-lookup"><span data-stu-id="32fdc-107">method.</span></span>

- <span data-ttu-id="32fdc-108">**Ve** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemi arayarak mesajları pompalar.</span><span class="sxs-lookup"><span data-stu-id="32fdc-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="32fdc-109">Etki</span><span class="sxs-lookup"><span data-stu-id="32fdc-109">Impact</span></span>

<span data-ttu-id="32fdc-110">Bu değişiklik yalnızca .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="32fdc-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="32fdc-111">.NET Framework'ün önceki sürümlerini hedefleyen Windows Forms uygulamaları için, <xref:System.IndexOutOfRangeException> yöntem <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> çağrıldığında bazı durumlarda bu tür uygulamalar bir özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="32fdc-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="32fdc-112">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="32fdc-112">Mitigation</span></span>

<span data-ttu-id="32fdc-113">Bu değişiklik istenmiyorsa, .NET Framework 4.6.1 veya daha sonraki bir sürümü hedefleyen uygulamalar, [ \<](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının çalışma zamanı>bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu uygulamadan vazgeçebilir:</span><span class="sxs-lookup"><span data-stu-id="32fdc-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="32fdc-114">Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 veya daha sonraki bir sürüm [ \<](../configure-apps/file-schema/runtime/runtime-element.md) altında çalışan uygulamalar, uygulamanın yapılandırma dosyasının çalışma süresi>bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı seçebilir:</span><span class="sxs-lookup"><span data-stu-id="32fdc-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="32fdc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32fdc-115">See also</span></span>

- [<span data-ttu-id="32fdc-116">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="32fdc-116">Application compatibility</span></span>](application-compatibility.md)
