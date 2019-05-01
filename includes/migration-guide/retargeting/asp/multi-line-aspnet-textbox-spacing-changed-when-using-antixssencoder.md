---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640082"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="746a6-101">AntiXSSEncoder kullanılırken çok satırlı ASP.Net TextBox boşluğu değiştirildi</span><span class="sxs-lookup"><span data-stu-id="746a6-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

|   |   |
|---|---|
|<span data-ttu-id="746a6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="746a6-102">Details</span></span>|<span data-ttu-id="746a6-103">.NET Framework 4.0’da, <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name> kullanılırken geri göndermede çok satırlı metin kutularındaki satırların arasına ek satırlar ekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="746a6-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name>.</span></span> <span data-ttu-id="746a6-104">.NET Framework 4.5’te, web uygulaması .NET Framework 4.5’i hedefliyorsa bu ek satır sonları eklenmez</span><span class="sxs-lookup"><span data-stu-id="746a6-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>|
|<span data-ttu-id="746a6-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="746a6-105">Suggestion</span></span>|<span data-ttu-id="746a6-106">.NET Framework 4.5’e yeniden hedeflenen 4.0 web uygulamalarında, çok satırlı metin kutularının ek satır sonu eklenmeyecek şekilde geliştirilmiş olabileceğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="746a6-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="746a6-107">Bu istenmeyen bir durumsa, uygulama .NET Framework 4.5 üzerinde çalışırken .NET Framework 4.0 hedeflenerek eski davranışa dönülebilir.</span><span class="sxs-lookup"><span data-stu-id="746a6-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>|
|<span data-ttu-id="746a6-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="746a6-108">Scope</span></span>|<span data-ttu-id="746a6-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="746a6-109">Minor</span></span>|
|<span data-ttu-id="746a6-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="746a6-110">Version</span></span>|<span data-ttu-id="746a6-111">4,5</span><span class="sxs-lookup"><span data-stu-id="746a6-111">4.5</span></span>|
|<span data-ttu-id="746a6-112">Tür</span><span class="sxs-lookup"><span data-stu-id="746a6-112">Type</span></span>|<span data-ttu-id="746a6-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="746a6-113">Retargeting</span></span>|
