---
description: Parameter dizileri için params anahtar sözcüğü-C# başvurusu
title: Parameter dizileri için params anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134477"
---
# <a name="params-c-reference"></a>params (C# Başvurusu)

`params`Anahtar sözcüğünü kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz. Parametre türü tek boyutlu bir dizi olmalıdır.

`params`Yöntem bildiriminde anahtar kelimeden sonra ek parametrelere izin verilmez ve `params` bir yöntem bildiriminde yalnızca bir anahtar sözcüğe izin verilir.

Parametrenin bildirildiği tür `params` tek boyutlu bir dizi değilse, derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.

Bir parametre içeren bir yöntemi çağırdığınızda `params` , şu şekilde geçiş yapabilirsiniz:

- Dizi öğelerinin türünün bağımsız değişkenlerinin virgülle ayrılmış listesi.
- Belirtilen türde bir bağımsız değişken dizisi.
- Bağımsız değişken yok. Bağımsız değişken gönderirseniz, `params` listenin uzunluğu sıfırdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bağımsız değişkenlerin bir parametreye gönderilebileceği çeşitli yollar gösterilmektedir `params` .

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)
