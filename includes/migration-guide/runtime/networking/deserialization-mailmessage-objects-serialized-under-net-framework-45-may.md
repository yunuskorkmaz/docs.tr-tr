---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620639"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="da37f-101">.NET Framework 4,5 altında seri hale getirilen MailMessage nesnelerinin serisini kaldırma işlemi başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="da37f-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="da37f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="da37f-102">Details</span></span>

<span data-ttu-id="da37f-103">4,5 .NET Framework başlayarak, <xref:System.Web.Mail.MailMessage> nesneler ASCII olmayan karakterler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="da37f-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="da37f-104">.NET Framework 4 ' te yalnızca ASCII karakterleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="da37f-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="da37f-105"><xref:System.Web.Mail.MailMessage>ASCII olmayan karakterler içeren ve .NET Framework 4,5 veya üzeri bir sürümde seri hale getirilen nesneler .NET Framework 4 altında seri durumdan çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="da37f-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="da37f-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="da37f-106">Suggestion</span></span>

<span data-ttu-id="da37f-107">Bir nesne seri durumdan çıkarılırken kodunuzun özel durum işleme sağladığından emin olun <xref:System.Web.Mail.MailMessage> .</span><span class="sxs-lookup"><span data-stu-id="da37f-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="da37f-108">Name</span><span class="sxs-lookup"><span data-stu-id="da37f-108">Name</span></span>    | <span data-ttu-id="da37f-109">Değer</span><span class="sxs-lookup"><span data-stu-id="da37f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="da37f-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="da37f-110">Scope</span></span>   |<span data-ttu-id="da37f-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="da37f-111">Minor</span></span>|
|<span data-ttu-id="da37f-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="da37f-112">Version</span></span>|<span data-ttu-id="da37f-113">4,5</span><span class="sxs-lookup"><span data-stu-id="da37f-113">4.5</span></span>|
|<span data-ttu-id="da37f-114">Tür</span><span class="sxs-lookup"><span data-stu-id="da37f-114">Type</span></span>|<span data-ttu-id="da37f-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="da37f-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da37f-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="da37f-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
