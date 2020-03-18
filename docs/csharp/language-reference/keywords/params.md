---
title: params anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173555"
---
# <a name="params-c-reference"></a>params (C# Başvurusu)

Anahtar kelimeyi `params` kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.

Parametre bildiriminde belirtilen türdeki bağımsız değişkenlerin veya belirtilen türdeki bağımsız değişkenlerin bir dizi virgülle ayrılmış bir listesini gönderebilirsiniz. Ayrıca hiçbir bağımsız değişken gönderebilirsiniz. Bağımsız değişken göndermezseniz, `params` listenin uzunluğu sıfırdır.

Yöntem bildirimindeki anahtar kelimeden `params` sonra ek parametreye `params` izin verilmez ve yöntem bildiriminde yalnızca bir anahtar kelimeye izin verilir.

Aşağıdaki örnekte `params` görüldüğü gibi, parametrenin bildirilen türü tek boyutlu bir dizi olmalıdır. Aksi takdirde, bir derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.

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
