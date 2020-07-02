---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617268"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="b67be-101">AntiXSSEncoder kullanılırken çok satırlı ASP.Net TextBox boşluğu değiştirildi</span><span class="sxs-lookup"><span data-stu-id="b67be-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="b67be-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b67be-102">Details</span></span>

<span data-ttu-id="b67be-103">.NET Framework 4.0’da, <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName> kullanılırken geri göndermede çok satırlı metin kutularındaki satırların arasına ek satırlar ekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="b67be-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="b67be-104">.NET Framework 4.5’te, web uygulaması .NET Framework 4.5’i hedefliyorsa bu ek satır sonları eklenmez</span><span class="sxs-lookup"><span data-stu-id="b67be-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b67be-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b67be-105">Suggestion</span></span>

<span data-ttu-id="b67be-106">.NET Framework 4.5’e yeniden hedeflenen 4.0 web uygulamalarında, çok satırlı metin kutularının ek satır sonu eklenmeyecek şekilde geliştirilmiş olabileceğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b67be-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="b67be-107">Bu istenmeyen bir durumsa, uygulama .NET Framework 4.5 üzerinde çalışırken .NET Framework 4.0 hedeflenerek eski davranışa dönülebilir.</span><span class="sxs-lookup"><span data-stu-id="b67be-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="b67be-108">Name</span><span class="sxs-lookup"><span data-stu-id="b67be-108">Name</span></span>    | <span data-ttu-id="b67be-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b67be-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b67be-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b67be-110">Scope</span></span>   | <span data-ttu-id="b67be-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="b67be-111">Minor</span></span>       |
| <span data-ttu-id="b67be-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b67be-112">Version</span></span> | <span data-ttu-id="b67be-113">4,5</span><span class="sxs-lookup"><span data-stu-id="b67be-113">4.5</span></span>         |
| <span data-ttu-id="b67be-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b67be-114">Type</span></span>    | <span data-ttu-id="b67be-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b67be-115">Retargeting</span></span> |
