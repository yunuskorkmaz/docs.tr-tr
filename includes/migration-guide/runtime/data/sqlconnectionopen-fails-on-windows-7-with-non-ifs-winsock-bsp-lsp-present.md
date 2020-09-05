---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496805"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="a72f6-101">SqlConnection. Open, ıFS olmayan Winsock BSP veya LSP içeren Windows 7 ' de başarısız oluyor</span><span class="sxs-lookup"><span data-stu-id="a72f6-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="a72f6-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a72f6-102">Details</span></span>

<span data-ttu-id="a72f6-103"><xref:System.Data.SqlClient.SqlConnection.Open><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)>bilgisayarda IFS olmayan Winsock BSP veya LSP içeren bir Windows 7 makinesi üzerinde çalışıyorsa 4,5 .NET Framework başarısız olur. ICıFS BSP veya LSP 'nin yüklü olup olmadığını anlamak için <code>netsh WinSock Show Catalog</code> komutunu kullanın ve <code>Winsock Catalog Provider Entry</code> döndürülen her öğeyi inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a72f6-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="a72f6-104">Hizmet bayrak değeri <code>0x20000</code> bit kümesine sahipse, sağlayıcı IFS tutamaçlarını kullanır ve doğru çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="a72f6-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="a72f6-105"><code>0x20000</code>Bit açık (ayarlı değil) ise, CIFS BSP veya LSP olmayan bir.</span><span class="sxs-lookup"><span data-stu-id="a72f6-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a72f6-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="a72f6-106">Suggestion</span></span>

<span data-ttu-id="a72f6-107">Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="a72f6-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="a72f6-108">Alternatif olarak, yüklü ıFS olmayan Winsock LSPs 'ler kaldırılarak bu kaçınılabilir.</span><span class="sxs-lookup"><span data-stu-id="a72f6-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="a72f6-109">Name</span><span class="sxs-lookup"><span data-stu-id="a72f6-109">Name</span></span>    | <span data-ttu-id="a72f6-110">Değer</span><span class="sxs-lookup"><span data-stu-id="a72f6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a72f6-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a72f6-111">Scope</span></span>   |<span data-ttu-id="a72f6-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="a72f6-112">Minor</span></span>|
|<span data-ttu-id="a72f6-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a72f6-113">Version</span></span>|<span data-ttu-id="a72f6-114">4,5</span><span class="sxs-lookup"><span data-stu-id="a72f6-114">4.5</span></span>|
|<span data-ttu-id="a72f6-115">Tür</span><span class="sxs-lookup"><span data-stu-id="a72f6-115">Type</span></span>|<span data-ttu-id="a72f6-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a72f6-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a72f6-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a72f6-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
