---
title: "Erişim Denetimi (F#)"
description: "Türleri, yöntemleri ve İşlevler, F # programlama dili gibi programlama öğeleri erişimi denetlemek öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a>Erişim Denetimi

*Erişim denetimi* hangi istemcilerin türleri, yöntemleri ve işlevleri gibi bazı program öğeleri kullanabilirsiniz bildirmek için başvuruyor.


## <a name="basics-of-access-control"></a>Erişim denetimi ile ilgili temel bilgiler
F #'ta erişimi denetleyen tanımlayıcıları `public`, `internal`, ve `private` modülleri, türleri, yöntemleri, değer tanımları, İşlevler, özellikleri ve açık alanlar için uygulanabilir.


- `public`Varlık tüm arayanlar tarafından erişilebilir gösterir.

- `internal`varlık yalnızca aynı derlemesinden erişilebilir gösterir.

- `private`varlık yalnızca kapsayan türü veya modülünden erişilebilir gösterir.


>[!NOTE] 
Erişim belirteci `protected` destek dillerde yazılmış türleri kullanıyorsanız, kabul edilebilir olmasına rağmen F #'ta kullanılmaz `protected` erişim. Bu nedenle, bir korumalı yöntemi geçersiz kılarsanız yönteminizi yalnızca sınıfı ve alt öğelerinden içinde erişilebilir kalır.

Genel olarak, ne zaman dışında varlık adı önünde belirleyici put bir `mutable` veya `inline` belirticisi kullanılır, erişim denetimi belirticisi sonra görünen.

Hiçbir erişim belirticisi kullanılırsa, varsayılan değer `public`, dışında `let` bir türdeki her zaman bağlamaları `private` türü.

İmzaları F #, F # programı öğelere erişimi denetlemek için başka bir mekanizma sağlar. İmzalar için erişim denetimi gerekli değildir. Daha fazla bilgi için bkz: [imzalar](signatures.md).


## <a name="rules-for-access-control"></a>Erişim denetimi için kuralları
Erişim denetimi aşağıdaki kuralları tabi şöyledir:


- Devralma bildirimleri (diğer bir deyişle, kullanımını `inherit` bir sınıf için temel sınıf belirtmek için), arabirim (bir sınıf bir arabirimini uygulayan belirterek olan) bildirimleri ve soyut üyeleri her zaman kendilerini kapsayan türle aynı erişilebilirlik sahiptir. Bu nedenle, bir erişim denetimi belirticisi bu yapıları üzerinde kullanılamaz.

- Ayrılmış birleşim tek tek durumlarda birleşim türü ayrı kendi erişim denetimi değiştiricileri sahip olamaz.

- Bir kayıt türü tek tek alanların kayıt türünden ayrı kendi erişim denetimi değiştiricileri sahip olamaz.


## <a name="example"></a>Örnek
Aşağıdaki kod, erişim denetimi belirticileri kullanımını gösterir. Projede iki dosya vardır `Module1.fs` ve `Module2.fs`. Her dosya örtük olarak bir modüldür. Bu nedenle, iki modülleri vardır `Module1` ve `Module2`. Özel bir türü ve iç tür tanımlanan `Module1`. Özel tür erişim sağlanamaz `Module2`, ancak iç türü.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
Aşağıdaki kod içinde oluşturulan türleri erişilebilirliğini testleri `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)

[İmzaları](signatures.md)
