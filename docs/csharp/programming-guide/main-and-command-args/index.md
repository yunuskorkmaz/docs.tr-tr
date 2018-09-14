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
ms.openlocfilehash: 144d03edf28464717430bd0ae83db637578d8296
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590916"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Ana() ve komut satırı bağımsız değişkenleri (C# programlama Kılavuzu)

`Main` Bir C# uygulaması giriş noktası bir yöntemdir. (Kitaplıkları ve Hizmetleri gerektirmez bir `Main` yöntemi olarak bir giriş noktası.) Uygulama başlatıldığında `Main` çağrılan ilk yöntem yöntemidir.

 Yalnızca bir C# programında bir giriş noktası olabilir. Birden fazla sınıf varsa bir `Main` yöntemi programınızla birlikte derleme gerekir **/main** belirtmek için derleyici seçeneği `Main` giriş noktası olarak kullanmak için yöntemi. Daha fazla bilgi için [/Main (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Genel Bakış

- `Main` Yöntemdir giriş noktası yürütülebilir bir program; Burada, program denetimi başlar ve biter.
- `Main` bir sınıf veya yapı içinde bildirilir. `Main` olmalıdır [statik](../../../csharp/language-reference/keywords/static.md) ve olmaması [genel](../../../csharp/language-reference/keywords/public.md). (Önceki örnekte, varsayılan erişim aldığı [özel](../../../csharp/language-reference/keywords/private.md).) Kapsayan sınıfın veya yapının statik olması gerekli değildir.
- `Main` yalnızca birine sahip olabilir bir `void`, `int`, ya da C# 7.1 ile başlangıç `Task`, veya `Task<int>` dönüş türü.
- Ve yalnızca, `Main` döndürür bir `Task` veya `Task<int>`, bildirimi `Main` içerebilir [ `async` ](../../language-reference/keywords/async.md) değiştiricisi. Bu özellikle hariç Not bir `async void Main` yöntemi.
- `Main` Yöntemi ile veya olmadan bildirilebilir bir `string[]` komut satırı bağımsız değişkenleri içeren bir parametre. Visual Studio, Windows uygulamaları oluşturmak için kullanılırken, parametresi el ile ekleyin Aksi takdirde kullanmak <xref:System.Environment> komut satırı bağımsız değişkenlerini almak için sınıf. Parametre sıfır dizinli komut satırı bağımsız değişkenleri okunur. C ve C++'ın aksine, programın adı, ilk komut satırı bağımsız değişkeni işlenmez.

Ek `async` ve `Task`, `Task<int>` dönüş türleri, konsol uygulamaları başlatmak gerektiğinde program kodu basitleştirir ve `await` zaman uyumsuz işlemler `Main`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [C# Programı İçinde](../../../csharp/programming-guide/inside-a-program/index.md)  
