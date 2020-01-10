---
title: params anahtar sözcüğü C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713241"
---
# <a name="params-c-reference"></a>params (C# Başvurusu)

`params` anahtar sözcüğünü kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.

Parametre bildiriminde belirtilen türde bağımsız değişkenlerin virgülle ayrılmış bir listesini veya belirtilen türdeki bağımsız değişkenlerin dizisini gönderebilirsiniz. Bağımsız değişken de gönderebilirsiniz. Bağımsız değişken gönderirseniz `params` listesinin uzunluğu sıfırdır.

Yöntem bildiriminde `params` anahtar sözcüğünden sonra ek parametre yapılmasına izin verilmez ve yöntem bildiriminde yalnızca bir `params` anahtar sözcüğüne izin verilir.

`params` parametresinin belirtilen türü, aşağıdaki örnekte gösterildiği gibi tek boyutlu bir dizi olmalıdır. Aksi takdirde, bir derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bağımsız değişkenlerin `params` parametreye gönderilebileceği çeşitli yollar gösterilmektedir.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Yöntem Parametreleri](method-parameters.md)
