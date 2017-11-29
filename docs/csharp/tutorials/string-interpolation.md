---
title: "Dize ilişkilendirme - C#"
description: "C# 6'dizesi ilişkilendirme nasıl çalıştığını öğrenin"
keywords: .NET, .NET core, C#, dize
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: ac19d4208da4f8ee6dd3e071ab70dbc41a0cd065
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="string-interpolation-in-c"></a>C# dize ilişkilendirme #

Dize ilişkilendirme bir dize yer tutucuları bir dize değişkeni değeriyle değiştirilir yoludur. Bunu yapmanın yolu olan C# 6'dan önce `System.String.Format`. Bu Tamam çalışır, ancak numaralı yer tutucuları kullandığından, okumak daha zor ve daha ayrıntılı olabilir.

Diğer programlama dilleri dize ilişkilendirme dilinde yerleşik bir süre beklendiğinden. Örneğin, PHP ile:

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

C# 6'da, son olarak bu dize ilişkilendirme stilini sunuyoruz. Kullanabileceğiniz bir `$` önce değişkenleri/ifadeleri değerlerine için alternatif belirtmek için bir dize.

## <a name="prerequisites"></a>Önkoşullar
.NET core çalışmasına, makine ayarlamanız gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası.
Bu uygulama, Windows, Ubuntu Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. Kullanım aşağıda açıklamaları [Visual Studio Code](https://code.visualstudio.com/) platform Düzenleyicisi arası bir açık kaynak olduğu. Ancak, tanımanız ne olursa olsun araçları kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulama oluşturma

Tüm Araçlar yüklediniz, yeni bir .NET Core uygulaması oluşturun. Komut satırı Oluşturucu kullanmak için projeniz için bir dizin gibi oluşturun `interpolated`ve sık kullanılan kabuğuna şu komutu çalıştırın:

```
dotnet new console
```

Bu komutu proje dosyasıyla birlikte bir temel .NET core projesi oluşturacaksınız *interpolated.csproj*ve kaynak kodu dosyasının *Program.cs*. Yürütme gerekecek `dotnet restore` bu projeyi derlemek için gerekli bağımlılıkların geri yüklemek için.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı çalıştırmak üzere kullanmadan `dotnet run`. "Hello, World" çıkışı konsola görmeniz gerekir.



## <a name="intro-to-string-interpolation"></a>İlişkilendirme dize giriş

İle `System.String.Format`, "yer tutucuları" dizesini izleyen parametreleri tarafından değiştirilen bir dize belirtin. Örneğin:

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

Bu, "adımın Matt Groves olduğu" çıkarır.

C# 6 kullanmak yerine, `String.Format`, Ara değerli bir dize ile başlayan tanımladığınız `$` sembol ve sonra doğrudan dizesindeki değişkenleri kullanma. Örneğin:

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

Yalnızca değişkenleri kullanmanız gerekmez. Köşeli ayraçlar içindeki herhangi bir ifade kullanabilirsiniz. Örneğin:

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

Hangi çıktı:

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a>Dize ilişkilendirme nasıl çalışır?

Arka planda Bu dize ilişkilendirme sözdizimi derleyici tarafından String.Format çevrilir. Bu nedenle, yapabileceğiniz [aynı türde öğe işiniz önce String.Format ile](https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx).

Örneğin, doldurma ve sayısal biçimlendirme ekleyebilirsiniz:

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

Yukarıdaki gibi bir çıktı:

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

Bir değişken adı bulunmazsa, derleme zamanı hatası oluşturulur.

Örneğin:

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

Bu derleme hataları alırsınız:
 
* `Cannot use local variable 'adj' before it is declared`- `adj` değildi değişkeni bildirilen kadar *sonra* Ara değerli dize.
* `The name 'otheranimal' does not exist in the current context`-bir değişken adı verilen `otheranimal` hiçbir zaman bile bildirildi

## <a name="localization-and-internationalization"></a>Yerelleştirme ve uluslararası hale getirme

Ara değerli bir dize destekleyen `IFormattable` ve `FormattableString`, hangi uygulamalar için yararlı olabilir.

Varsayılan olarak, geçerli kültürü Ara değerli bir dize kullanır. Farklı bir kültür kullanmak için olarak cast`IFormattable`

Örneğin:

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a>Sonuç 

Bu öğreticide, dize ilişkilendirme özelliklerinin C# 6'ın nasıl kullanılacağını öğrendiniz. Temel yazma basit daha kısa bir yol olduğu `String.Format` ifadelerle daha gelişmiş kullanımları için bazı uyarılar.
