---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774451"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="7fb3f-101">AntiXSSEncoder kullanılırken çok satırlı ASP.Net TextBox boşluğu değiştirildi</span><span class="sxs-lookup"><span data-stu-id="7fb3f-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7fb3f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7fb3f-102">Details</span></span>|<span data-ttu-id="7fb3f-103">.NET Framework 4.0’da, <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name> kullanılırken geri göndermede çok satırlı metin kutularındaki satırların arasına ek satırlar ekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="7fb3f-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>.</span></span> <span data-ttu-id="7fb3f-104">.NET Framework 4.5’te, web uygulaması .NET Framework 4.5’i hedefliyorsa bu ek satır sonları eklenmez</span><span class="sxs-lookup"><span data-stu-id="7fb3f-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>|
|<span data-ttu-id="7fb3f-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="7fb3f-105">Suggestion</span></span>|<span data-ttu-id="7fb3f-106">.NET Framework 4.5’e yeniden hedeflenen 4.0 web uygulamalarında, çok satırlı metin kutularının ek satır sonu eklenmeyecek şekilde geliştirilmiş olabileceğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7fb3f-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="7fb3f-107">Bu istenmeyen bir durumsa, uygulama .NET Framework 4.5 üzerinde çalışırken .NET Framework 4.0 hedeflenerek eski davranışa dönülebilir.</span><span class="sxs-lookup"><span data-stu-id="7fb3f-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>|
|<span data-ttu-id="7fb3f-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7fb3f-108">Scope</span></span>|<span data-ttu-id="7fb3f-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="7fb3f-109">Minor</span></span>|
|<span data-ttu-id="7fb3f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7fb3f-110">Version</span></span>|<span data-ttu-id="7fb3f-111">4,5</span><span class="sxs-lookup"><span data-stu-id="7fb3f-111">4.5</span></span>|
|<span data-ttu-id="7fb3f-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7fb3f-112">Type</span></span>|<span data-ttu-id="7fb3f-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7fb3f-113">Retargeting</span></span>|
