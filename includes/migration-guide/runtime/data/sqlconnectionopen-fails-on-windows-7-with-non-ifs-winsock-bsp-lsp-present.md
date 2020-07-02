---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622133"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="55886-101">SqlConnection. Open, ıFS olmayan Winsock BSP veya LSP içeren Windows 7 ' de başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="55886-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="55886-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="55886-102">Details</span></span>

<span data-ttu-id="55886-103"><xref:System.Data.SqlClient.SqlConnection.Open><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)>bilgisayarda IFS olmayan Winsock BSP veya LSP içeren bir Windows 7 makinesi üzerinde çalışıyorsa 4,5 .NET Framework başarısız olur. ICıFS BSP veya LSP 'nin yüklü olup olmadığını anlamak için <code>netsh WinSock Show Catalog</code> komutunu kullanın ve <code>Winsock Catalog Provider Entry</code> döndürülen her öğeyi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="55886-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="55886-104">Hizmet bayrak değeri <code>0x20000</code> bit kümesine sahipse, sağlayıcı IFS tutamaçlarını kullanır ve doğru çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="55886-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="55886-105"><code>0x20000</code>Bit açık (ayarlı değil) ise, CIFS BSP veya LSP olmayan bir.</span><span class="sxs-lookup"><span data-stu-id="55886-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="55886-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="55886-106">Suggestion</span></span>

<span data-ttu-id="55886-107">Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="55886-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="55886-108">Alternatif olarak, yüklü ıFS olmayan Winsock LSPs 'ler kaldırılarak bu kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="55886-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="55886-109">Name</span><span class="sxs-lookup"><span data-stu-id="55886-109">Name</span></span>    | <span data-ttu-id="55886-110">Değer</span><span class="sxs-lookup"><span data-stu-id="55886-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="55886-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="55886-111">Scope</span></span>   |<span data-ttu-id="55886-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="55886-112">Minor</span></span>|
|<span data-ttu-id="55886-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="55886-113">Version</span></span>|<span data-ttu-id="55886-114">4,5</span><span class="sxs-lookup"><span data-stu-id="55886-114">4.5</span></span>|
|<span data-ttu-id="55886-115">Tür</span><span class="sxs-lookup"><span data-stu-id="55886-115">Type</span></span>|<span data-ttu-id="55886-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="55886-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="55886-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="55886-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
