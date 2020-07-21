---
title: 'Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları'
description: .NET Framework 4.6.1 ve üstünü hedefleyen Windows Forms uygulamalara eklenen özel IMessageFilter. PreFilterMessage uygulaması hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475261"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="162df-103">Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları</span><span class="sxs-lookup"><span data-stu-id="162df-103">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="162df-104">.NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarda, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama şu şekilde çağrıldığında özel bir uygulama iletileri güvenli bir şekilde filtreleyebilir <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="162df-104">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="162df-105">Aşağıdakilerden birini veya her ikisini de yapar:</span><span class="sxs-lookup"><span data-stu-id="162df-105">Does one or both of the following:</span></span>

  - <span data-ttu-id="162df-106">Yöntemini çağırarak bir ileti filtresi ekler <xref:System.Windows.Forms.Application.AddMessageFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="162df-106">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="162df-107">Yöntemini çağırarak bir ileti filtresini kaldırır <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="162df-107">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="162df-108">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="162df-108">method.</span></span>

- <span data-ttu-id="162df-109">**Ve** yöntemini çağırarak pompalara iletileri <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="162df-109">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="162df-110">Etki</span><span class="sxs-lookup"><span data-stu-id="162df-110">Impact</span></span>

<span data-ttu-id="162df-111">Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="162df-111">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="162df-112">.NET Framework önceki sürümlerini hedefleyen Windows Forms uygulamalar için, bazı durumlarda bu gibi uygulamalar <xref:System.IndexOutOfRangeException> , <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında bir özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="162df-112">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="162df-113">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="162df-113">Mitigation</span></span>

<span data-ttu-id="162df-114">Bu değişiklik isten, .NET Framework 4.6.1 veya sonraki bir sürümü hedefleyen uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="162df-114">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="162df-115">Ayrıca, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 altında çalışan uygulamalar veya sonraki bir sürüm, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="162df-115">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="162df-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="162df-116">See also</span></span>

- [<span data-ttu-id="162df-117">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="162df-117">Application compatibility</span></span>](application-compatibility.md)
