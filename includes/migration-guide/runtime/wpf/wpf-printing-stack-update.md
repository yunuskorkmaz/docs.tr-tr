---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621406"
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
