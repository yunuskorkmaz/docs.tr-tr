---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497036"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF metin kutusu varsayılan olarak 100 limitini geri alır

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,5 ' de, WPF metin kutusu için varsayılan geri alma sınırı 100 ' dir (.NET Framework 4,0 ' de sınırsız olacak şekilde)

#### <a name="suggestion"></a>Öneri

100 'nin bir geri alma sınırı çok düşükse, sınır şu şekilde açık şekilde ayarlanabilir <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
