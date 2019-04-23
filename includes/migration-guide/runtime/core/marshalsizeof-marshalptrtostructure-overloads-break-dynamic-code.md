---
ms.openlocfilehash: 6309cead46dff44ff6360bac9b31666f875be210
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981626"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Dinamik kod Marshal.SizeOf ve Marshal.PtrToStructure aşırı yüklemeler Kes

|   |   |
|---|---|
|Ayrıntılar|Dinamik olarak yöntemlere bağlama .NET Framework 4.5.1 başlayarak <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, veya <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (Windows PowerShell, IronPython, aracılığıyla veya C# dynamic anahtar sözcüğü için Örnek) sonuçlanabilir <code>MethodInvocationExceptions</code> nedeni bu yöntemlerin yeni aşırı yüklemeler olabilecek altyapılarının için belirsiz eklenmemiş.|
|Öneri|Hangi aşırı yüklemenin kullanılması gerektiğini açıkça belirtmek için komut dosyalarını güncelleştirin. Bu can genellikle yöntemleri türü parametreleri olarak açıkça atayarak Bitti <xref:System.Type>. Bkz: [bu bağlantıyı](https://support.microsoft.com/kb/2909958/) daha fazla ayrıntı ve nasıl örnekleri geçici sorun.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
