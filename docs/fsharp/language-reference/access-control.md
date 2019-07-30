---
title: Erişim Denetimi
description: F# Programlama dilindeki türler, Yöntemler ve işlevler gibi programlama öğelerine erişimi nasıl denetleyeceğinizi öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ed77a09cf87aabf9a4134276e89e84aa42abd3c3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629964"
---
# <a name="access-control"></a>Erişim Denetimi

*Erişim denetimi* , hangi istemcilerin türler, Yöntemler ve işlevler gibi belirli program öğelerini kullanbileceği bildirimini belirtir.

## <a name="basics-of-access-control"></a>Access Control temelleri

' F#De, erişim denetimi belirticileri `public` `internal`, ve `private` , modüller, türler, Yöntemler, değer tanımları, işlevler, Özellikler ve açık alanlara uygulanabilir.

- `public`varlığa tüm çağıranlar tarafından erişilebileceğini belirtir.

- `internal`varlığa yalnızca aynı derlemeden erişilebileceğini belirtir.

- `private`varlığa yalnızca kapsayan türden veya modülden erişilebileceğini belirtir.

> [!NOTE]
> Erişim belirleyicisi `protected` , erişimi destekleyen `protected` dillerde yazılmış F#türler kullanıyorsanız kabul edilebilir olmasına rağmen ' de kullanılmaz. Bu nedenle, korumalı bir yöntemi geçersiz kılarsınız, yönteminiz yalnızca sınıf ve alt öğelerinden biri içinde erişilebilir kalır.

Genel olarak, tanımlayıcı, erişim denetimi belirticisinden sonra görünen bir `mutable` veya `inline` tanımlayıcı kullanıldığı durumlar dışında, varlığın adının önüne konur.

Hiçbir erişim belirticisi kullanılmazsa, varsayılan olarak, bir tür `public`içindeki `let` bağlamalar dışında, her zaman `private` tür olarak olur.

İçindeki F# imzalar F# program öğelerine erişimi denetlemek için başka bir mekanizma sağlar. İmza, erişim denetimi için gerekli değildir. Daha fazla bilgi için bkz. [imzalar](signatures.md).

## <a name="rules-for-access-control"></a>Access Control kuralları

Erişim denetimi aşağıdaki kurallara tabidir:

- Devralma bildirimleri (yani, bir sınıf için bir `inherit` taban sınıf belirtmek için kullanımı), arabirim bildirimleri (yani, bir sınıfın bir arabirim uyguladığı) ve soyut üyelerin her zaman kapsayan türle aynı erişilebilirliği vardır. Bu nedenle, bir erişim denetim belirticisi bu yapılar üzerinde kullanılamaz.

- Ayrılmış bir Union içindeki bireysel durumlar için erişilebilirlik, ayrılmış birleşimin erişilebilirliğine göre belirlenir. Diğer bir deyişle, belirli bir birleşim durumunun birleşimin kendisinden daha az erişilebilir olmaması gerekir.

- Kayıt türündeki ayrı alanlar için erişilebilirlik, kaydın kendisi tarafından belirlenir. Diğer bir deyişle, belirli bir kayıt etiketi kaydın kendisinden daha az erişilebilir değildir.

## <a name="example"></a>Örnek

Aşağıdaki kod, erişim denetimi belirticilerinin kullanımını gösterir. `Module1.fs` Projesinde`Module2.fs`iki dosya vardır. Her dosya örtük olarak bir modüldür. Bu nedenle, `Module1` ve `Module2`olmak üzere iki modül vardır. Özel bir tür ve bir iç tür içinde `Module1`tanımlanmıştır. Özel türe erişilemez `Module2`, ancak iç tür olabilir.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Aşağıdaki kod, içinde `Module1.fs`oluşturulan türlerin erişilebilirliğini sınar.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [İmzalar](signatures.md)
