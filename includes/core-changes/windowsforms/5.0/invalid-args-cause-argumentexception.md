---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702459"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="7967d-101">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="7967d-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="7967d-102">Bazı Windows Forms Yöntemler artık <xref:System.ArgumentException> , daha önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7967d-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7967d-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="7967d-103">Change description</span></span>

<span data-ttu-id="7967d-104">Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="7967d-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="7967d-105">.NET 5,0 ' den başlayarak, bu yöntemler artık <xref:System.ArgumentException> geçersiz bağımsız değişkenler geçirildiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7967d-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="7967d-106"><xref:System.ArgumentException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="7967d-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="7967d-107">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="7967d-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="7967d-108">Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="7967d-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="7967d-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7967d-109">Method</span></span> | <span data-ttu-id="7967d-110">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="7967d-110">Parameter name</span></span> | <span data-ttu-id="7967d-111">Koşul</span><span class="sxs-lookup"><span data-stu-id="7967d-111">Condition</span></span> | <span data-ttu-id="7967d-112">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="7967d-112">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="7967d-113">Bağımsız değişken türünde değil <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="7967d-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="7967d-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="7967d-114">5.0 Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="7967d-115">Bağımsız değişken `null` , <xref:System.String.Empty?displayProperty=nameWithType> veya boşluk.</span><span class="sxs-lookup"><span data-stu-id="7967d-115">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="7967d-116">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="7967d-116">5.0 Preview 5</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="7967d-117">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7967d-117">Version introduced</span></span>

<span data-ttu-id="7967d-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="7967d-118">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7967d-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7967d-119">Recommended action</span></span>

- <span data-ttu-id="7967d-120">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7967d-120">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="7967d-121">Gerekirse, <xref:System.ArgumentException> yöntemini çağırırken bir işleyin.</span><span class="sxs-lookup"><span data-stu-id="7967d-121">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="7967d-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="7967d-122">Category</span></span>

<span data-ttu-id="7967d-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7967d-123">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7967d-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7967d-124">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
