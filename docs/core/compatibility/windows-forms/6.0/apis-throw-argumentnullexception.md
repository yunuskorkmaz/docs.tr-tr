---
title: "Son değişiklik: bazı API 'Ler bağımsız değişkenler NullException oluşturur"
description: Bazı API 'Lerin bağımsız değişkenleri doğruladığını ve şimdi bir ArgumentNullException oluşturmasını .NET 6,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 01/29/2021
ms.openlocfilehash: f9d7dc8bb57ed8dc5b4ff41bda9b3bde7db7b880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804168"
---
# <a name="some-apis-throw-argumentnullexception"></a><span data-ttu-id="56a8a-103">Bazı API 'Ler bağımsız değişkenler NullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="56a8a-103">Some APIs throw ArgumentNullException</span></span>

<span data-ttu-id="56a8a-104">Bazı API 'Ler artık giriş parametrelerini doğrular ve <xref:System.ArgumentNullException> <xref:System.NullReferenceException> giriş bağımsız değişkenleriyle çağrılırsa daha önce oluşturduğu yerleri oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="56a8a-104">Some APIs now validate input parameters and throw an <xref:System.ArgumentNullException> where previously they threw a <xref:System.NullReferenceException>, if invoked with `null` input arguments.</span></span>

## <a name="change-description"></a><span data-ttu-id="56a8a-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="56a8a-105">Change description</span></span>

<span data-ttu-id="56a8a-106">Önceki .NET sürümlerinde, etkilenen API 'Ler, bir <xref:System.NullReferenceException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="56a8a-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> if invoked with an argument that's `null`.</span></span>

<span data-ttu-id="56a8a-107">.NET 6,0 ' den başlayarak, etkilenen API 'Ler bir <xref:System.ArgumentNullException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="56a8a-107">Starting in .NET 6.0, the affected APIs throw an <xref:System.ArgumentNullException> if invoked with an argument that's `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="56a8a-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="56a8a-108">Reason for change</span></span>

<span data-ttu-id="56a8a-109"><xref:System.ArgumentNullException>.NET çalışma zamanı davranışına uygun şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="56a8a-109">Throwing <xref:System.ArgumentNullException> conforms to .NET Runtime behavior.</span></span> <span data-ttu-id="56a8a-110">Özel duruma neden olan bağımsız değişkeni açıkça iletişim kurarak daha iyi bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56a8a-110">It provides a better debug experience by clearly communicating which argument caused the exception.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="56a8a-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="56a8a-111">Version introduced</span></span>

<span data-ttu-id="56a8a-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="56a8a-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="56a8a-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56a8a-113">Recommended action</span></span>

- <span data-ttu-id="56a8a-114">' Yi gözden geçirin ve gerekirse, `null` giriş bağımsız değişkenlerinin etkilenen API 'lere geçirilmesini engellemek için kodunuzu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="56a8a-114">Review and, if necessary, update your code to prevent passing `null` input arguments to the affected APIs.</span></span>
- <span data-ttu-id="56a8a-115">Kodunuz tarafından kullanılıyorsa <xref:System.NullReferenceException> , için ek bir işleyici değiştirin veya ekleyin <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="56a8a-115">If your code handles <xref:System.NullReferenceException>, replace or add an additional handler for <xref:System.ArgumentNullException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="56a8a-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56a8a-116">Affected APIs</span></span>

<span data-ttu-id="56a8a-117">Aşağıdaki tabloda etkilenen özellikler listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="56a8a-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="56a8a-118">Özellik</span><span class="sxs-lookup"><span data-stu-id="56a8a-118">Property</span></span> | <span data-ttu-id="56a8a-119">Sürüm değişti</span><span class="sxs-lookup"><span data-stu-id="56a8a-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | <span data-ttu-id="56a8a-120">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="56a8a-120">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
