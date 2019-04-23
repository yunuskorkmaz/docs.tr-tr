---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981716"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="8d029-101">Hata kodları maxRequestLength veya maxReceivedMessageSize için farklıdır</span><span class="sxs-lookup"><span data-stu-id="8d029-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8d029-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8d029-102">Details</span></span>|<span data-ttu-id="8d029-103">Wcf'de ileti web maxRequestLength (ASP.NET'te) aşan Internet Information Services (IIS) veya ASP.NET Development Server'da barındırılan hizmetleri veya maxReceivedMessageSize (wcf'de) sahip farklı hata değişkenden HTTP durum kodu 400 (Hatalı istek değişti ) iken 413 (istek varlığı çok büyük) ve maxRequestLength veya maxReceivedMessageSize ayarını aşan iletiler throw bir <xref:System.ServiceModel.ProtocolException?displayProperty=name> özel durum.</span><span class="sxs-lookup"><span data-stu-id="8d029-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=name> exception.</span></span> <span data-ttu-id="8d029-104">Bu, aktarım modunun akış yoluyla servis taleplerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8d029-104">This includes cases in which the transfer mode is Streamed.</span></span>|
|<span data-ttu-id="8d029-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8d029-105">Suggestion</span></span>|<span data-ttu-id="8d029-106">Bu değişiklik, burada ileti uzunluğu ASP.NET veya WCF tarafından izin verilen sınırları aştığı durumlarda hata ayıklamayı kolaylaştırır. Bir HTTP 400 durum koduna göre işleyen herhangi bir kodu değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d029-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>|
|<span data-ttu-id="8d029-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8d029-107">Scope</span></span>|<span data-ttu-id="8d029-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="8d029-108">Edge</span></span>|
|<span data-ttu-id="8d029-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8d029-109">Version</span></span>|<span data-ttu-id="8d029-110">4,5</span><span class="sxs-lookup"><span data-stu-id="8d029-110">4.5</span></span>|
|<span data-ttu-id="8d029-111">Tür</span><span class="sxs-lookup"><span data-stu-id="8d029-111">Type</span></span>|<span data-ttu-id="8d029-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8d029-112">Runtime</span></span>|
