---
ms.openlocfilehash: 9f6703c77e17ac9376aee944b891f4635dc7632e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309173"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="ba6fd-101">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="ba6fd-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="ba6fd-102">Bazı Windows Forms Yöntemler artık <xref:System.ArgumentException> , daha önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ba6fd-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ba6fd-103">Change description</span></span>

<span data-ttu-id="ba6fd-104">Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="ba6fd-105">.NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentException> geçersiz bağımsız değişkenler geçirildiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="ba6fd-106"><xref:System.ArgumentException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="ba6fd-107">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba6fd-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ba6fd-108">Version introduced</span></span>

<span data-ttu-id="ba6fd-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="ba6fd-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba6fd-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ba6fd-110">Recommended action</span></span>

- <span data-ttu-id="ba6fd-111">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="ba6fd-112">Gerekirse, <xref:System.ArgumentException> yöntemini çağırırken bir işleyin.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-112">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="ba6fd-113">Category</span><span class="sxs-lookup"><span data-stu-id="ba6fd-113">Category</span></span>

<span data-ttu-id="ba6fd-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ba6fd-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba6fd-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ba6fd-115">Affected APIs</span></span>

<span data-ttu-id="ba6fd-116">Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="ba6fd-116">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="ba6fd-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ba6fd-117">Method</span></span> | <span data-ttu-id="ba6fd-118">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="ba6fd-118">Parameter name</span></span> | <span data-ttu-id="ba6fd-119">Koşul</span><span class="sxs-lookup"><span data-stu-id="ba6fd-119">Condition</span></span> | <span data-ttu-id="ba6fd-120">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="ba6fd-120">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="ba6fd-121">Bağımsız değişken türünde değil <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="ba6fd-121">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="ba6fd-122">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="ba6fd-122">Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="ba6fd-123">Bağımsız değişken `null` , <xref:System.String.Empty?displayProperty=nameWithType> veya boşluk.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-123">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="ba6fd-124">Preview 5</span><span class="sxs-lookup"><span data-stu-id="ba6fd-124">Preview 5</span></span> |
| <xref:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)> | `culture` | <span data-ttu-id="ba6fd-125">`InputLanguage`Belirtilen kültür için alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="ba6fd-125">Unable to retrieve an `InputLanguage` for the specified culture.</span></span> | <span data-ttu-id="ba6fd-126">Önizleme 7</span><span class="sxs-lookup"><span data-stu-id="ba6fd-126">Preview 7</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`
- `M:System.Windows.Forms.InputLanguageChangedEventArgs.%23ctor(System.Globalization.CultureInfo,System.Byte)`

-->
