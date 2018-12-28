---
title: Erişim Denetimi
description: Türlerin, yöntemlerin ve İşlevler, gibi programlama öğelerine erişim denetimi öğrenin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 8db178b26f3beb6ce95bff84ccad9ac9e8c40ce7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612818"
---
# <a name="access-control"></a>Erişim Denetimi

*Erişim denetimi* hangi istemcilerin türleri, yöntemleri ve işlevleri gibi belirli program öğelerini kullanabilirsiniz bildirmek için ifade eder.

## <a name="basics-of-access-control"></a>Erişim denetimi ile ilgili temel bilgiler

İçinde F#, erişim denetimi tanımlayıcıları `public`, `internal`, ve `private` modülleri, türleri, yöntemleri, değer tanımları, işlevleri, özellikleri ve açık alanlar için uygulanabilir.

- `public` varlığın tüm çağıranlar tarafından erişilebilir olduğunu gösterir.

- `internal` varlık yalnızca aynı bütünleştirilmiş koddan erişilebilir olduğunu gösterir.

- `private` varlık yalnızca kapsayan tür veya modülünden erişilebilir olduğunu gösterir.

> [!NOTE]
> Erişim belirticisi `protected` kullanılmaz F#, destekleyen dillerde yazılan türleri kullanıyorsanız, kabul edilebilir olmasına rağmen `protected` erişim. Bu nedenle, korunan bir yöntemi geçersiz kılarsanız, yöntemi yalnızca sınıf ve onun alt öğelerine içinde erişilebilir kalır.

Genel olarak, aşağıdakiler haricinde varlığın adını önünde tanımlayıcısı put bir `mutable` veya `inline` belirticisi kullanıldığında, erişim denetimi belirticisinden sonra görünen.

Hiçbir erişim belirticisi kullanıldığında varsayılandır `public`, dışında `let` her zaman bir türdeki bağlamaları `private` türü.

İmzaları F# erişimi denetlemek için başka bir mekanizma sağlar F# program öğeleri. İmzalar için erişim denetimi gerekli değildir. Daha fazla bilgi için [imzaları](signatures.md).

## <a name="rules-for-access-control"></a>Erişim denetim için kuralları

Erişim denetimi aşağıdaki kurallarına tabidir şöyledir:

- Devralma bildirimleri (diğer bir deyişle, kullanımını `inherit` bir sınıf için temel sınıf belirtmek için), arabirim (bir sınıf bir arabirim uyguladığını belirterek olduğu gibi) bildirimleri ve soyut üyeleri, her zaman aynı erişilebilirliği kapsayan tür olarak sahiptir. Bu nedenle, erişim denetimi belirticisinin bu yapıları üzerinde kullanılamaz.

- Erişilebilirlik için ayrılmış bir birleşim bireysel durumlarda, ayrılmış birleşim erişilebilirliğini tarafından belirlenir. Diğer bir deyişle, belirli bir birleşim durumu birleşim bundan daha az erişilebilir.

- Bir kayıt türünün her bir alanı olamaz için erişilebilirlik kaydın kendisini erişilebilirliğini tarafından belirlenir. Diğer bir deyişle, belirli kayıt etiket kaydı bundan daha az erişilebilir.

## <a name="example"></a>Örnek

Aşağıdaki kod, erişim denetimi tanımlayıcıları kullanımını gösterir. Projenin başında iki dosya vardır `Module1.fs` ve `Module2.fs`. Her dosya örtük olarak bir modüldür. Bu nedenle, iki modül vardır `Module1` ve `Module2`. Özel bir tür ile iç tür tanımlanan `Module1`. Özel tür erişilemez `Module2`, ancak iç türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

Aşağıdaki kod içinde oluşturulan türleri erişilebilirliğini test `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [İmzalar](signatures.md)