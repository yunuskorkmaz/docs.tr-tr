---
title: Açık arabirim uygulama-C# Programlama Kılavuzu
description: Bir sınıf, C# ' de aynı imzaya sahip bir üye içeren arabirimler uygulayabilir. Açık uygulama, bir arabirime özgü bir sınıf üyesi oluşturur.
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: a6ec328c08d1da84a11431d9400a094df8c72223
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303094"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur. Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için çağırır. Bu ilk örnek, türleri tanımlar:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Aşağıdaki örnek yöntemleri çağırır:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

İki arabirim üyesi aynı işlevi gerçekleştirmezseniz, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına yol açar. Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür. Sınıf üyesini arabirimin adı ve nokta ile adlandırın. Örneğin:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Sınıf üyesi `IControl.Paint` yalnızca arabirim aracılığıyla kullanılabilir `IControl` ve `ISurface.Paint` yalnızca ile kullanılabilir `ISurface` . Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz. Örneğin:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır. Her iki arabirimi de uygulamak için bir sınıf, bir `P` derleyici hatasından kaçınmak için özellik veya yöntem ya da her ikisi için açık uygulamayı kullanmalıdır `P` . Örneğin:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

[C# 8,0](../../whats-new/csharp-8.md#default-interface-methods)' den başlayarak, bir arabirimde bildirildiği Üyeler için bir uygulama tanımlayabilirsiniz. Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir. Devralınan üye, ortak arabirimin parçası olarak görünmez. Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Aşağıdaki örnek varsayılan uygulamayı çağırır:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Arabirimi uygulayan herhangi bir sınıf, `IControl` `Paint` genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan yöntemi geçersiz kılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Devralma](../classes-and-structs/inheritance.md)
