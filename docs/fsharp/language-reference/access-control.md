---
title: Erişim Denetimi
description: F# Programlama dilindeki türler, Yöntemler ve işlevler gibi programlama öğelerine erişimi nasıl denetleyeceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425107"
---
# <a name="access-control"></a>Erişim Denetimi

*Erişim denetimi* , hangi istemcilerin türler, Yöntemler ve işlevler gibi belirli program öğelerini kullanbileceği bildirimini belirtir.

## <a name="basics-of-access-control"></a>Access Control temelleri

' F#De, erişim denetimi belirticileri `public`, `internal`ve `private`, modüller, türler, Yöntemler, değer tanımları, işlevler, Özellikler ve açık alanlara uygulanabilir.

- `public`, varlığa tüm çağıranlar tarafından erişilebileceğini belirtir.

- `internal`, varlığa yalnızca aynı derlemeden erişilebileceğini belirtir.

- `private`, varlığa yalnızca kapsayan tür veya modülden erişilebileceğini belirtir.

> [!NOTE]
> `protected` erişim belirleyicisi ' de F#kullanılamaz, ancak `protected` erişimi destekleyen dillerde yazılmış türler kullanıyorsanız bu kabul edilebilir. Bu nedenle, korumalı bir yöntemi geçersiz kılarsınız, yönteminiz yalnızca sınıf ve alt öğelerinden biri içinde erişilebilir kalır.

Genel olarak, tanımlayıcı, erişim denetimi belirticisinden sonra görünen bir `mutable` veya `inline` belirticisi dışında, varlığın adının önüne konur.

Herhangi bir erişim belirticisi kullanılmazsa, bir tür `let` bağlamaları dışında, her zaman türüne `private` olan `public`varsayılan değer.

İçindeki F# imzalar F# program öğelerine erişimi denetlemek için başka bir mekanizma sağlar. İmza, erişim denetimi için gerekli değildir. Daha fazla bilgi için bkz. [imzalar](signature-files.md).

## <a name="rules-for-access-control"></a>Access Control kuralları

Erişim denetimi aşağıdaki kurallara tabidir:

- Devralma bildirimleri (yani, bir sınıf için bir taban sınıf belirtmek için `inherit` kullanımı), arabirim bildirimleri (yani bir sınıfın bir arabirim uyguladığı) ve soyut üyelerin her zaman kapsayan türle aynı erişilebilirliği vardır. Bu nedenle, bir erişim denetim belirticisi bu yapılar üzerinde kullanılamaz.

- Ayrılmış bir Union içindeki bireysel durumlar için erişilebilirlik, ayrılmış birleşimin erişilebilirliğine göre belirlenir. Diğer bir deyişle, belirli bir birleşim durumunun birleşimin kendisinden daha az erişilebilir olmaması gerekir.

- Kayıt türündeki ayrı alanlar için erişilebilirlik, kaydın kendisinin erişilebilirliği tarafından belirlenir. Diğer bir deyişle, belirli bir kayıt etiketi kaydın kendisinden daha az erişilebilir değildir.

## <a name="example"></a>Örnek

Aşağıdaki kod, erişim denetimi belirticilerinin kullanımını gösterir. Projede iki dosya vardır `Module1.fs` ve `Module2.fs`. Her dosya örtük olarak bir modüldür. Bu nedenle, `Module1` ve `Module2`iki modül vardır. Özel bir tür ve bir iç tür `Module1`tanımlanmıştır. Özel türe `Module2`erişilemez, ancak iç tür olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Aşağıdaki kod `Module1.fs`içinde oluşturulan türlerin erişilebilirliğini sınar.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [İmzalar](signature-files.md)
