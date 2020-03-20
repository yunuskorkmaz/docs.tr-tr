---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803159"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="b8086-101">EnableViewStateMac'i artık false olarak ayarlayama</span><span class="sxs-lookup"><span data-stu-id="b8086-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b8086-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b8086-102">Details</span></span>|<span data-ttu-id="b8086-103">ASP.NET artık geliştiricilerin <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> belirtmesine veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="b8086-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="b8086-104">Görünüm durumu iletikimlik doğrulama kodu (MAC) şimdi katıştırılmış görünüm durumu olan tüm istekler için zorlanır.</span><span class="sxs-lookup"><span data-stu-id="b8086-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="b8086-105">Yalnızca EnableViewStateMac özelliğini <code>false</code> açıkça ayarlayan uygulamalar etkilenir.</span><span class="sxs-lookup"><span data-stu-id="b8086-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="b8086-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="b8086-106">Suggestion</span></span>|<span data-ttu-id="b8086-107">EnableViewStateMac'in doğru olduğu varsayılmalıdır ve ortaya çıkan MAC hataları çözülmelidir [(bu kılavuzda](https://support.microsoft.com/kb/2915218)açıklandığı gibi, MAC hatalarına neyin neden olduğuna bağlı olarak birden çok çözünürlük içerir).</span><span class="sxs-lookup"><span data-stu-id="b8086-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="b8086-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b8086-108">Scope</span></span>|<span data-ttu-id="b8086-109">Ana</span><span class="sxs-lookup"><span data-stu-id="b8086-109">Major</span></span>|
|<span data-ttu-id="b8086-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b8086-110">Version</span></span>|<span data-ttu-id="b8086-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="b8086-111">4.5.2</span></span>|
|<span data-ttu-id="b8086-112">Tür</span><span class="sxs-lookup"><span data-stu-id="b8086-112">Type</span></span>|<span data-ttu-id="b8086-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b8086-113">Runtime</span></span>|
