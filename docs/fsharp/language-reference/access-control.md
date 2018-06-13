---
title: Erişim Denetimi (F#)
description: 'Türleri, yöntemleri ve İşlevler, F # programlama dili gibi programlama öğeleri erişimi denetlemek öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566528"
---
# <a name="access-control"></a>Erişim Denetimi

*Erişim denetimi* hangi istemcilerin türleri, yöntemleri ve işlevleri gibi bazı program öğeleri kullanabilirsiniz bildirmek için başvuruyor.


## <a name="basics-of-access-control"></a>Erişim denetimi ile ilgili temel bilgiler
F #'ta erişimi denetleyen tanımlayıcıları `public`, `internal`, ve `private` modülleri, türleri, yöntemleri, değer tanımları, İşlevler, özellikleri ve açık alanlar için uygulanabilir.


- `public` Varlık tüm arayanlar tarafından erişilebilir gösterir.

- `internal` varlık yalnızca aynı derlemesinden erişilebilir gösterir.

- `private` varlık yalnızca kapsayan türü veya modülünden erişilebilir gösterir.


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
[F# Dili Başvurusu](index.md)

[İmzalar](signatures.md)
