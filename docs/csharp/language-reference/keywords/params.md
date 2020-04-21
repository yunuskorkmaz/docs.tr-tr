---
title: parametre dizileri için params anahtar kelime - C# referans
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738838"
---
# <a name="params-c-reference"></a>params (C# Başvurusu)

Anahtar kelimeyi `params` kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz. Parametre türü tek boyutlu bir dizi olmalıdır.

Yöntem bildirimindeki anahtar kelimeden `params` sonra ek parametreye `params` izin verilmez ve yöntem bildiriminde yalnızca bir anahtar kelimeye izin verilir.

Bildirilen `params` parametre türü tek boyutlu bir dizi değilse, derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.

Parametresi olan bir `params` yöntemi çağırdığınızda, şu yoldan geçebilirsiniz:

- Dizi öğelerinin türüne ait bağımsız değişkenlerin virgülle ayrılmış bir listesi.
- Belirtilen türdeki bağımsız değişkenler dizisi.
- Tartışma yok. Bağımsız değişken göndermezseniz, `params` listenin uzunluğu sıfırdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bağımsız değişkenlerin bir `params` parametreye gönderilebildiği çeşitli yolları göstermektedir.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Yöntem Parametreleri](method-parameters.md)
