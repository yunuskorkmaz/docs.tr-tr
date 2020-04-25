---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158416"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="39ab2-101">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="39ab2-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="39ab2-102">Bazı Windows Forms Yöntemler artık, daha <xref:System.ArgumentException> önce hiç olmadığı geçersiz bağımsız değişkenler için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39ab2-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="39ab2-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="39ab2-103">Change description</span></span>

<span data-ttu-id="39ab2-104">Daha önce, beklenmeyen veya yanlış bir türün bağımsız değişkenlerini belirli Windows Forms yöntemlerine geçirmek belirsiz bir duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="39ab2-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="39ab2-105">.NET 5,0 ' den başlayarak, bu yöntemler artık geçersiz <xref:System.ArgumentException> bağımsız değişkenler geçirildiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39ab2-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="39ab2-106">.NET çalışma <xref:System.ArgumentException> zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="39ab2-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="39ab2-107">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="39ab2-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="39ab2-108">Aşağıdaki tabloda etkilenen Yöntemler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="39ab2-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="39ab2-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="39ab2-109">Method</span></span> | <span data-ttu-id="39ab2-110">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="39ab2-110">Parameter name</span></span> | <span data-ttu-id="39ab2-111">Koşul</span><span class="sxs-lookup"><span data-stu-id="39ab2-111">Condition</span></span> | <span data-ttu-id="39ab2-112">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="39ab2-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="39ab2-113">Bağımsız değişken türünde <xref:System.Windows.Forms.TabPage>değil.</span><span class="sxs-lookup"><span data-stu-id="39ab2-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="39ab2-114">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="39ab2-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="39ab2-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="39ab2-115">Version introduced</span></span>

<span data-ttu-id="39ab2-116">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="39ab2-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39ab2-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="39ab2-117">Recommended action</span></span>

- <span data-ttu-id="39ab2-118">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="39ab2-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="39ab2-119">Gerekirse, yöntemini çağırırken bir <xref:System.ArgumentException> işleyin.</span><span class="sxs-lookup"><span data-stu-id="39ab2-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="39ab2-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="39ab2-120">Category</span></span>

<span data-ttu-id="39ab2-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="39ab2-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39ab2-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="39ab2-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
