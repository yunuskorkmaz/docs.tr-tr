---
title: Açık arabirim uygulama-C# Programlama Kılavuzu
description: Bir sınıf, C# ' de aynı imzaya sahip bir üye içeren arabirimler uygulayabilir. Açık uygulama, bir arabirime özgü bir sınıf üyesi oluşturur.
ms.date: 03/24/2021
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.openlocfilehash: 2ca7e8a10c009b01b43e0c09d25d2dd99cbee2ec
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610869"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur. Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için çağırır. Bu ilk örnek, türleri tanımlar:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Aşağıdaki örnek yöntemleri çağırır:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Ancak aynı uygulamanın her iki arabirim için de çağrılması istemeyebilirsiniz. Hangi arabirimin kullanımda olduğuna bağlı olarak farklı bir uygulama çağırmak için, açıkça bir arabirim üyesi uygulayabilirsiniz. Açık arabirim uygulama, yalnızca belirtilen arabirim aracılığıyla çağrılan bir sınıf üyesidir. Sınıf üyesini, arabirimin adı ve bir nokta ile önek olarak adlandırın. Örnek:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Sınıf üyesi `IControl.Paint` yalnızca arabirim aracılığıyla kullanılabilir `IControl` ve `ISurface.Paint` yalnızca ile kullanılabilir `ISurface` . Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz. Örnek:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır. Her iki arabirimi de uygulamak için bir sınıf, bir `P` derleyici hatasından kaçınmak için özellik veya yöntem ya da her ikisi için açık uygulamayı kullanmalıdır `P` . Örnek:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Açık arabirim uygulamasında tanımlı olduğu türün bir üyesi olarak erişilebilir olmadığından, bir erişim değiştiricisi yoktur. Bunun yerine, yalnızca arabirimin bir örneği aracılığıyla çağrıldığında erişilebilir. Açık arabirim uygulamaları için bir erişim değiştiricisi belirtirseniz, derleyici hatası [CS0106](../../language-reference/compiler-messages/cs0106.md)alırsınız. Daha fazla bilgi için bkz. [ `interface` (C# Başvurusu)](../../language-reference/keywords/interface.md).

[C# 8,0](../../whats-new/csharp-8.md#default-interface-methods)' den başlayarak, bir arabirimde bildirildiği Üyeler için bir uygulama tanımlayabilirsiniz. Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir. Devralınan üye, ortak arabirimin parçası olarak görünmez. Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Aşağıdaki örnek varsayılan uygulamayı çağırır:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Arabirimi uygulayan herhangi bir sınıf, `IControl` `Paint` genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan yöntemi geçersiz kılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Devralma](../classes-and-structs/inheritance.md)
