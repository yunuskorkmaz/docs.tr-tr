---
title: Temsilciler (F#)
description: 'F # temsilciler çalışmak öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 664b4f80302871d05ea9604ca90219e19bc14ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="delegates"></a>Temsilciler

Temsilci bir nesne olarak bir işlev çağrısını temsil eder. F #'ta, normalde işlevi ilk sınıf değerleri olarak işlevler göstermek için değerleri kullanmanız; Ancak, temsilciler .NET Framework kullanılır ve bunları beklediğiniz API'leri ile birlikte çalışmak, böylece ihtiyaç vardır. Geliştirme kitaplıkları için tasarlanan diğer .NET Framework dillerinden kullandığınızda da kullanılabilir.


## <a name="syntax"></a>Sözdizimi

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde `type1` bağımsız değişken türü veya türleri temsil eder ve `type2` dönüş türünü temsil eder. Tarafından temsil edilen bağımsız değişken türleri `type1` otomatik olarak curried. Bu, bu tür bağımsız değişkenleri hedef işlevinin curried varsa bir tanımlama grubu formu kullanın ve kayıt formunda önceden olan bağımsız değişkenler için parantez içine alınmış bir tanımlama grubu için önerir. Otomatik currying hedef yöntemin eşleşen bir tanımlama grubu bağımsız değişkeni bırakarak parantez kümesini kaldırır. Her durumda kullanmalısınız söz dizimi kod örneğine bakın.

Temsilciler F # işlev değerlerini ve statik eklenebilecek veya yöntemleri örneği. F # işlev değerlerini oluşturucuları temsilci seçmek için doğrudan bağımsız değişken olarak geçirilebilir. Statik bir yöntem için sınıf ve yöntem adını kullanarak temsilci oluşturun. Bir örnek yöntemi için nesne örneği ve tek bir bağımsız değişken yöntemi sağlar. Her iki durumda da, üye erişimi işleci (`.`) kullanılır.

`Invoke` Temsilci türünün yöntemi kapsüllenmiş işlevi çağırır. Ayrıca, temsilciler işlevi değerleri olarak parantezler olmadan Invoke yöntemi adına başvuran tarafından gönderilir.

Aşağıdaki kod bir sınıf çeşitli yöntemlerle temsil temsilciler oluşturmak için söz dizimi görülmektedir. Bildirme ve temsilci atamak için sözdizimi yöntemi bir statik veya örnek yöntemini olup ve bağımsız değişkenleri tanımlama grubu form veya curried biçiminde olup bağlı olarak biraz farklıdır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

Aşağıdaki kod, temsilci ile çalışabilirsiniz farklı yollardan bazılarını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

Önceki kod örneğinde çıktı aşağıdaki gibidir.

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Parametreler ve Bağımsız Değişkenler](parameters-and-arguments.md)

[Olaylar](members/events.md)
