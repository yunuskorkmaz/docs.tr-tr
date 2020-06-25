---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325215"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="fe3d7-101">HttpSys: Istemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="fe3d7-101">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="fe3d7-102">Bir bağlantıyı yeniden oluşturma ve istemci sertifikası isteme seçeneği varsayılan olarak devre dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-102">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="fe3d7-103">Tartışma için bkz. sorun [DotNet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="fe3d7-103">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fe3d7-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fe3d7-104">Version introduced</span></span>

<span data-ttu-id="fe3d7-105">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="fe3d7-105">ASP.NET Core 5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fe3d7-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="fe3d7-106">Old behavior</span></span>

<span data-ttu-id="fe3d7-107">İstemci sertifikası istemek için bağlantıya yeniden anlaşma yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-107">The connection can be renegotiated to request a client certificate.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fe3d7-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="fe3d7-108">New behavior</span></span>

<span data-ttu-id="fe3d7-109">İstemci sertifikaları yalnızca ilk bağlantı el sıkışması sırasında istenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-109">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="fe3d7-110">Daha fazla bilgi için bkz. çekme isteği [DotNet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="fe3d7-110">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe3d7-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="fe3d7-111">Reason for change</span></span>

<span data-ttu-id="fe3d7-112">Yeniden anlaşma, bir dizi performans ve kilitlenme sorununa neden oldu.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-112">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="fe3d7-113">HTTP/2 ' de de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-113">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="fe3d7-114">Bu davranışı denetleme seçeneğinin ASP.NET Core 3,1 ' de tanıtılmasından daha fazla bağlam için, bkz. sorun [DotNet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="fe3d7-114">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe3d7-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fe3d7-115">Recommended action</span></span>

<span data-ttu-id="fe3d7-116">İstemci sertifikaları gerektiren uygulamalar, seçeneğini olarak ayarlamak için *netsh.exe* kullanmalıdır `clientcertnegotiation` `enabled` .</span><span class="sxs-lookup"><span data-stu-id="fe3d7-116">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="fe3d7-117">Daha fazla bilgi için bkz. [netsh http komutları](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="fe3d7-117">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="fe3d7-118">İstemci sertifikalarının yalnızca uygulamanızın bazı bölümleri için etkinleştirilmesini istiyorsanız, [Isteğe bağlı istemci sertifikalarındaki](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)kılavuza bakın.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-118">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="fe3d7-119">Eski yeniden anlaşmak davranışına ihtiyacınız varsa `HttpSysOptions.ClientCertificateMethod` eski değere ayarlayın `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="fe3d7-119">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="fe3d7-120">Bu, yukarıda ve bağlantılı kılavuzda özetlenen nedenlerle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="fe3d7-120">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

#### <a name="category"></a><span data-ttu-id="fe3d7-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="fe3d7-121">Category</span></span>

<span data-ttu-id="fe3d7-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fe3d7-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe3d7-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fe3d7-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
