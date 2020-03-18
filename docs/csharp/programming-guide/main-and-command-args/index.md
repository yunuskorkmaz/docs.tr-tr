---
title: Ana() ve komut satırı bağımsız değişkenleri - C# Programlama Kılavuzu
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
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700607"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Ana() ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)

Yöntem, `Main` C# uygulamasının giriş noktasıdır. (Kitaplıklar ve hizmetler `Main` giriş noktası olarak bir yöntem gerektirmez.) Uygulama başlatıldığında, `Main` yöntem çağrılan ilk yöntemdir.

 C# programında yalnızca bir giriş noktası olabilir. Bir `Main` yöntemi olan birden fazla sınıf varsa, giriş noktası olarak hangi `Main` yöntemi kullanacağınızı belirtmek için programınızı **/main** derleyici seçeneğiyle derlemeniz gerekir. Daha fazla bilgi için bkz: [-main (C# Derleyici Seçenekleri)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Genel Bakış

- Yöntem, `Main` çalıştırılabilir bir programın giriş noktasıdır; program denetiminin başladığı ve bittiği yerdir.
- `Main`bir sınıf veya yapı içinde bildirilir. `Main`[statik](../../language-reference/keywords/static.md) olmalı ve herkese [açık](../../language-reference/keywords/public.md)olması gerekmez. (Önceki örnekte, [özel](../../language-reference/keywords/private.md)varsayılan erişim alır.) Çevreleyen sınıf veya yapı statik olması gerekmez.
- `Main`c# `void`7.1 `int` `Task`ile başlayan veya `Task<int>` dönüş türüne sahip olabilir.
- Eğer ve `Main` sadece `Task` bir `Task<int>`veya döndürür, bildirimi `Main` [`async`](../../language-reference/keywords/async.md) değiştirici içerebilir. Bunun özellikle bir `async void Main` yöntemi dışladığını unutmayın.
- Yöntem `Main` komut satırı bağımsız değişkenleri içeren bir `string[]` parametre ile veya olmadan bildirilebilir. Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametreyi el <xref:System.Environment.GetCommandLineArgs> ile ekleyebilir veya [komut satırı bağımsız değişkenlerini](command-line-arguments.md)elde etmek için yöntemi kullanabilirsiniz. Parametreler sıfır dizine bizinlenmiş komut satırı bağımsız değişkenleri olarak okunur. C ve C++'Dan farklı olarak, programın adı `args` dizideki ilk komut satırı bağımsız değişkeni olarak <xref:System.Environment.GetCommandLineArgs> kabul edilmez, ancak yöntemin ilk öğesidir.

Geçerli imzaların listesi `Main` aşağıda veda edilebistir:

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

Konsol uygulamalarının `Task` `Task<int>` başlatılması gerektiğinde ve , return türlerinin `async` eklenmesi `await` ve , iade `Main`türleri program kodunu basitleştirir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# Programı İçinde](../inside-a-program/index.md)
