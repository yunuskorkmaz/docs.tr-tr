---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802528"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="bb83c-101">ObjectDisposedException WPF yazım denetleyicisi tarafından oluşturuldu</span><span class="sxs-lookup"><span data-stu-id="bb83c-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bb83c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bb83c-102">Details</span></span>|<span data-ttu-id="bb83c-103">WPF uygulamaları bazen kilitlenme ile uygulama kapatma sırasında bir <xref:System.ObjectDisposedException?displayProperty=name> yazım denetleyicisi tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bb83c-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="bb83c-104">Bu .NET Framework 4.7 WPF içinde düzgün biçimde özel durum işleme ve bu nedenle uygulamalar artık olumsuz şekilde etkilenir sağlama sabit.</span><span class="sxs-lookup"><span data-stu-id="bb83c-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="bb83c-105">Bazen ilk fırsat özel hata ayıklayıcı altında çalışan uygulamalarda üzere gözlenecek olmaya devam eder, bu unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb83c-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="bb83c-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="bb83c-106">Suggestion</span></span>|<span data-ttu-id="bb83c-107">.NET Framework 4.7 yükseltme</span><span class="sxs-lookup"><span data-stu-id="bb83c-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="bb83c-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bb83c-108">Scope</span></span>|<span data-ttu-id="bb83c-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="bb83c-109">Edge</span></span>|
|<span data-ttu-id="bb83c-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bb83c-110">Version</span></span>|<span data-ttu-id="bb83c-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="bb83c-111">4.6.1</span></span>|
|<span data-ttu-id="bb83c-112">Tür</span><span class="sxs-lookup"><span data-stu-id="bb83c-112">Type</span></span>|<span data-ttu-id="bb83c-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="bb83c-113">Runtime</span></span>|

