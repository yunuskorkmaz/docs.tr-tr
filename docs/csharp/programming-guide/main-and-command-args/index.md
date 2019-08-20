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
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588911"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () ve komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)

Yöntemi, bir C# uygulamanın giriş noktasıdır. `Main` (Kitaplıklar ve hizmetler bir giriş noktası olarak `Main` bir yöntem gerektirmez.) Uygulama başlatıldığında, `Main` yöntemi çağrılan ilk yöntemdir.

 Bir C# programda yalnızca bir giriş noktası olabilir. `Main` Yöntemine sahip birden fazla sınıfınız varsa, giriş noktası olarak hangi `Main` yöntemin kullanılacağını belirtmek için programınızı **/Main** derleyici seçeneğiyle derlemeniz gerekir. Daha fazla bilgi için bkz. [/MainC# (derleyici seçenekleri)](../../language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Genel Bakış

- `Main` Yöntemi, çalıştırılabilir programın giriş noktasıdır; program denetiminin başladığı ve bittiği yerdir.
- `Main`bir sınıf veya yapı içinde bildirilmiştir. `Main`[statik](../../language-reference/keywords/static.md) olmalı ve [genel](../../language-reference/keywords/public.md)olmamalıdır. (Önceki örnekte, [Private](../../language-reference/keywords/private.md)'ın varsayılan erişimini alır.) Kapsayan sınıf veya yapının statik olması gerekmez.
- `Main``int` C# yada`Task`, 7,1, veyadönüştüründenbaşlayarak,yadaolabilir.`Task<int>` `void`
- `Main` Ve yalnızca [`async`](../../language-reference/keywords/async.md) bir `Task` veya döndürürse`Task<int>`, bildirimi `Main` , değiştiricisini içerebilir. Bunun özellikle bir `async void Main` yöntemi dışladığı unutulmamalıdır.
- Yöntemi komut satırı bağımsız değişkenleri içeren bir `string[]` parametre ile veya olmadan bildirilemez. `Main` Windows uygulamaları oluşturmak için Visual Studio kullanırken, parametresini el ile ekleyebilir veya komut satırı bağımsız değişkenlerini almak için <xref:System.Environment> sınıfını kullanabilirsiniz. Parametreler, sıfır dizinli komut satırı bağımsız değişkenleri olarak okunurdur. C ve C++' nin aksine, programın adı ilk komut satırı bağımsız değişkeni olarak değerlendirilmez.

Ve `async` '`Task` `await` `Main`nin eklenmesi, konsol uygulamalarının ' de başlaması ve zaman uyumsuz işlemler gerektiğinde program kodunu basitleştirir. `Task<int>`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [C# Programı İçinde](../inside-a-program/index.md)
