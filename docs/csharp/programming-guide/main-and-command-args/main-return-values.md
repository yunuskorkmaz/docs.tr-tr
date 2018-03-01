---
title: "Ana() Dönüş Değerleri (C# Programlama Kılavuzu)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a>Ana() dönüş değerleri (C# programlama Kılavuzu)

`Main` Yöntemi dönebilirsiniz `void`:

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

Ayrıca dönebilirsiniz bir `int`:

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

Dönüş değeri, `Main` , döndürme kullanılmaz `void` için biraz daha basit kod sağlar. Ancak, bir tamsayı döndürme diğer programları veya yürütülebilir dosyanın çağırma betikleri durum bilgilerini iletmek program sağlar. Dönüş değerini `Main` işlem çıkış kodu olarak kabul edilir. Aşağıdaki örnek, dönüş nasıl değeri gösterir `Main` erişilebilir.

## <a name="example"></a>Örnek

Bu örnekte [.NET Core](../../../core/index.md) komut satırı araçları. .NET Core komut satırı araçları ile unfamilar varsa, bunları bu öğrenebilir [Get başlatılan konu](../../../core/tutorials/using-with-xplat-cli.md).

Değiştirme `Main` yönteminde *program.cs* gibi:

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

Windows'da bir program çalıştırıldığında, herhangi bir değer döndürülen `Main` işlevi bir ortam değişkeni depolanır. Bu ortam değişkenini kullanarak alınabilir `ERRORLEVEL` bir toplu iş dosyasından veya `$LastExitCode` powershell'den.

Kullanarak uygulama oluşturabilir [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` komutu.

Ardından, uygulamayı çalıştırın ve sonucu görüntülemek için bir Powershell betiği oluşturun. Bir metin dosyasına aşağıdaki kodu yapıştırın ve kaydedileceği `test.ps1` projeyi içeren klasörün içinde. Powershell betiği yazarak çalıştırırsınız `test.ps1` powershell komut isteminde.

Kodu sıfır döndürdüğünden, toplu iş dosyasını başarı rapor eder. Ancak, sıfır olmayan bir değer dönün ve ardından programı yeniden derleyin MainReturnValTest.cs değiştirirseniz, powershell betiği sonraki yürütülmesi hata bildirir.

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

Zaman uyumsuz ana dönüş değerleri taşımak için zaman uyumsuz yöntemleri çağırma gerekli Demirbaş kod `Main` derleyici tarafından üretilen kod için. Daha önce zaman uyumsuz kod çağırmak ve zaman uyumsuz işlemi tamamlanana kadar programı çalıştıran sağlamak için bu yapıyı yazma gerekir:

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

Şimdi, bu tarafından değiştirilebilir:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Yeni sözdizimini avantajlarından derleyici her zaman doğru kod oluşturur birisidir.

## <a name="compiler-generated-code"></a>Oluşturulan derleyici kodu

Uygulama giriş noktası döndüğünde bir `Task` veya `Task<int>`, derleyici uygulama kodunda bildirilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktası çağrıldı varsayılarak `$GeneratedMain`, bu giriş noktaları için aşağıdaki kod derleyici oluşturur:

- `static Task Main()`denk yayma derleyici sonuçları`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])`denk yayma derleyici sonuçları`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()`denk yayma derleyici sonuçları`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])`denk yayma derleyici sonuçları`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Örnekler kullandıysanız `async` değiştirici `Main` yöntemi derleyici aynı kodu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
[C# programlama kılavuzu](../../programming-guide/index.md)
[C# başvurusu](../index.md)
[ana() ve komut satırı bağımsız değişkenleri](index.md)
[nasıl yapılır: komut satırı görüntüleme Bağımsız değişkenler](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[nasıl yapılır: foreach kullanarak komut satırı bağımsız değişkenlerine erişme](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
