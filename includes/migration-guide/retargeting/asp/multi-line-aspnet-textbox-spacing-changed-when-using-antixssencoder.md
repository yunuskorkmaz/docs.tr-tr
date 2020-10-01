---
ms.openlocfilehash: 53860bb867522503c5cb9bd35e25fadd00a116a2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609173"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="5ad93-101">AntiXSSEncoder kullanılırken çok satırlı ASP.NET metin kutusu aralığı değişti</span><span class="sxs-lookup"><span data-stu-id="5ad93-101">Multi-line ASP.NET TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="5ad93-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5ad93-102">Details</span></span>

<span data-ttu-id="5ad93-103">.NET Framework 4.0’da, <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName> kullanılırken geri göndermede çok satırlı metin kutularındaki satırların arasına ek satırlar ekleniyordu.</span><span class="sxs-lookup"><span data-stu-id="5ad93-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="5ad93-104">.NET Framework 4.5’te, web uygulaması .NET Framework 4.5’i hedefliyorsa bu ek satır sonları eklenmez</span><span class="sxs-lookup"><span data-stu-id="5ad93-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5ad93-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="5ad93-105">Suggestion</span></span>

<span data-ttu-id="5ad93-106">.NET Framework 4.5’e yeniden hedeflenen 4.0 web uygulamalarında, çok satırlı metin kutularının ek satır sonu eklenmeyecek şekilde geliştirilmiş olabileceğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5ad93-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="5ad93-107">Bu istenmeyen bir durumsa, uygulama .NET Framework 4.5 üzerinde çalışırken .NET Framework 4.0 hedeflenerek eski davranışa dönülebilir.</span><span class="sxs-lookup"><span data-stu-id="5ad93-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="5ad93-108">Name</span><span class="sxs-lookup"><span data-stu-id="5ad93-108">Name</span></span>    | <span data-ttu-id="5ad93-109">Değer</span><span class="sxs-lookup"><span data-stu-id="5ad93-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5ad93-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5ad93-110">Scope</span></span>   | <span data-ttu-id="5ad93-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="5ad93-111">Minor</span></span>       |
| <span data-ttu-id="5ad93-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5ad93-112">Version</span></span> | <span data-ttu-id="5ad93-113">4,5</span><span class="sxs-lookup"><span data-stu-id="5ad93-113">4.5</span></span>         |
| <span data-ttu-id="5ad93-114">Tür</span><span class="sxs-lookup"><span data-stu-id="5ad93-114">Type</span></span>    | <span data-ttu-id="5ad93-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="5ad93-115">Retargeting</span></span> |
