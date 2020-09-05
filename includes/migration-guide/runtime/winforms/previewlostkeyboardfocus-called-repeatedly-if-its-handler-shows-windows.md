---
ms.openlocfilehash: c4a3d903894027a01d32ca132d1233da9d9c3ee5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496395"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="960da-101">PreviewLostKeyboardFocus, işleyicisi bir Windows Forms ileti kutusu gösteriyorsa, tekrar tekrar çağırılır</span><span class="sxs-lookup"><span data-stu-id="960da-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="960da-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="960da-102">Details</span></span>

<span data-ttu-id="960da-103">.NET Framework 4,5 ' den başlayarak, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> bir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> işleyiciden çağırmak, ileti kutusu kapatıldığında işleyicinin yeniden başlatılmasına neden olur ve bu da muhtemelen ileti kutularından oluşan sonsuz bir döngüye neden olur.</span><span class="sxs-lookup"><span data-stu-id="960da-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="960da-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="960da-104">Suggestion</span></span>

<span data-ttu-id="960da-105">Bu sorunu geçici olarak çözmek için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="960da-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="960da-106">Yerine çağırarak bu durum önlenebilir <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="960da-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="960da-107">Bir <xref:System.Windows.UIElement.LostKeyboardFocus> olay işleyicisinden (bir olay işleyicisine karşılık gelen) ileti kutusu gösterilerek kaçınılabilir <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="960da-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="960da-108">Name</span><span class="sxs-lookup"><span data-stu-id="960da-108">Name</span></span>    | <span data-ttu-id="960da-109">Değer</span><span class="sxs-lookup"><span data-stu-id="960da-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="960da-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="960da-110">Scope</span></span>   |<span data-ttu-id="960da-111">Edge</span><span class="sxs-lookup"><span data-stu-id="960da-111">Edge</span></span>|
|<span data-ttu-id="960da-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="960da-112">Version</span></span>|<span data-ttu-id="960da-113">4,5</span><span class="sxs-lookup"><span data-stu-id="960da-113">4.5</span></span>|
|<span data-ttu-id="960da-114">Tür</span><span class="sxs-lookup"><span data-stu-id="960da-114">Type</span></span>|<span data-ttu-id="960da-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="960da-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="960da-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="960da-116">Affected APIs</span></span>

- <xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType>
- <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.ContentElement.PreviewLostKeyboardFocus`
- `E:System.Windows.IInputElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement.PreviewLostKeyboardFocus`
- `E:System.Windows.UIElement3D.PreviewLostKeyboardFocus`

-->
