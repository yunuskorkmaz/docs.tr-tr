---
title: Üst düzey deyimler-C# öğreticisi
description: Bu öğreticide, fikirlerinizi araştırırken en üst düzey deyimlerinizi deneyip kanıtlarken kavram kanıtlarını nasıl kullanabileceğiniz gösterilmektedir
ms.date: 10/28/2020
ms.openlocfilehash: 5e5dc6cec382baa69ac8cb4625684315bb2cd5e0
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282265"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a>Öğretici: öğreniniz sırasında kod derlemek için en üst düzey deyimleri kullanarak fikirleri araştırma

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - En üst düzey deyimlerinizi kullanmanızı düzenleyen kuralları öğrenin.
> - Algoritmaları araştırmak için en üst düzey deyimleri kullanın.
> - Araştırmaları yeniden kullanılabilir bileşenlerle yeniden düzenleyin.

## <a name="prerequisites"></a>Önkoşullar

Makinenizde C# 9 derleyicisini içeren .NET 5 ' i çalıştıracak şekilde ayarlamanız gerekir. C# 9 derleyicisi, [Visual Studio 2019 sürüm 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) veya [.NET 5,0 SDK](https://dot.net/get-dotnet5)ile başlayarak kullanılabilir.

Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="start-exploring"></a>Keşfetmeye başlayın

Üst düzey deyimler, programınızın giriş noktasını bir sınıftaki statik bir yönteme yerleştirerek gereken ek bir sertifika oluşmasını önlemenize olanak sağlar. Yeni bir konsol uygulaması için tipik başlangıç noktası aşağıdaki kod gibi görünür:

```csharp
using System;

namespace Application
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Yukarıdaki kod, `dotnet new console` komutunu çalıştırmanın ve yeni bir konsol uygulaması oluşturmanın sonucudur. Bu 11 satır yalnızca bir adet yürütülebilir kod içerir. Bu programı, yeni en üst düzey deyimler özelliğiyle basitleştirebilirsiniz. Bu, bu programdaki satırlardan yalnızca birini kaldırmanızı sağlar:

```csharp
using System;

Console.WriteLine("Hello World!");
```

Bu eylem, yeni fikirleri keşfetmeye başlamak için gerekenleri basitleştirir. Komut dosyası senaryoları için en üst düzey deyimleri kullanabilir veya keşfedebilirsiniz. Temel bilgileri aldıktan sonra kodu yeniden düzenlemeye başlayabilir ve derlediğiniz yeniden kullanılabilir bileşenler için yöntemler, sınıflar veya diğer derlemeler oluşturabilirsiniz. Üst düzey deyimler hızlı deneme ve başlangıç öğreticilerini etkinleştirir. Ayrıca, deneme 'den tam programlara sorunsuz bir yol sağlar.

Üst düzey deyimler dosyada göründükleri sırada yürütülür. En üst düzey deyimler yalnızca uygulamanızdaki tek bir kaynak dosyasında kullanılabilir. Birden çok dosyada kullandığınızda derleyici bir hata oluşturur.

## <a name="build-a-magic-net-answer-machine"></a>Sihirli .NET yanıt makinesi oluşturma

Bu öğreticide, rastgele bir Yanıt ile "Evet" veya "Hayır" sorusunu yanıtlayan bir konsol uygulaması oluşturalım. Adım adım işlevselliği oluşturacaksınız. Tipik bir programın yapısı için gereken sertifika yerine görevliliğe odaklanırsınız. Daha sonra, işlevsellikten memnun olduğunuzda uygulamayı uygun gördüğünüz şekilde yeniden düzenleyebilirsiniz.

İyi bir başlangıç noktası, soruyu konsola geri yazmaktır. Aşağıdaki kodu yazarak başlayabilirsiniz:

```csharp
using System;

