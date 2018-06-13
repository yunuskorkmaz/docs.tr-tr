---
title: Ana() ve komut satırı bağımsız değişkenleri (C# programlama Kılavuzu)
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 03d6e7185a0a16589fb612724be52ce51e813173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332374"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Ana() ve komut satırı bağımsız değişkenleri (C# programlama Kılavuzu)

`Main` Yöntemi bir C# uygulamasının giriş noktasıdır. (Kitaplıkları ve Hizmetleri gerektirmez bir `Main` yöntemi bir giriş noktası olarak.) Uygulama başlatıldığında `Main` çağrılan ilk yöntemi bir yöntemdir.

 Yalnızca bir giriş noktası bir C# programında olabilir. Sahip birden fazla sınıf varsa bir `Main` yöntemi, programınızla birlikte derleme gerekir **/ana** belirtmek için derleyici seçeneği `Main` giriş noktası olarak kullanılacak yöntemi. Daha fazla bilgi için bkz: [/Main (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Genel Bakış

- `Main` Yöntemi bir yürütülebilir program giriş noktasıdır; burada program denetimini başlar ve biter değildir.
- `Main` bir sınıf veya yapı içinde bildirildi. `Main` olmalıdır [statik](../../../csharp/language-reference/keywords/static.md) ve olmaması [ortak](../../../csharp/language-reference/keywords/public.md). (Önceki örnekte, varsayılan erişimini aldığı [özel](../../../csharp/language-reference/keywords/private.md).) Kapsayan sınıfta veya yapı statik olması gerekli değildir.
- `Main` ya da sahip bir `void`, `int`, veya C# ile 7.1, başlangıç `Task`, veya `Task<int>` dönüş türü.
- Yalnızca ve yalnızca, `Main` döndüren bir `Task` veya `Task<int>`, bildirimi `Main` içerebilir [ `async` ](../../language-reference/keywords/async.md) değiştiricisi. Bu özellikle dışlar Not bir `async void Main` yöntemi.
- `Main` Yöntemi ile veya olmadan bildirilebilir bir `string[]` komut satırı bağımsız değişkenleri içeriyor parametresi. Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresi el ile ekleyin Aksi takdirde kullanmak <xref:System.Environment> komut satırı bağımsız değişkenlerini elde etmek için sınıf. Parametre sıfır dizinli komut satırı bağımsız değişkenleri okunur. C ve C++ aksine, programın adı ilk komut satırı bağımsız değişkeni işlenmez.

Eklenmesi `async` ve `Task`, `Task<int>` türleri basitleştirir program kodunu konsol uygulamaları başlaması gerekiyorsa dönün ve `await` zaman uyumsuz işlemleri `Main`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.
[csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
[C# Programı İçinde](../../../csharp/programming-guide/inside-a-program/index.md)  
