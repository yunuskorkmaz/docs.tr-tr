---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664622"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="cfd7f-101">ObjectDisposedException WPF yazım denetleyicisi tarafından oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="cfd7f-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cfd7f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cfd7f-102">Details</span></span>|<span data-ttu-id="cfd7f-103">WPF uygulamaları bazen kilitlenme ile uygulama kapatma sırasında bir <xref:System.ObjectDisposedException?displayProperty=name> yazım denetleyicisi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cfd7f-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="cfd7f-104">Bu .NET Framework 4.7 WPF içinde düzgün biçimde özel durum işleme ve bu nedenle uygulamalar artık olumsuz şekilde etkilenir sağlama sabit.</span><span class="sxs-lookup"><span data-stu-id="cfd7f-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="cfd7f-105">Bazen ilk fırsat özel hata ayıklayıcı altında çalışan uygulamalarda üzere gözlenecek olmaya devam eder, bu unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfd7f-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="cfd7f-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="cfd7f-106">Suggestion</span></span>|<span data-ttu-id="cfd7f-107">.NET Framework 4.7 yükseltme</span><span class="sxs-lookup"><span data-stu-id="cfd7f-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="cfd7f-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="cfd7f-108">Scope</span></span>|<span data-ttu-id="cfd7f-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="cfd7f-109">Edge</span></span>|
|<span data-ttu-id="cfd7f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="cfd7f-110">Version</span></span>|<span data-ttu-id="cfd7f-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="cfd7f-111">4.6.1</span></span>|
|<span data-ttu-id="cfd7f-112">Tür</span><span class="sxs-lookup"><span data-stu-id="cfd7f-112">Type</span></span>|<span data-ttu-id="cfd7f-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="cfd7f-113">Runtime</span></span>|
