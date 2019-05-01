---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664080"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="1d6c9-101">Artık şunları EnableViewStateMac false olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d6c9-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1d6c9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1d6c9-102">Details</span></span>|<span data-ttu-id="1d6c9-103">ASP.NET belirlemek geliştiriciler artık sağlayan <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> veya <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="1d6c9-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="1d6c9-104">Görünüm durumu ileti kimlik doğrulama kodu (MAC), artık katıştırılmış görünüm durumuna sahip tüm istekler için zorlanır.</span><span class="sxs-lookup"><span data-stu-id="1d6c9-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="1d6c9-105">Yalnızca açıkça EnableViewStateMac özellik kümesine uygulamaların <code>false</code> etkilenir.</span><span class="sxs-lookup"><span data-stu-id="1d6c9-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="1d6c9-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="1d6c9-106">Suggestion</span></span>|<span data-ttu-id="1d6c9-107">EnableViewStateMac varsayıldı, doğru olmasını ve ortaya çıkan MAC hataları çözümlenemedi. (açıklandığı şekilde [bu kılavuz](https://support.microsoft.com/kb/2915218), MAC hataları neden olan özelliklerini bağlı olarak birden çok çözümler içerir).</span><span class="sxs-lookup"><span data-stu-id="1d6c9-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="1d6c9-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1d6c9-108">Scope</span></span>|<span data-ttu-id="1d6c9-109">Ana</span><span class="sxs-lookup"><span data-stu-id="1d6c9-109">Major</span></span>|
|<span data-ttu-id="1d6c9-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1d6c9-110">Version</span></span>|<span data-ttu-id="1d6c9-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1d6c9-111">4.5.2</span></span>|
|<span data-ttu-id="1d6c9-112">Tür</span><span class="sxs-lookup"><span data-stu-id="1d6c9-112">Type</span></span>|<span data-ttu-id="1d6c9-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1d6c9-113">Runtime</span></span>|
