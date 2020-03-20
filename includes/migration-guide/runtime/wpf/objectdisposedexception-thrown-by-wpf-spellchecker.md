---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802528"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="5d868-101">WPF yazım denetleyicisi tarafından atılan ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="5d868-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5d868-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5d868-102">Details</span></span>|<span data-ttu-id="5d868-103">WPF uygulamaları bazen uygulama kapatma sırasında <xref:System.ObjectDisposedException?displayProperty=name> yazım denetleyicisi tarafından atılan bir ile kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="5d868-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="5d868-104">Bu, .NET Framework 4.7 WPF'de özel durumu incelikle işleyerek ve böylece uygulamaların artık olumsuz etkilenmemesini sağlayarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="5d868-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="5d868-105">Bir hata ayıklama altında çalışan uygulamalarda zaman zaman ilk şans istisnalarının gözlenmeye devam edeceği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d868-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="5d868-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="5d868-106">Suggestion</span></span>|<span data-ttu-id="5d868-107">.NET Framework 4.7'ye yükseltin</span><span class="sxs-lookup"><span data-stu-id="5d868-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="5d868-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5d868-108">Scope</span></span>|<span data-ttu-id="5d868-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5d868-109">Edge</span></span>|
|<span data-ttu-id="5d868-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5d868-110">Version</span></span>|<span data-ttu-id="5d868-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="5d868-111">4.6.1</span></span>|
|<span data-ttu-id="5d868-112">Tür</span><span class="sxs-lookup"><span data-stu-id="5d868-112">Type</span></span>|<span data-ttu-id="5d868-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5d868-113">Runtime</span></span>|
