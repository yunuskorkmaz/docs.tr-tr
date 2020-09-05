---
ms.openlocfilehash: e42bce91afab68e509cb35a8992fa3ca2f096872
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497743"
---
### <a name="wpf-printing-stack-update"></a>WPF yazdırma yığını güncelleştirmesi

#### <a name="details"></a>Ayrıntılar

WPF 'nin yazdırma API 'Leri <xref:System.Printing.PrintQueue?displayProperty=fullName> Şu anda kullanım dışı olan XPS yazdırma API 'sini tercih eden Windows 'un yazdırma belgesi paketi API 'sini çağırır. Değişiklik, akılda bakım yapılmıştı. Kullanıcı veya geliştiricilerin davranış veya API kullanımında hiçbir değişiklik görmemelidir. Yeni yazdırma yığını, Windows 10 Creators Update 'te çalışırken varsayılan olarak etkindir. Eski yazdırma yığını, eski Windows sürümlerinde olduğu gibi çalışmaya devam edecektir.

#### <a name="suggestion"></a>Öneri

Windows 10 Creators Update 'te eski yığını kullanmak için <code>UseXpsOMPrinting</code> <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> kayıt defteri anahtarının REG_DWORD değerini olarak ayarlayın <code>1</code> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
