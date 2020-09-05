---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497122"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="599ed-101">.NET Framework 4,5 altında seri hale getirilen MailMessage nesnelerinin serisini kaldırma işlemi başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="599ed-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="599ed-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="599ed-102">Details</span></span>

<span data-ttu-id="599ed-103">4,5 .NET Framework başlayarak, <xref:System.Web.Mail.MailMessage> nesneler ASCII olmayan karakterler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="599ed-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="599ed-104">.NET Framework 4 ' te yalnızca ASCII karakterleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="599ed-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="599ed-105"><xref:System.Web.Mail.MailMessage> ASCII olmayan karakterler içeren ve .NET Framework 4,5 veya üzeri bir sürümde seri hale getirilen nesneler .NET Framework 4 altında seri durumdan çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="599ed-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="599ed-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="599ed-106">Suggestion</span></span>

<span data-ttu-id="599ed-107">Bir nesne seri durumdan çıkarılırken kodunuzun özel durum işleme sağladığından emin olun <xref:System.Web.Mail.MailMessage> .</span><span class="sxs-lookup"><span data-stu-id="599ed-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="599ed-108">Name</span><span class="sxs-lookup"><span data-stu-id="599ed-108">Name</span></span>    | <span data-ttu-id="599ed-109">Değer</span><span class="sxs-lookup"><span data-stu-id="599ed-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="599ed-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="599ed-110">Scope</span></span>   |<span data-ttu-id="599ed-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="599ed-111">Minor</span></span>|
|<span data-ttu-id="599ed-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="599ed-112">Version</span></span>|<span data-ttu-id="599ed-113">4,5</span><span class="sxs-lookup"><span data-stu-id="599ed-113">4.5</span></span>|
|<span data-ttu-id="599ed-114">Tür</span><span class="sxs-lookup"><span data-stu-id="599ed-114">Type</span></span>|<span data-ttu-id="599ed-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="599ed-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="599ed-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="599ed-116">Affected APIs</span></span>

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
