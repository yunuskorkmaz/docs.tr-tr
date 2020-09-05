---
ms.openlocfilehash: 26facb645de175d7ef0432394fc2b84f59e8437d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496811"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="25c92-101">MaxRequestLength veya maxReceivedMessageSize için hata kodları farklı</span><span class="sxs-lookup"><span data-stu-id="25c92-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="25c92-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="25c92-102">Details</span></span>

<span data-ttu-id="25c92-103">Internet Information Services (IIS) veya ASP.NET geliştirme sunucusunda barındırılan, maxRequestLength (ASP.NET) veya maxReceivedMessageSize (WCF 'de) ' da bulunan WCF Web hizmetlerindeki iletiler, HTTP durum kodu 400 (Hatalı Istek) ile 413 (Istek varlığı çok büyük) olarak değiştirilmiştir ve maxRequestLength veya maxReceivedMessageSize ayarını aşan iletiler bir <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25c92-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="25c92-104">Bu, aktarım modunun akışa alındığı durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="25c92-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25c92-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="25c92-105">Suggestion</span></span>

<span data-ttu-id="25c92-106">Bu değişiklik, ileti uzunluğunun ASP.NET veya WCF tarafından izin verilen sınırları aştığı durumlarda hata ayıklamayı kolaylaştırır. HTTP 400 durum koduna göre işlem yapan tüm kodları değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="25c92-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="25c92-107">Name</span><span class="sxs-lookup"><span data-stu-id="25c92-107">Name</span></span>    | <span data-ttu-id="25c92-108">Değer</span><span class="sxs-lookup"><span data-stu-id="25c92-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25c92-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="25c92-109">Scope</span></span>   |<span data-ttu-id="25c92-110">Edge</span><span class="sxs-lookup"><span data-stu-id="25c92-110">Edge</span></span>|
|<span data-ttu-id="25c92-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="25c92-111">Version</span></span>|<span data-ttu-id="25c92-112">4,5</span><span class="sxs-lookup"><span data-stu-id="25c92-112">4.5</span></span>|
|<span data-ttu-id="25c92-113">Tür</span><span class="sxs-lookup"><span data-stu-id="25c92-113">Type</span></span>|<span data-ttu-id="25c92-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="25c92-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="25c92-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="25c92-115">Affected APIs</span></span>

<span data-ttu-id="25c92-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="25c92-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
