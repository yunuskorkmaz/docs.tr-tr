---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556227"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="d35f4-101">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d35f4-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="d35f4-102">`Switch.System.Windows.Forms.UseLegacyImages`.NET Framework 4,8 ' de tanıtılan uyumluluk anahtarı .NET Core veya .net 5,0 ve sonraki sürümlerde Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d35f4-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d35f4-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d35f4-103">Change description</span></span>

<span data-ttu-id="d35f4-104">.NET Framework 4,8 ' den başlayarak, `Switch.System.Windows.Forms.UseLegacyImages` Uyumluluk anahtarı yüksek DPI ortamlarında ClickOnce senaryolarında olası görüntü ölçeklendirme sorunlarını çözmekteydi.</span><span class="sxs-lookup"><span data-stu-id="d35f4-104">Starting with .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="d35f4-105">Olarak ayarlandığında `true` , anahtar, ölçek %100 ' den büyük olarak ayarlanan yüksek DPI ekranlarda kullanıcının eski görüntü ölçeklendirmesini geri yüklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d35f4-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="d35f4-106">Daha fazla bilgi için bkz. GitHub üzerinde [.NET Framework 4,8 sürüm notları](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) .</span><span class="sxs-lookup"><span data-stu-id="d35f4-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="d35f4-107">.NET Core ve .NET 5,0 ve üzeri sürümlerde, `Switch.System.Windows.Forms.UseLegacyImages` anahtar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d35f4-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d35f4-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d35f4-108">Version introduced</span></span>

<span data-ttu-id="d35f4-109">3,0</span><span class="sxs-lookup"><span data-stu-id="d35f4-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d35f4-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d35f4-110">Recommended action</span></span>

<span data-ttu-id="d35f4-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d35f4-111">Remove the switch.</span></span> <span data-ttu-id="d35f4-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d35f4-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d35f4-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="d35f4-113">Category</span></span>

<span data-ttu-id="d35f4-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d35f4-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d35f4-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d35f4-115">Affected APIs</span></span>

- <span data-ttu-id="d35f4-116">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="d35f4-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
