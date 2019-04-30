---
title: params anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: dd9699eb50f7dffc7c2f4976a79afbf689ba2470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660989"
---
# <a name="params-c-reference"></a>params (C# Başvurusu)

Kullanarak `params` belirtebileceğiniz anahtar sözcüğü, bir [yöntem parametresi](method-parameters.md) , değişken sayıda bağımsız değişken alır.

Parametre bildiriminde belirtilen türde bağımsız değişkenleri dizisini belirtilen türdeki bağımsız değişkenlerin virgülle ayrılmış bir liste gönderebilirsiniz. Ayrıca, herhangi bir bağımsız değişken gönderebilirsiniz. Hiçbir bağımsız değişken uzunluğu gönderirseniz `params` sıfır listesidir.

Ek parametre sonra izin verilen `params` anahtar sözcüğü bir yöntem bildiriminde ve tek `params` anahtar sözcüğü bir metodun bildiriminde izin verilir.

Bildirilen türü `params` parametresi, aşağıdaki örnekte gösterildiği gibi bir tek boyutlu bir dizi olmalıdır. Aksi halde bir derleyici hatası [CS0225](../../misc/cs0225.md) gerçekleşir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bağımsız değişkenleri göndermenin çeşitli yollarını gösterir bir `params` parametresi.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)