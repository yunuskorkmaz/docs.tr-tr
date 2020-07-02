---
ms.openlocfilehash: 416590c7bd959eea011b7e7c5db48f22d349d0f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615746"
---
### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a><span data-ttu-id="af08c-101">SHA-256 kod imzalama sertifikası kullanan ClickOnce ile yayımlanan uygulamalar Windows 2003 ' de başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="af08c-101">Apps published with ClickOnce that use a SHA-256 code-signing certificate may fail on Windows 2003</span></span>

#### <a name="details"></a><span data-ttu-id="af08c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="af08c-102">Details</span></span>

<span data-ttu-id="af08c-103">Yürütülebilir dosya SHA256 ile imzalanır.</span><span class="sxs-lookup"><span data-stu-id="af08c-103">The executable is signed with SHA256.</span></span> <span data-ttu-id="af08c-104">Daha önce, kod imzalama sertifikasının SHA-1 veya SHA-256 olmasına bakılmaksızın SHA1 ile imzalanmıştı.</span><span class="sxs-lookup"><span data-stu-id="af08c-104">Previously, it was signed with SHA1 regardless of whether the code-signing certificate was SHA-1 or SHA-256.</span></span> <span data-ttu-id="af08c-105">Bu için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="af08c-105">This applies to:</span></span>

- <span data-ttu-id="af08c-106">Visual Studio 2012 veya üzeri ile oluşturulan tüm uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="af08c-106">All applications built with Visual Studio 2012 or later.</span></span>
- <span data-ttu-id="af08c-107">.NET Framework 4,5 olan sistemlerde Visual Studio 2010 veya daha önceki bir sürümü ile oluşturulan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="af08c-107">Applications built with Visual Studio 2010 or earlier on systems with the .NET Framework 4.5 present.</span></span>
<span data-ttu-id="af08c-108">Ayrıca, .NET Framework 4,5 veya üzeri bir sürüm varsa, derlenen .NET Framework sürümden bağımsız olarak SHA-256 sertifikaları için de ClickOnce bildirimi de 256 imzalanır.</span><span class="sxs-lookup"><span data-stu-id="af08c-108">In addition, if the .NET Framework 4.5 or later is present, the ClickOnce manifest is also signed with SHA-256 for SHA-256 certificates regardless of the .NET Framework version against which it was compiled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af08c-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="af08c-109">Suggestion</span></span>

<span data-ttu-id="af08c-110">ClickOnce yürütülebiliri imzalanırken değişiklik yalnızca Windows Server 2003 sistemlerini etkiler; Bu, KB 938397 ' nin yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af08c-110">The change in signing the ClickOnce executable affects only Windows Server 2003 systems; they require that KB 938397 be installed.</span></span> <span data-ttu-id="af08c-111">Bir uygulama .NET Framework 4,0 veya önceki sürümleri hedefliyorsa, .NET Framework 4,5 veya sonraki bir sürümde bir çalışma zamanı bağımlılığı sunarak, bildirimi SHA-256 ile imzalamada değişiklik.</span><span class="sxs-lookup"><span data-stu-id="af08c-111">The change in signing the manifest with SHA-256 even when an app targets the .NET Framework 4.0 or earlier versions introduces a runtime dependency on the .NET Framework 4.5 or a later version.</span></span>

| <span data-ttu-id="af08c-112">Name</span><span class="sxs-lookup"><span data-stu-id="af08c-112">Name</span></span>    | <span data-ttu-id="af08c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="af08c-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af08c-114">Kapsam</span><span class="sxs-lookup"><span data-stu-id="af08c-114">Scope</span></span>   | <span data-ttu-id="af08c-115">Edge</span><span class="sxs-lookup"><span data-stu-id="af08c-115">Edge</span></span>        |
| <span data-ttu-id="af08c-116">Sürüm</span><span class="sxs-lookup"><span data-stu-id="af08c-116">Version</span></span> | <span data-ttu-id="af08c-117">4,5</span><span class="sxs-lookup"><span data-stu-id="af08c-117">4.5</span></span>         |
| <span data-ttu-id="af08c-118">Tür</span><span class="sxs-lookup"><span data-stu-id="af08c-118">Type</span></span>    | <span data-ttu-id="af08c-119">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="af08c-119">Retargeting</span></span> |
