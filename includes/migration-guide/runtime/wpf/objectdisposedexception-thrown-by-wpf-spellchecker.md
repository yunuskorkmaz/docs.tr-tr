---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234286"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="3a55b-101">ObjectDisposedException WPF yazım denetleyicisi tarafından oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="3a55b-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3a55b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3a55b-102">Details</span></span>|<span data-ttu-id="3a55b-103">WPF uygulamaları bazen kilitlenme ile uygulama kapatma sırasında bir <xref:System.ObjectDisposedException?displayProperty=name> yazım denetleyicisi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a55b-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="3a55b-104">Bu .NET Framework 4.7 WPF içinde düzgün biçimde özel durum işleme ve bu nedenle uygulamalar artık olumsuz şekilde etkilenir sağlama sabit.</span><span class="sxs-lookup"><span data-stu-id="3a55b-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="3a55b-105">Bazen ilk fırsat özel hata ayıklayıcı altında çalışan uygulamalarda üzere gözlenecek olmaya devam eder, bu unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3a55b-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="3a55b-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="3a55b-106">Suggestion</span></span>|<span data-ttu-id="3a55b-107">.NET Framework 4.7 yükseltme</span><span class="sxs-lookup"><span data-stu-id="3a55b-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="3a55b-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3a55b-108">Scope</span></span>|<span data-ttu-id="3a55b-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="3a55b-109">Edge</span></span>|
|<span data-ttu-id="3a55b-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="3a55b-110">Version</span></span>|<span data-ttu-id="3a55b-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3a55b-111">4.6.1</span></span>|
|<span data-ttu-id="3a55b-112">Tür</span><span class="sxs-lookup"><span data-stu-id="3a55b-112">Type</span></span>|<span data-ttu-id="3a55b-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="3a55b-113">Runtime</span></span>|
