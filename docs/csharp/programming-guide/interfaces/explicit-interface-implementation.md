---
title: Açık Arayüz Uygulaması - C# Programlama Kılavuzu
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167679"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md) aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyenin sınıfta uygulanması her iki arabirimin de bu üyeyi uygulama olarak kullanmasına neden olur. Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemi çağırmak için. Bu ilk örnek türleri tanımlar:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Aşağıdaki örnek yöntemleri çağırır:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

İki arabirim üyesi aynı işlevi yerine getirmediğinde, arabirimlerin birinden veya her ikisinin yanlış uygulanmasına neden olur. Bir arabirim üyesini açıkça uygulamak mümkündür-yalnızca arabirim üzerinden çağrılan ve bu arabirime özgü bir sınıf üyesi oluşturmak. Arabirimin adı ve bir nokta ile sınıf üyesi adı. Örnek:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirim üzerinden `ISurface.Paint` kullanılabilir ve `ISurface`yalnızca . Her iki yöntem uygulamaları ayrıdır ve ikisi de doğrudan sınıfta kullanılamaz. Örnek:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Açık uygulama, her biri bir özellik ve yöntem gibi aynı adı taşıyan farklı üyeleri beyan eden iki arabirimin bulunduğu durumları çözmek için de kullanılır. Her iki arabirimi de uygulamak için, derleyici `P`hatasını önlemek `P`için bir sınıfın özellik veya yöntem veya her ikisi için açık uygulama kullanması zorunludur. Örnek:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

[C# 8.0](../../whats-new/csharp-8.md#default-interface-methods)ile başlayarak, arabirimde bildirilen üyeler için bir uygulama tanımlayabilirsiniz. Bir sınıf bir arabirimden bir yöntem uygulaması devralıyorsa, bu yönteme yalnızca arabirim türünün başvurusu yla erişilebilir. Devralınan üye ortak arabirimin bir parçası olarak görünmez. Aşağıdaki örnek, arabirim yöntemi için varsayılan bir uygulama tanımlar:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Aşağıdaki örnek temerrüt uygulamasını çağırır:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

`IControl` Arabirimi uygulayan herhangi bir sınıf, `Paint` genel bir yöntem olarak veya açık arabirim uygulaması olarak varsayılan yöntemi geçersiz kılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Devralma](../classes-and-structs/inheritance.md)
