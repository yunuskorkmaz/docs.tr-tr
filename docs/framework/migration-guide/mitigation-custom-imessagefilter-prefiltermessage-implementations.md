---
title: 'Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457934"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="8fbe6-102">Risk azaltma: özel IMessageFilter. PreFilterMessage uygulamaları</span><span class="sxs-lookup"><span data-stu-id="8fbe6-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="8fbe6-103">.NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarda, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında bir özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulaması iletileri güvenli bir şekilde filtreleyebilir:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="8fbe6-104">Aşağıdakilerden birini veya her ikisini de yapar:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="8fbe6-105"><xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemini çağırarak bir ileti filtresi ekler.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="8fbe6-106"><xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> yöntemini çağırarak bir ileti filtresini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="8fbe6-107">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-107">method.</span></span>

- <span data-ttu-id="8fbe6-108">**Ve** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemini çağırarak pompalara iletileri.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="8fbe6-109">Etki</span><span class="sxs-lookup"><span data-stu-id="8fbe6-109">Impact</span></span>

<span data-ttu-id="8fbe6-110">Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen Windows Forms uygulamalarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="8fbe6-111">.NET Framework önceki sürümlerini hedefleyen Windows Forms uygulamalar için, bazı durumlarda bu tür uygulamalar <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında <xref:System.IndexOutOfRangeException> özel durumu oluşturur</span><span class="sxs-lookup"><span data-stu-id="8fbe6-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="8fbe6-112">Azaltma</span><span class="sxs-lookup"><span data-stu-id="8fbe6-112">Mitigation</span></span>

<span data-ttu-id="8fbe6-113">Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 veya sonraki bir sürümü hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="8fbe6-114">Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar veya daha sonraki bir sürüm, aşağıdaki yapılandırma ayarını [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek bu davranışı kabul edebilir. uygulamanın yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="8fbe6-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="8fbe6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fbe6-115">See also</span></span>

- [<span data-ttu-id="8fbe6-116">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="8fbe6-116">Application compatibility</span></span>](application-compatibility.md)
