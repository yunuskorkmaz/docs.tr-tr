---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620586"
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
