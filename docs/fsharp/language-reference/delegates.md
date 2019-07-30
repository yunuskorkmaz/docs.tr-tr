---
title: Temsilciler
description: "' De F#temsilcilerle çalışmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630361"
---
# <a name="delegates"></a>Temsilciler

Bir temsilci, bir işlev çağrısını bir nesne olarak temsil eder. ' F#De, işlevleri ilk sınıf değerler olarak göstermek için normalde işlev değerlerini kullanmanız gerekir; Ancak, temsilciler .NET Framework kullanılır ve bu nedenle, bunları bekleyen API 'lerle birlikte çalışırken gereklidir. Bunlar ayrıca, diğer .NET Framework dillerden kullanılmak üzere tasarlanan kitaplıkları yazmak için de kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, `type1` bağımsız değişken türünü veya türlerini temsil eder ve `type2` dönüş türünü temsil eder. Tarafından `type1` temsil edilen bağımsız değişken türleri otomatik olarak curried ' dir. Bu, bu tür için hedef işlevin bağımsız değişkenleri curried ise ve başlık formunda zaten olan bağımsız değişkenler için parantez içine alınmış bir tanımlama grubu olan bir demet formu kullanmanızı önerir. Otomatik currying, target yöntemiyle eşleşen bir demet bağımsız değişkeni bırakarak bir parantez kümesini kaldırır. Her durumda kullanmanız gereken sözdiziminin kod örneğine bakın.

Temsilciler F# işlev değerlerine, statik veya örnek yöntemlerine eklenebilir. F#işlev değerleri, doğrudan temsilci oluşturucularına bağımsız değişken olarak geçirilebilir. Statik bir yöntemde, sınıfının adını ve yöntemini kullanarak temsilciyi oluşturursunuz. Bir örnek yönteminde, nesne örneğini ve yöntemini bir bağımsız değişkende sağlarsınız. Her iki durumda da, üye erişim işleci (`.`) kullanılır.

Temsilci `Invoke` türündeki yöntemi kapsüllenmiş işlevi çağırır. Ayrıca, temsilciler, parantez olmadan Invoke yöntemi adına başvurarak işlev değerleri olarak geçirilebilir.

Aşağıdaki kod, bir sınıftaki çeşitli yöntemleri temsil eden temsilciler oluşturmak için söz dizimini gösterir. Yöntemin statik bir yöntem veya örnek yöntemi olmasına ve tanımlama grubu formunda veya curried formunda bağımsız değişkenler içerip içermediğini bağlı olarak, temsilciyi bildirme ve atamaya yönelik sözdizimi biraz farklıdır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Aşağıdaki kod temsilcilerle çalışabilmeniz için kullanabileceğiniz farklı yolları gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Önceki kod örneği çıkışı aşağıdaki gibidir.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)
- [Olaylar](./members/events.md)
