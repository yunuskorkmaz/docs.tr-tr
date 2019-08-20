---
title: Main () dönüş değerleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 1be04f98a4dec1317c485c7e482568cfe48ea9bf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588885"
---
# <a name="main-return-values-c-programming-guide"></a>Main () dönüş değerleri (C# Programlama Kılavuzu)

Yöntemi şu şekilde dönebilir `void`: `Main`

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ayrıca, şunu döndürebilir `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Dönüş değeri `Main` kullanılmazsa, döndürme `void` biraz daha basit bir koda izin verir. Ancak, bir tamsayı döndürmek programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar. Dönüş değeri `Main` , işlem için çıkış kodu olarak değerlendirilir. Çıkış kodundan döndürülürse, örtülü `0`olarak olur. `Main` `void` Aşağıdaki örnekte, ' den `Main` dönüş değerine nasıl erişilebileceği gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek [.NET Core](../../../core/index.md) komut satırı araçlarını kullanır. .NET Core komut satırı araçları hakkında bilginiz yoksa, bu Başlarken konusunda bilgi edinebilirsiniz. [](../../../core/tutorials/using-with-xplat-cli.md)

`Main` *Program.cs* içindeki yöntemi aşağıdaki gibi değiştirin:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Bir program Windows 'da yürütüldüğünde, `Main` işlevden döndürülen herhangi bir değer bir ortam değişkeninde depolanır. Bu ortam değişkeni, bir toplu iş `ERRORLEVEL` dosyasından veya `$LastExitCode` PowerShell 'den kullanılarak alınabilir.

[DotNet CLI](../../../core/tools/dotnet.md) `dotnet build` komutunu kullanarak uygulamayı oluşturabilirsiniz.

Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin. Aşağıdaki kodu bir metin dosyasına yapıştırın ve projeyi içeren klasöre kaydedin `test.ps1` . PowerShell komut istemine yazarak `test.ps1` PowerShell betiğini çalıştırın.

Kod sıfır döndürdüğünden, toplu iş dosyası başarıyı bildirir. Ancak, MainReturnValTest.cs değerini sıfır olmayan bir değer döndürecek şekilde değiştirip programı yeniden derlerseniz, PowerShell betiğinin sonraki yürütmesi hata bildirir.

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Örnek çıkış

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Zaman uyumsuz ana dönüş değerleri

Zaman uyumsuz ana dönüş değerleri, içinde `Main` zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu derleyici tarafından oluşturulan koda taşır. Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Şimdi bu, şu şekilde değiştirilebilir:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu üretmesinin avantajına sahiptir.

## <a name="compiler-generated-code"></a>Derleyicinin ürettiği kod

Uygulama giriş noktası bir `Task` veya `Task<int>`döndürdüğünde, derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktasının çağrıldığı kabul edildiğinde `$GeneratedMain`, derleyici bu giriş noktaları için aşağıdaki kodu üretir:

- `static Task Main()`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Örnekler `Main` yöntemde değiştirici kullandıysanız `async` , derleyici aynı kodu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C#Başvurunun](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüle](./how-to-display-command-line-arguments.md)
