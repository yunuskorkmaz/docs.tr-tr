---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760446"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="e335e-101">WPF yazdırma yığını güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="e335e-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e335e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e335e-102">Details</span></span>|<span data-ttu-id="e335e-103">WPF'nin yazdırma API'lerini kullanarak <xref:System.Printing.PrintQueue?displayProperty=name> penceresinin Yazdır belge paket API artık kullanım dışı XPS yazdırma API yerine artık çağırın.</span><span class="sxs-lookup"><span data-stu-id="e335e-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="e335e-104">Bakım kolaylığı düşünülerek ile değişiklik yapılmıştır; kullanıcıların ne geliştiricilerin herhangi bir değişiklik davranış veya API kullanımı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e335e-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="e335e-105">Yeni yazdırma yığın içinde Windows 10 Creators Update çalıştıran, varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="e335e-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="e335e-106">Eski yazdırma yığın hala eski Windows sürümlerinde yalnızca önceki gibi çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e335e-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="e335e-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="e335e-107">Suggestion</span></span>|<span data-ttu-id="e335e-108">Eski yığın içinde Windows 10 Creators Update kullanmak için ayarlanmış <code>UseXpsOMPrinting</code> REG_DWORD değeri <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> kayıt defteri anahtarına <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="e335e-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="e335e-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e335e-109">Scope</span></span>|<span data-ttu-id="e335e-110">Kenar</span><span class="sxs-lookup"><span data-stu-id="e335e-110">Edge</span></span>|
|<span data-ttu-id="e335e-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e335e-111">Version</span></span>|<span data-ttu-id="e335e-112">4.7</span><span class="sxs-lookup"><span data-stu-id="e335e-112">4.7</span></span>|
|<span data-ttu-id="e335e-113">Tür</span><span class="sxs-lookup"><span data-stu-id="e335e-113">Type</span></span>|<span data-ttu-id="e335e-114">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e335e-114">Runtime</span></span>|

