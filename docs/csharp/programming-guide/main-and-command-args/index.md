---
title: Main () ve komut satırı bağımsız değişkenleri- C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: a5707e8cfff11dd9d27fffc9deb41662fb2c4460
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281762"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)

`Main` yöntemi, bir C# uygulamanın giriş noktasıdır. (Kitaplıklar ve hizmetler, giriş noktası olarak bir `Main` yöntemi gerektirmez.) Uygulama başlatıldığında `Main` yöntemi çağrılan ilk yöntemdir.

 Bir C# programda yalnızca bir giriş noktası olabilir. `Main` yöntemine sahip birden fazla sınıfınız varsa, giriş noktası olarak hangi `Main` yönteminin kullanılacağını belirtmek için programınızı **/Main** derleyici seçeneğiyle derlemeniz gerekir. Daha fazla bilgi için bkz. [-MainC# (derleyici seçenekleri)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Genel Bakış

- `Main` yöntemi, çalıştırılabilir programın giriş noktasıdır; Program denetiminin başladığı ve bittiği yerdir.
- `Main` bir sınıf veya yapı içinde bildirilmiştir. `Main` [statik](../../language-reference/keywords/static.md) olması ve [genel](../../language-reference/keywords/public.md)olmaması gerekir. (Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.
- `Main`, C# 7,1, `Task`veya `Task<int>` dönüş türünden başlayarak `void`, `int`ya da olabilir.
- Yalnızca `Main` bir `Task` veya `Task<int>`döndürürse, `Main` bildirimi [`async`](../../language-reference/keywords/async.md) değiştiricisini içerebilir. Bunun özellikle bir `async void Main` yöntemi dışladığı unutulmamalıdır.
- `Main` yöntemi komut satırı bağımsız değişkenleri içeren bir `string[]` parametresiyle veya bu parametre olmadan bildirilebilecek. Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya [komut satırı bağımsız değişkenlerini](command-line-arguments.md)almak için <xref:System.Environment.GetCommandLineArgs> yöntemini kullanabilirsiniz. Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur. C ve C++' nin aksine, programın adı `args` dizideki ilk komut satırı bağımsız değişkeni olarak değerlendirilmez, ancak <xref:System.Environment.GetCommandLineArgs> yönteminin ilk öğesidir.

Geçerli `Main` imzalarının listesi aşağıda verilmiştir:

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

`async` ve `Task`ekleme `Task<int>` dönüş türleri, konsol uygulamalarının `Main`zaman uyumsuz işlemlere `await` başlaması gerektiğinde program kodunu basitleştirir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# Programı İçinde](../inside-a-program/index.md)
