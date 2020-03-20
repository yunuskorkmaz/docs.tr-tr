---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803228"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open, IFS Winsock BSP veya LSP olmayan windows 7'de başarısız olur

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Data.SqlClient.SqlConnection.Open><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> ve .NET Framework 4.5'te başarısız olup, bilgisayarda IFS Winsock BSP veya LSP olmayan bir Windows 7 makinesinde çalışıyorsanız. IFS BSP veya LSP olmayan bir öğenin yüklü <code>netsh WinSock Show Catalog</code> olup olmadığını <code>Winsock Catalog Provider Entry</code> belirlemek için komutu kullanın ve döndürülen her öğeyi inceleyin. Hizmet Bayrakları değeri bit <code>0x20000</code> kümesine sahipse, sağlayıcı IFS işlamacını kullanır ve doğru çalışır. <code>0x20000</code> Bit açıksa (ayarlı değilse), IFS BSP veya LSP olmayan bir bittir.|
|Öneri|Bu hata .NET Framework 4.5.2'de sabitlenmiştir, böylece .NET Framework yükseltilerek önlenebilir. Alternatif olarak, yüklü olmayan IFS Winsock LSP'leri kaldırarak önlenebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
