---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235844"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open IFS olmayan Winsock BSP veya mevcut bir LSP ile Windows 7'de başarısız oluyor

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Data.SqlClient.SqlConnection.Open> ve <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> IFS olmayan Winsock BSP veya LSP'nize ile Windows 7 makinesinde çalıştıran bilgisayarda .NET Framework 4. 5 ' başarısız. IFS olmayan BSP veya LSP'nize yüklü olup olmadığını belirlemek için <code>netsh WinSock Show Catalog</code> komutunu ve İnceleme her <code>Winsock Catalog Provider Entry</code> döndürülen öğe. Hizmet Flags değeri varsa <code>0x20000</code> bit kümesi, sağlayıcı IFS tanıtıcıları kullanan ve doğru bir şekilde çalışır. Varsa <code>0x20000</code> bit Temizle (ayarlanmamış), IFS olmayan BSP veya LSP'nize.|
|Öneri|.NET Framework yükselterek önlenebilir için .NET Framework 4.5.2, bu hata düzeltildi. Alternatif olarak, tüm yüklü olmayan - IFS Winsock Lps'ler kaldırarak önlenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
