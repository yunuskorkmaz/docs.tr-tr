---
title: Açık arabirim uygulama- C# Programlama Kılavuzu
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628156"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur. Aşağıdaki örnekte, `Paint` için tüm çağrılar aynı yöntemi çağırır. Bu ilk örnek, türleri tanımlar:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Aşağıdaki örnek yöntemleri çağırır:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

İki arabirim üyesi aynı işlevi gerçekleştirmezseniz, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına yol açar. Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür. Sınıf üyesini arabirimin adı ve nokta ile adlandırın. Örnek:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirimi aracılığıyla kullanılabilir ve `ISurface.Paint` yalnızca `ISurface`ile kullanılabilir. Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz. Örnek:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır. Her iki arabirimi de uygulamak için bir sınıfın bir derleyici hatasından kaçınmak için özellik `P`veya yöntem `P`ya da her ikisi için açık uygulamayı kullanması gerekir. Örnek:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Bir sınıf bir arabirimden bir yöntem uygulamasını devralırsa, bu yönteme yalnızca arabirim türünün bir başvurusuyla erişilebilir. Devralınan üye, ortak arabirimin parçası olarak görünmez. Aşağıdaki örnek, bir arabirim yöntemi için varsayılan uygulamayı tanımlar:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Aşağıdaki örnek varsayılan uygulamayı çağırır:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

`IControl` arabirimini uygulayan herhangi bir sınıf, genel bir yöntem olarak ya da açık bir arabirim uygulamasıyla varsayılan `Paint` yöntemini geçersiz kılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Devralma](../classes-and-structs/inheritance.md)
