---
title: Ana() dönüş değerleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: f515268af13ef95b8b6d9a79f71c49d5d4a98d05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149844"
---
# <a name="main-return-values-c-programming-guide"></a>Ana() dönüş değerleri (C# programlama Kılavuzu)

`Main` Yöntemi döndürebilir `void`:

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ayrıca döndürebilir bir `int`:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

Döndürülen değeri `Main` döndüren kullanılmıyor `void` için biraz daha basit kod sağlar. Ancak, bir tamsayı döndüren diğer programları veya yürütülebilir dosya çağırma betikleri için durum bilgisi iletişim kurmak programın sağlar. Dönüş değeri `Main` işlemi için çıkış kodu olarak kabul edilir. Aşağıdaki örnek, dönüş değeri nasıl gösterir `Main` erişilebilir.

## <a name="example"></a>Örnek

Bu örnekte [.NET Core](../../../core/index.md) komut satırı araçları. .NET Core komut satırı araçlarıyla alışkın değilseniz, bunlarla ilgili bu öğrenebilirsiniz [Get başlatılan konu](../../../core/tutorials/using-with-xplat-cli.md).

Değiştirme `Main` yönteminde *program.cs* gibi:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Herhangi bir değer Windows programı yürütüldüğünde, döndürülen `Main` işlevi, bir ortam değişkeninde depolanır. Bu ortam değişkeni kullanılarak alınabilir `ERRORLEVEL` bir toplu iş dosyasından veya `$LastExitCode` powershell'den.

Kullanarak uygulama derleme [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutu.

Ardından, uygulamayı çalıştırmak ve sonucu görüntülemek için bir Powershell betiği oluşturun. Aşağıdaki kodu bir metin dosyasına yapıştırın ve kaydedileceği `test.ps1` projeyi içeren klasörü içinde. Yazarak powershell betiğini çalıştırma `test.ps1` powershell komut isteminde.

Toplu iş dosyası, kod sıfır döndürdüğünden, başarı rapor eder. Ancak, sıfır olmayan bir değer döndürmez ve ardından programı yeniden derlemek için MainReturnValTest.cs değiştirirseniz, powershell betiğinin sonraki yürütme hata rapor eder.

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

## <a name="async-main-return-values"></a>Async Main dönüş değerleri

Async Main dönüş değerleri taşımak için zaman uyumsuz yöntemleri çağırma gerekli ortak kod `Main` derleyici tarafından üretilen kod. Daha önce zaman uyumsuz kod arama ve zaman uyumsuz işlem tamamlanana kadar programınızı çalıştırdınız emin olmak için bu yapıyı yazma gerekir:

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

Şimdi bu tarafından değiştirilebilir:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Yeni sözdizimi avantajı, derleyici her zaman doğru kodu oluşturur ' dir.

## <a name="compiler-generated-code"></a>Derleyicinin ürettiği kodu

Uygulama giriş noktası döndürdüğünde bir `Task` veya `Task<int>`, derleyici uygulama kodunda bildirilen girdi noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktası çağrıldı varsayarak `$GeneratedMain`, derleyici bu giriş noktaları için şu kodu oluşturur:

- `static Task Main()` denk yayan derleme sonuçları `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` denk yayan derleme sonuçları `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` denk yayan derleme sonuçları `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` denk yayan derleme sonuçları `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Örnekleri kullandıysanız `async` değiştiricisi `Main` yöntemi, derleyici aynı kodu üretir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# başvurusu](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
