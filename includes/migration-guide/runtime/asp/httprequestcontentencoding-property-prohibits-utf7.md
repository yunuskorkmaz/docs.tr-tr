---
ms.openlocfilehash: cf34c5df1badcfd86d8a07bafdf1b759234712e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496200"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="1a6a5-101">HttpRequest. Contentenkodlama özelliği yasaklar UTF7</span><span class="sxs-lookup"><span data-stu-id="1a6a5-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="1a6a5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1a6a5-102">Details</span></span>

<span data-ttu-id="1a6a5-103">.NET Framework 4,5 ' den başlayarak UTF-7 kodlaması <xref:System.Web.HttpRequest?displayProperty=fullName> s ' gövdelerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a6a5-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="1a6a5-104">Gelen UTF-7 verilerine bağlı olan uygulamalar için verilerin kodları bazı durumlarda düzgün çözülmez.</span><span class="sxs-lookup"><span data-stu-id="1a6a5-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1a6a5-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="1a6a5-105">Suggestion</span></span>

<span data-ttu-id="1a6a5-106">İdeal olarak, uygulamaların s 'de UTF-7 kodlaması kullanmamalıdır <xref:System.Web.HttpRequest?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="1a6a5-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="1a6a5-107">Alternatif olarak, eski davranış <code>aspnet:AllowUtf7RequestContentEncoding</code> [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) öğesinin özniteliği kullanılarak geri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1a6a5-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="1a6a5-108">Name</span><span class="sxs-lookup"><span data-stu-id="1a6a5-108">Name</span></span>    | <span data-ttu-id="1a6a5-109">Değer</span><span class="sxs-lookup"><span data-stu-id="1a6a5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1a6a5-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1a6a5-110">Scope</span></span>   |<span data-ttu-id="1a6a5-111">Edge</span><span class="sxs-lookup"><span data-stu-id="1a6a5-111">Edge</span></span>|
|<span data-ttu-id="1a6a5-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1a6a5-112">Version</span></span>|<span data-ttu-id="1a6a5-113">4,5</span><span class="sxs-lookup"><span data-stu-id="1a6a5-113">4.5</span></span>|
|<span data-ttu-id="1a6a5-114">Tür</span><span class="sxs-lookup"><span data-stu-id="1a6a5-114">Type</span></span>|<span data-ttu-id="1a6a5-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="1a6a5-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1a6a5-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1a6a5-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.ContentEncoding`

-->
