---
title: Bitwise İşleçleri (F#)
description: 'F # programlama dilinde kullanılabilen bit düzeyinde işleçler hakkında bilgi edinin.'
ms.date: 07/20/2018
ms.openlocfilehash: abd2778eba422b3ce2a3472efd458446854b3d2f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390709"
---
# <a name="bitwise-operators"></a>Bitwise İşleçleri

Bu konu F # dilinde kullanılabilen bit düzeyinde işleçler açıklar.

## <a name="summary-of-bitwise-operators"></a>Bit düzeyinde işleçler özeti
Aşağıdaki tabloda, F # dilinde kutulanmamış tam sayı türleri için desteklenen bir bit düzeyinde işleçler açıklanmaktadır.

|İşleç|Notlar|
|--------|-----|
|`&&&`|Bit düzeyinde AND işleci. Her iki kaynak işlenenleri karşılık gelen bitler 1 olan ve yalnızca, bit sonuçta 1 değeri var.|
|<code>&#124;&#124;&#124;</code>|Bit düzeyinde OR işleci. Sonuçta bite sahip ' % s'değeri 1 ya da kaynağa karşılık gelen bitleri 1 işlenenin olduğu.|
|`^^^`|Bit düzeyinde özel OR işleci. Kaynak işlenenden bit eşit olmayan değerlere sahip ve yalnızca, bit sonuçta 1 değeri var.|
|`~~~`|Bitwise olumsuzlama işleci. Bu birli işleç ve kaynak işlenende 0 tüm bitleri 1 bit dönüştürülür ve 1 tüm bitleri 0 bit dönüştürülür bir sonuç üretir.|
|`<<<`|Bit düzeyinde sola kaydırma işleci. BITS ile ilk işlenen ikinci işlenenin bit sayısına göre sola kaydırılacak sonucudur. En önemli konumu kaydırılacak bit en az önemli konumuna döndürülemez. En az önemli bitlerin sıfırlarla doldurulur. İkinci bağımsız değişken türü `int32`.|
|`>>>`|Bitwise sağ kaydırma işleci. Birinci işlenenin ikinci işlenenin bit sayısına göre sağa kaydırılacak bit sonucudur. En az önemli konumu kaydırılacak bit en önemli konumuna döndürülemez. İmzasız türler için en önemli bitleri sıfırlarla doldurulur. Negatif değerler içeren imzalı türler için en önemli bitleri ettiklerinizi doldurulur. İkinci bağımsız değişken türü `int32`.|

Bitwise işleçleri ile aşağıdaki türleri kullanılabilir: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, ve `unativeint`.

## <a name="see-also"></a>Ayrıca Bkz.
[Simge ve İşleç Başvurusu](index.md)

[Aritmetik İşleçler](arithmetic-operators.md)

[Boole İşleçleri](boolean-operators.md)

