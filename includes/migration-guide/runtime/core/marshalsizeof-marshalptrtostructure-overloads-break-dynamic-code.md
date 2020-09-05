---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497230"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal. SizeOf ve Marshal. PtrToStructure aşırı yüklemeleri dinamik kodu Böl

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.5.1 ' den başlayarak,,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> , (örneğin, Windows PowerShell, IronPython veya C# dinamik anahtar sözcüğü aracılığıyla) dinamik olarak bağlama, <code>MethodInvocationExceptions</code> Bu yöntemlerin yeni aşırı yüklemeleri eklendiğinden, komut dosyası altyapılarına belirsiz olabilir.

#### <a name="suggestion"></a>Öneri

Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için betikleri güncelleştirin. Bu, genellikle yöntemlerin tür parametreleri olarak açıkça atama yoluyla yapılabilir <xref:System.Type> . Daha fazla ayrıntı ve soruna geçici çözüm örnekleri için [Bu bağlantıya](https://support.microsoft.com/kb/2909958/) bakın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
