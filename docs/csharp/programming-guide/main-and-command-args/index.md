---
title: Main () ve komut satırı bağımsız değişkenleri-C# Programlama Kılavuzu
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
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200125"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)

`Main` Yöntemi, bir C# uygulamasının giriş noktasıdır. (Kitaplıklar ve hizmetler bir giriş noktası olarak `Main` bir yöntem gerektirmez.) Uygulama başlatıldığında, `Main` yöntemi çağrılan ilk yöntemdir.

 C# programında yalnızca bir giriş noktası olabilir. Yöntemine sahip birden fazla sınıfınız varsa, giriş noktası olarak hangi `Main` yöntemin kullanılacağını belirtmek için programınızı **/Main** derleyici seçeneğiyle derlemeniz gerekir. `Main` Daha fazla bilgi için bkz. [-Main (C# derleyici seçenekleri)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Genel Bakış

- `Main` Yöntemi, çalıştırılabilir programın giriş noktasıdır; Program denetiminin başladığı ve bittiği yerdir.
- `Main`bir sınıf veya yapı içinde bildirilmiştir. `Main`[statik](../../language-reference/keywords/static.md) olmalı ve [genel](../../language-reference/keywords/public.md)olmamalıdır. (Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.
- `Main`C# 7,1, `void` `Task`veya `Task<int>` dönüş `int`türü ile başlayan, veya, ya da olabilir.
- Ve yalnızca `Main` bir `Task` `Task<int>`veya döndürürse, bildirimi `Main` , [`async`](../../language-reference/keywords/async.md) değiştiricisini içerebilir. Bunun özellikle bir `async void Main` yöntemi dışladığı unutulmamalıdır.
- `Main` Yöntemi komut satırı bağımsız değişkenleri içeren bir `string[]` parametre ile veya olmadan bildirilemez. Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya [komut satırı bağımsız değişkenlerini](command-line-arguments.md)almak için <xref:System.Environment.GetCommandLineArgs> yöntemini kullanabilirsiniz. Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur. C ve C++ ' dan farklı olarak, programın adı `args` dizideki ilk komut satırı bağımsız değişkeni olarak değerlendirilmez, ancak <xref:System.Environment.GetCommandLineArgs> yöntemin ilk öğesidir.

Geçerli `Main` imzaların listesi aşağıda verilmiştir:

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

Yukarıdaki örneklerin hepsi ortak erişimci değiştiricisini kullanır. Bu tipik, ancak gerekli değildir.

`async` Ve `Task`' `Task<int>` nin eklenmesi, konsol uygulamalarının ' de `await` `Main`başlaması ve zaman uyumsuz işlemler gerektiğinde program kodunu basitleştirir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# programı içinde](../inside-a-program/index.md)
