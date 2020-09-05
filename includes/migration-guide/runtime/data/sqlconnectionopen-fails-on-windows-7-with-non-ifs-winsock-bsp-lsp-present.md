---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496805"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection. Open, ıFS olmayan Winsock BSP veya LSP içeren Windows 7 ' de başarısız oluyor

#### <a name="details"></a>Ayrıntılar

<xref:System.Data.SqlClient.SqlConnection.Open><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)>bilgisayarda IFS olmayan Winsock BSP veya LSP içeren bir Windows 7 makinesi üzerinde çalışıyorsa 4,5 .NET Framework başarısız olur. ICıFS BSP veya LSP 'nin yüklü olup olmadığını anlamak için <code>netsh WinSock Show Catalog</code> komutunu kullanın ve <code>Winsock Catalog Provider Entry</code> döndürülen her öğeyi inceleyin. Hizmet bayrak değeri <code>0x20000</code> bit kümesine sahipse, sağlayıcı IFS tutamaçlarını kullanır ve doğru çalışacaktır. <code>0x20000</code>Bit açık (ayarlı değil) ise, CIFS BSP veya LSP olmayan bir.

#### <a name="suggestion"></a>Öneri

Bu hata 4.5.2 .NET Framework düzeltildi, bu nedenle .NET Framework yükseltilerek kaçınılabilir. Alternatif olarak, yüklü ıFS olmayan Winsock LSPs 'ler kaldırılarak bu kaçınılabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
