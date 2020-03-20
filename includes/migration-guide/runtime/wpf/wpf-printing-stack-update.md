---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802521"
---
### <a name="wpf-printing-stack-update"></a>WPF Yazdırma Yığını Güncellemesi

|   |   |
|---|---|
|Ayrıntılar|WPF'nin Yazdırma API'leri <xref:System.Printing.PrintQueue?displayProperty=name> artık window'un Yazdırma Belge Paketi API'sini artık amortismana hazır olan XPS Print API lehine arayın. Değişiklik, hizmet edilebilirlik göz önünde bulundurularak yapıldı; ne kullanıcılar ne de geliştiriciler davranış veya API kullanımında herhangi bir değişiklik görmemelidir. Windows 10 Creators Update'te çalışırken yeni yazdırma yığını varsayılan olarak etkinleştirilir. Eski yazdırma yığını, eski Windows sürümlerinde olduğu gibi çalışmaya devam edecektir.|
|Öneri|Windows 10 Creators Update'teki eski yığını <code>UseXpsOMPrinting</code> kullanmak <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> için, kayıt <code>1</code>defteri anahtarının REG_DWORD değerini .|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|
