---
ms.openlocfilehash: a9011514c7c4393ec44de2c7fae88768cdccf435
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496537"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4,6, kayıt defterine kendisini kaydederken 4.5. x. x sürümünü kullanmaz

#### <a name="details"></a>Ayrıntılar

Bir tane beklendiğinde, 4,6 .NET Framework için kayıt defterindeki (at) kayıt defteri 'nde ayarlanan sürüm anahtarı ' <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> 4,6 ' ile başlar, ' 4,5 ' değil. Bir makineye hangi .NET Framework sürümlerinin yüklendiğini öğrenmek için bu kayıt defteri anahtarlarına bağımlı olan uygulamalar, 4,6 'in yeni bir olası sürüm olduğunu ve bir önceki 4.5. x sürümleriyle uyumlu olduğunu anlamak için güncelleştirilmeleri gerekir.

#### <a name="suggestion"></a>Öneri

4,5 kayıt defteri anahtarlarını arayarak 4,6 de kabul etmek için .NET Framework 4,5 yüklemesi için uygulamaları yoklayan güncelleştirme.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