Console.WriteLine(args);
```

Bir değişken bildiremezsiniz `args` . En üst düzey deyimlerinizi içeren tek kaynak dosya için, derleyici `args` komut satırı bağımsız değişkenlerini anlamı olarak tanır. Bağımsız değişkenlerin türü `string[]` , tüm C# programlarında olduğu gibi.

Aşağıdaki komutu çalıştırarak kodunuzu test edebilirsiniz `dotnet run` :

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

Komut satırındaki öğesinden sonraki bağımsız değişkenler `--` programa geçirilir. Nesnenin türünü görebilirsiniz `args` çünkü bu, konsola yazdırılmıştır:

```console
System.String[]
```

Soruyu konsola yazmak için, bağımsız değişkenleri numaralandırın ve bir boşluk ile ayırmanız gerekir. `WriteLine`Çağrıyı aşağıdaki kodla değiştirin:

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

Artık programı çalıştırdığınızda, soruyu bir bağımsız değişken dizesi olarak doğru şekilde görüntüler.

## <a name="respond-with-a-random-answer"></a>Rastgele bir Yanıtla yanıtla

Soruyu yankıladıktan sonra rastgele yanıtı oluşturmak için kodu ekleyebilirsiniz. Olası bir yanıt dizisi ekleyerek başlayın:

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

Bu dizide, komite olmayan ve altı negatif olan 12 yanıt vardır. Sonra, diziden rastgele bir yanıt oluşturmak ve bu yanıtı göstermek için aşağıdaki kodu ekleyin:

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

Sonuçları görmek için uygulamayı yeniden çalıştırabilirsiniz. Aşağıdaki çıktıya benzer bir şey görmeniz gerekir:

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

Bu kod soruları yanıtlar, ancak bir özellik ekleyelim. Soru uygulamanızı, yanıt hakkında düşünmeyi benzetmek istiyorsunuz. Bunu, ASCII animasyonunu bir bit ekleyerek ve çalışırken duraklatarak yapabilirsiniz.  Soruyu yankılayan satırdan sonra aşağıdaki kodu ekleyin:

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

Ayrıca, `using` kaynak dosyanın en üstüne bir ifade eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

`using`Deyimler, dosyadaki diğer deyimlerden önce olmalıdır. Aksi halde derleyici hatası olur. Programı yeniden çalıştırabilir ve animasyonu görebilirsiniz. Bu, daha iyi bir deneyim sunar. Zevkinizi eşleştirmeye yönelik gecikmenin uzunluğu ile denemeler yapın.

Yukarıdaki kod, boşlukla ayrılmış bir dönen çizgiler kümesi oluşturur. `await`Anahtar sözcüğü eklemek derleyiciye, değiştiriciye sahip bir yöntem olarak program giriş noktasını oluşturmasını söyler `async` ve bir döndürür <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> . Bu program bir değer döndürmüyor, bu nedenle program giriş noktası bir döndürür `Task` . Programınız bir tamsayı değeri döndürürse, en üst düzey deyimlerinizin sonuna bir return deyimi eklersiniz. Bu return ifadesinde döndürülecek tamsayı değeri belirtilebilir. En üst düzey deyimlerinizin bir ifadesi varsa `await` , dönüş türü olur <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> .

## <a name="refactoring-for-the-future"></a>Geleceğe yönelik yeniden düzenleme

Programınız aşağıdaki kod gibi görünmelidir:

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

Yukarıdaki kod mantıklı. İşe yarar. Ancak yeniden kullanılabilir değil. Uygulamanın çalışır durumda olduğuna göre, yeniden kullanılabilir parçalar çekmeniz zaman alabilir.

Bir aday, bekleyen animasyonu görüntüleyen koddur. Bu kod parçacığı bir yöntem haline gelebilir:

Dosyanızda yerel bir işlev oluşturarak başlayabilirsiniz. Geçerli animasyonu şu kodla değiştirin:

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

Yukarıdaki kod, ana yönteminizin içinde yerel bir işlev oluşturur. Yine de yeniden kullanılabilir değildir. Bu nedenle, kodu bir sınıfa ayıklayın. *Utilities.cs* adlı yeni bir dosya oluşturun ve aşağıdaki kodu ekleyin:

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

En üst düzey deyimler yalnızca bir dosya içinde olabilir ve bu dosya ad alanları veya türler içeremez.

Son olarak, bir yinelemeyi kaldırmak için animasyon kodunu temizleyebilirsiniz:

:::code language="csharp" source="snippets/top-level-statements/Utilities.cs" ID="Animation":::

Artık bir uygulamanız vardır ve daha sonra kullanmak üzere yeniden kullanılabilir parçalar yeniden düzenlenmiş.

## <a name="summary"></a>Özet

En üst düzey deyimler, yeni algoritmaları araştırmak için kullanılmak üzere basit programlar oluşturmayı kolaylaştırır. Farklı kod parçacıkları deneyerek algoritmalarla denemeler yapabilirsiniz. Ne işe yarar olduğunu öğrendikten sonra kodu daha sürdürülebilir olacak şekilde yeniden düzenleyebilirsiniz.

Üst düzey deyimler Konsol uygulamalarını temel alan programları basitleştirir. Bunlar Azure işlevleri, GitHub eylemleri ve diğer küçük yardımcı programları içerir.
