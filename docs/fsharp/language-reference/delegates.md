---
title: Temsilciler (F#)
description: 'Temsilciler F # ile çalışmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: be58997dffe8fcd949bbc2d47d86ffccc157d43e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261830"
---
# <a name="delegates"></a>Temsilciler

Bir temsilci, bir nesne olarak bir işlev çağrısını temsil eder. F # programında, genellikle işlev değerleri ilk sınıf değerleri olarak işlevler temsil etmek için kullanmanız gerekir; Ancak, temsilciler .NET Framework'teki kullanılır ve bunları beklediğiniz API'leri ile birlikte çalışmak, bu nedenle gereklidir. Geliştirme kitaplıkları için tasarlanan diğer .NET Framework dillerde kullandığınızda da kullanılabilir.

## <a name="syntax"></a>Sözdizimi

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, `type1` bağımsız değişken türü veya türleri temsil eder ve `type2` dönüş türünü temsil eder. Tarafından temsil edilen bağımsız değişken türleri `type1` otomatik olarak curried. Bu, bu tür hedef işlevinin bağımsız değişkenleri curried bir tanımlama grubu form kullanmanızı ve parantez içine alınmış demet tanımlama grubu biçiminde olan bağımsız değişkenler için önerir. Otomatik currying hedef yöntemin eşleşen bir tanımlama grubu bağımsız değişkenini bırakarak, parantez kümesi kaldırır. Her durumda kullanmalısınız söz dizimi kod örneğine bakın.

Temsilciler, F # işlev değerleri olarak ve statik eklenebilecek veya örnek yöntemler. F # işlev değerleri oluşturucuları temsilci olarak doğrudan bağımsız değişken olarak geçirilebilir. Statik bir yöntem için temsilci sınıf ve yöntem adını kullanarak oluşturun. Bir örnek yöntemi için nesne örneği ve bir bağımsız değişkende yöntemi sağlar. Her iki durumda da, üye erişim işleci (`.`) kullanılır.

`Invoke` Temsilci türünde yöntemi kapsüllenmiş işlevi çağırır. Ayrıca, parantezler olmadan Invoke yöntemi ada başvurarak Temsilciler, işlev değerleri ' e geçirilebilir.

Aşağıdaki kod, bir sınıfta çeşitli yöntemleri temsil eden temsilciler oluşturmak için sözdizimi gösterir. Yöntem statik bir yöntem veya bir örnek yöntemi olup ve demet veya curried formundaki değişkenlerinde olup bağlı olarak bildirmek ve temsilci atamak için söz dizimi biraz farklıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Aşağıdaki kod temsilcileri ile çalışabilir farklı yollardan bazılarını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Önceki kod örnek çıktısı aşağıdaki gibidir.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)
- [Olaylar](members/events.md)
