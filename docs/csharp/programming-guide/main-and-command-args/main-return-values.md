---
title: Main () dönüş değerleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 13d1eda178a4c2580af67ef5a7198e7f0884a7d6
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884403"
---
# <a name="main-return-values-c-programming-guide"></a>Main () dönüş değerleri (C# Programlama Kılavuzu)

`Main` yöntemi `void`döndürebilir:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ayrıca, bir `int`döndürebilir:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

`Main` dönüş değeri kullanılmazsa, `void` döndürme biraz daha basit bir koda izin verir. Ancak, bir tamsayı döndürmek programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar. `Main` dönüş değeri, işlem için çıkış kodu olarak değerlendirilir. `Main` `void` döndürüldüğünde çıkış kodu örtük olarak `0`olur. Aşağıdaki örnek, `Main` ' den dönüş değerine nasıl erişildiğini gösterir.

## <a name="example"></a>Örnek

Bu örnek [.NET Core](../../../core/index.md) komut satırı araçlarını kullanır. .NET Core komut satırı araçları hakkında bilginiz yoksa [, bu Başlarken konusunda bilgi](../../../core/tutorials/cli-create-console-app.md)edinebilirsiniz.

*Program.cs* içinde `Main` yöntemini aşağıdaki gibi değiştirin:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Bir program Windows 'da yürütüldüğünde, `Main` işlevinden döndürülen herhangi bir değer bir ortam değişkeninde depolanır. Bu ortam değişkeni bir toplu iş dosyasından `ERRORLEVEL` veya PowerShell 'den `$LastExitCode` kullanılarak alınabilir.

[DotNet clı](../../../core/tools/dotnet.md) `dotnet build` komutunu kullanarak uygulamayı oluşturabilirsiniz.

Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin. Aşağıdaki kodu bir metin dosyasına yapıştırın ve projeyi içeren klasöre `test.ps1` olarak kaydedin. PowerShell komut isteminde `test.ps1` yazarak PowerShell betiğini çalıştırın.

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

## <a name="sample-output"></a>Örnek çıktı

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Zaman uyumsuz ana dönüş değerleri

Zaman uyumsuz ana dönüş değerleri, derleyici tarafından oluşturulan koda `Main` zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu taşır. Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:

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

Uygulama giriş noktası bir `Task` veya `Task<int>`döndürdüğünde, derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktasının `$GeneratedMain`çağrıldığı kabul edildiğinde, derleyici bu giriş noktaları için aşağıdaki kodu üretir:

- `static Task Main()`, derleyicinin `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur
- `static Task Main(string[])`, derleyicinin `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur
- `static Task<int> Main()`, derleyicinin `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur
- `static Task<int> Main(string[])`, derleyicinin `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` eşdeğerini yaymasına neden olur

> [!NOTE]
>Örnekler `Main` yönteminde `async` değiştirici kullandıysanız, derleyici aynı kodu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C#Başvurunun](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme](./how-to-display-command-line-arguments.md)
