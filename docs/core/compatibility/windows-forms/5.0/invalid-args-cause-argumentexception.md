---
title: 'Son değişiklik: WinForms yöntemleri şimdi ArgumentException oluşturur'
description: SWindows Forms yöntemlerinin artık geçersiz bağımsız değişkenler için bir ArgumentException oluşturması durumunda .NET 5,0 'deki önemli değişiklik hakkında bilgi edinin.
ms.date: 07/18/2020
ms.openlocfilehash: 46fe3f3b1208a5cd676e1b7546507bed36a850f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761717"
---
# <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="ed063-103">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="ed063-103">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="ed063-104">Bazı Windows Forms Yöntemler artık <xref:System.ArgumentException> , daha önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed063-104">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="ed063-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ed063-105">Change description</span></span>

<span data-ttu-id="ed063-106">Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="ed063-106">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="ed063-107">.NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentException> geçersiz bağımsız değişkenler geçirildiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed063-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="ed063-108"><xref:System.ArgumentException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ed063-108">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="ed063-109">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="ed063-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ed063-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ed063-110">Version introduced</span></span>

<span data-ttu-id="ed063-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="ed063-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ed063-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ed063-112">Recommended action</span></span>

- <span data-ttu-id="ed063-113">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ed063-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="ed063-114">Gerekirse, <xref:System.ArgumentException> yöntemini çağırırken bir işleyin.</span><span class="sxs-lookup"><span data-stu-id="ed063-114">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ed063-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ed063-115">Affected APIs</span></span>

<span data-ttu-id="ed063-116">Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="ed063-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="ed063-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ed063-117">Method</span></span> | <span data-ttu-id="ed063-118">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="ed063-118">Parameter name</span></span> | <span data-ttu-id="ed063-119">Koşul</span><span class="sxs-lookup"><span data-stu-id="ed063-119">Condition</span></span> | <span data-ttu-id="ed063-120">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="ed063-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="ed063-121">Bağımsız değişken türünde değil <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="ed063-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="ed063-122">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="ed063-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="ed063-123">Bağımsız değişken `null` , <xref:System.String.Empty?displayProperty=nameWithType> veya boşluk.</span><span class="sxs-lookup"><span data-stu-id="ed063-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="ed063-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ed063-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="ed063-125">`InputLanguage`Belirtilen kültür için alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="ed063-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="ed063-126">Önizleme 7</span><span class="sxs-lookup"><span data-stu-id="ed063-126">Preview 7</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

### Category

Windows Forms

-->
