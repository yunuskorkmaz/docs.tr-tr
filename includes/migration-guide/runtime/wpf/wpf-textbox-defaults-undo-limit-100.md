---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620712"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF metin kutusu varsayılan olarak 100 limitini geri alır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, WPF metin kutusu için varsayılan geri alma sınırı 100 ' dir (.NET Framework 4,0 ' de sınırsız olacak şekilde)

#### <a name="suggestion"></a>Öneri

100 'nin bir geri alma sınırı çok düşükse, sınır şu şekilde açık şekilde ayarlanabilir<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
