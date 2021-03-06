---
title: 'Son değişiklik: NotifyIcon. Text maksimum metin uzunluğu artırıldı'
description: .NET 6 ' da, NotifyIcon. Text özelliği için en fazla metin uzunluğunun arttığı Son değişiklik hakkında bilgi edinin.
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255782"
---
# <a name="notifyicontext-maximum-text-length-increased"></a><span data-ttu-id="e2945-103">NotifyIcon.Text en fazla metin uzunluğu artırıldı</span><span class="sxs-lookup"><span data-stu-id="e2945-103">NotifyIcon.Text maximum text length increased</span></span>

<span data-ttu-id="e2945-104">Özellik için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 ile 127 arasında artar.</span><span class="sxs-lookup"><span data-stu-id="e2945-104">The maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property increased from 63 to 127.</span></span>

## <a name="change-description"></a><span data-ttu-id="e2945-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e2945-105">Change description</span></span>

<span data-ttu-id="e2945-106">Önceki .NET sürümlerinde, özelliği için izin verilen maksimum metin uzunluğu <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 63 karakterdir.</span><span class="sxs-lookup"><span data-stu-id="e2945-106">In previous .NET versions, the maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property is 63 characters.</span></span> <span data-ttu-id="e2945-107">.NET 6 ' dan başlayarak, izin verilen en fazla metin uzunluğu 127 karakterdir.</span><span class="sxs-lookup"><span data-stu-id="e2945-107">Starting in .NET 6, the maximum allowed text length is 127 characters.</span></span> <span data-ttu-id="e2945-108">Herhangi bir sürümde, <xref:System.ArgumentException> sınırdan daha uzun bir değer ayarlamaya çalıştığınızda bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e2945-108">In any version, an <xref:System.ArgumentException> is thrown when you attempt to set a value that's longer than the limit.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e2945-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e2945-109">Reason for change</span></span>

<span data-ttu-id="e2945-110">İzin verilen en büyük metin uzunluğu, [temeldeki Windows API 'sine](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080)sahip olacak şekilde artmıştı.</span><span class="sxs-lookup"><span data-stu-id="e2945-110">The maximum allowed text length was increased to be in line with the [underlying Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span></span> <span data-ttu-id="e2945-111">Windows API 'SI Windows 2000 ' de güncelleştirildi, ancak uyumluluk nedeniyle bu özellik için boyut sınırı .NET Framework ' de güncelleştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="e2945-111">The Windows API was updated in Windows 2000, but due to compatibility reasons, the size limit for this property wasn't updated in .NET Framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e2945-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e2945-112">Version introduced</span></span>

<span data-ttu-id="e2945-113">.NET 6 Preview 1</span><span class="sxs-lookup"><span data-stu-id="e2945-113">.NET 6 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e2945-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e2945-114">Recommended action</span></span>

<span data-ttu-id="e2945-115">Gerekirse, kodunuzu gözden geçirin ve var olan koruma koşullarını rahatdan yapın.</span><span class="sxs-lookup"><span data-stu-id="e2945-115">Review your code and relax any existing guard conditions, if necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e2945-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e2945-116">Affected APIs</span></span>

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
