---
ms.openlocfilehash: d4f0095bc9fde98087dce528c8154d9c9ac6ddb7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621836"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="bda96-101">WPF yazım denetimi beklenmeyen yollarla başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="bda96-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="bda96-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bda96-102">Details</span></span>

<span data-ttu-id="bda96-103">Buna bir dizi WPF yazım denetleyicisi sorunu dahildir:</span><span class="sxs-lookup"><span data-stu-id="bda96-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="bda96-104">WPF yazım denetleyicisi bazen<xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bda96-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="bda96-105">WPF yazım denetleyicisi <xref:System.UnauthorizedAccessException> , ' farklı kullanıcı olarak Çalıştır ' kullanılarak uygulama başlatıldığında başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="bda96-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="bda96-106">WPF yazım denetleyicisi, Almanya 'daki ' Hausnummer ' gibi bileşik sözcüklerdeki yazım hatalarını yanlış bir şekilde tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="bda96-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="bda96-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="bda96-107">Suggestion</span></span>

<span data-ttu-id="bda96-108">Sorun #1-Bu, .NET Framework 4.6.2 sorunu #2 düzeltildi-WPF yazım denetleyicisi, ' farklı kullanıcı olarak Çalıştır ' kullanılarak başlatıldığında artık desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bda96-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="bda96-109">.NET Framework 4.6.2 başlatılıyor, bu şekilde başlatılan uygulamalar artık beklenmedik şekilde kilitlenmeyecektir. bunun yerine yazım denetleyicisi sessizce devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="bda96-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="bda96-110">Sorun #3-Bu, .NET Framework 4.6.2 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="bda96-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="bda96-111">Name</span><span class="sxs-lookup"><span data-stu-id="bda96-111">Name</span></span>    | <span data-ttu-id="bda96-112">Değer</span><span class="sxs-lookup"><span data-stu-id="bda96-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bda96-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bda96-113">Scope</span></span>   |<span data-ttu-id="bda96-114">Edge</span><span class="sxs-lookup"><span data-stu-id="bda96-114">Edge</span></span>|
|<span data-ttu-id="bda96-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bda96-115">Version</span></span>|<span data-ttu-id="bda96-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="bda96-116">4.6.1</span></span>|
|<span data-ttu-id="bda96-117">Tür</span><span class="sxs-lookup"><span data-stu-id="bda96-117">Type</span></span>|<span data-ttu-id="bda96-118">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="bda96-118">Runtime</span></span>|
