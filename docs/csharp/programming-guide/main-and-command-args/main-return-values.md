---
title: Ana() İade Değerleri - C# Programlama Kılavuzu
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 3d97ab2b3f53179cb184f2ad3944ea29ff5566a2
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345122"
---
# <a name="main-return-values-c-programming-guide"></a>Ana() iade değerleri (C# Programlama Kılavuzu)

Yöntem `Main` döndürebilir: `void`

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

Ayrıca bir `int`döndürebilir:

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

İade `Main` değeri kullanılmazsa, geri `void` döndürme biraz daha basit bir kod sağlar. Ancak, bir arayıcı döndürülen program, durum bilgilerini yürütülebilir dosyayı çağıran diğer programlara veya komut dosyalarına iletilmesini sağlar. Gelen `Main` iade değeri, işlemin çıkış kodu olarak kabul edilir. Çıkış `void` kodundan `Main` döndürülürse örtülü `0`olarak . Aşağıdaki örnek, geri `Main` dönüş değerinin nasıl erişilebildiğini gösterir.

## <a name="example"></a>Örnek

Bu örnekte [.NET Core](../../../core/index.yml) komut satırı araçları kullanılıyor. .NET Core komut satırı araçlarını bilmiyorsanız, bu [Başlangıç konusu](../../../core/tutorials/cli-create-console-app.md)hakkında bilgi edinebilirsiniz.

Yöntemi `Main` aşağıdaki *gibi program.cs* değiştirin:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Bir program Windows'da yürütüldüğünde, `Main` işlevden döndürülen herhangi bir değer bir ortam değişkeninde depolanır. Bu ortam değişkeni bir `ERRORLEVEL` toplu iş dosyasından veya `$LastExitCode` powershell'den alınabilir.

Uygulamayı [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutunu kullanarak oluşturabilirsiniz.

Ardından, uygulamayı çalıştırmak ve sonucu görüntülemek için bir Powershell komut dosyası oluşturun. Aşağıdaki kodu bir metin dosyasına yapıştırın `test.ps1` ve projeyi içeren klasörde olduğu gibi kaydedin. Powershell komut isteminde `test.ps1` yazarak powershell komut dosyasını çalıştırın.

Kod sıfır döndürüldüğünden, toplu işdosyası başlıcayı bildirir. Ancak, MainReturnValTest.cs sıfır olmayan bir değeri döndürmek ve sonra programı yeniden derlemek için değiştirirseniz, powershell komut dosyasının sonraki yürütülmesi hata bildirir.

```dotnetcli
dotnet run
```

```powershell
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

## <a name="async-main-return-values"></a>Async Ana iade değerleri

Async Main return değerleri, derleyici tarafından oluşturulan `Main` koda eşzamanlı yöntemleri çağırmak için gerekli olan ortak kodu taşır. Daha önce, eşzamanlı kodu çağırmak ve programınızın eşzamanlı işlem tamamlanana kadar çalıştırdığından emin olmak için bu yapıyı yazmanız gerekir:

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

Şimdi, bu değiştirilebilir:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu oluşturmasıdır.

## <a name="compiler-generated-code"></a>Derleyici oluşturulan kod

Uygulama giriş noktası a `Task` `Task<int>`veya , derleyici döndürdüğünde, uygulama kodunda bildirilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktasının `$GeneratedMain`çağrıldığını varsayarsak, derleyici bu giriş noktaları için aşağıdaki kodu oluşturur:

- `static Task Main()`eşdeğeri yayan derleyici sonuçları`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`eşdeğeri yayan derleyici sonuçları`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`eşdeğeri yayan derleyici sonuçları`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`eşdeğeri yayan derleyici sonuçları`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Örnekler `Main` yöntemde `async` değiştirici kullanılırsa, derleyici aynı kodu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Referans](../index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](index.md)
- [Komut satırı bağımsız değişkenleri nasıl görüntülenir?](./how-to-display-command-line-arguments.md)
