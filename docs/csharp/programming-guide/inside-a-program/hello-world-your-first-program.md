---
title: Hello World--İlk programınız - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 62aaf8785b0dfb646ea804dab6918940f1e33346
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635297"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World--İlk programınız (C# Programlama Kılavuzu)

Aşağıdaki yordam geleneksel "Hello World!"'ın bir C# sürümünü oluşturur. Program. Program dizesini görüntüler. `Hello World!`

Tanıtım kavramlarına daha fazla örnek için bkz: [Visual C# ve Visual Basic ile çalışmaya başlama](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Bir konsol uygulaması oluşturmak ve çalıştırmak için

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda, **dosya**, **yeni**, **proje**.

     **Yeni proje** iletişim kutusu açılır.

3. Genişletin **yüklü**, genişletme **şablonları**, genişletme **Visual C#** ve ardından **konsol uygulaması**.

4. İçinde **adı** kutusuna projeniz için bir ad belirtin ve ardından **Tamam** düğmesi.

     Yeni Proje görünür **Çözüm Gezgini**.

5. Program.cs içinde açık değilse **Kod Düzenleyicisi**, kısayol menüsünü açın **Program.cs** içinde **Çözüm Gezgini**ve ardından **Kodu Görüntüle**.

6. Program.cs içeriğini aşağıdaki kodla değiştirin.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Projeyi çalıştırmak için F5 tuşuna basın. Bir çizgi içeren bir komut istemi penceresi görünür `Hello World!`

Ardından, bu programın önemli bölümleri incelenir.

## <a name="comments"></a>Açıklamalar

İlk satır bir açıklama içerir. Karakterleri `//` satırın geri kalanını açıklamaya Dönüştür.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Metin bloğu arasında kapsayan tarafından da yorum yapabilecek `/*` ve `*/` karakter. Bu, aşağıdaki örnekte gösterilir.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>Main yöntemi

Bir C# konsol uygulaması içermelidir bir `Main` yöntemi, Denetim'ın başlar ve biter. `Main` Yöntemdir nesneleri oluşturduğunuz ve diğer bir yöntem yürütülemez.

`Main` Yöntemi bir [statik](../../../csharp/language-reference/keywords/static.md) bir sınıf ya da yapının içinde bulunan yöntemi. Önceki "Hello World!" Örneğin, adında bir sınıf içinde bulunduğu `Hello`. Bildirebilirsiniz `Main` aşağıdaki yollardan biriyle yöntemi:

- Geri dönebilirsiniz `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Bu, ayrıca bir tamsayı döndürebilir.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Dönüş türleri her ikisiyle bağımsız değişken alabilir.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     -veya-

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Parametresi `Main` yöntemi `args`, olan bir `string` program başlatmak için kullanılan komut satırı bağımsız değişkenleri içeren bir dizi. Farklı C++'da dizi yürütülebilir (exe) dosyanın adını içermez.

Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için bkz: örneklerde [ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md) ve [nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

Çağrı <xref:System.Console.ReadKey%2A> sonunda `Main` yöntemi kapatılmasını programınızı F5 tuşuna basarak hata ayıklama modunda çalıştırdığınızda, çıktıyı okuma şansı bulamadan konsol penceresinde engeller.

## <a name="input-and-output"></a>Giriş ve çıkış

C# programları genellikle .NET Framework'ün çalışma zamanı kitaplığı tarafından sağlanan giriş/çıkış hizmetlerini kullanır. Deyim `System.Console.WriteLine("Hello World!");` kullanan <xref:System.Console.WriteLine%2A> yöntemi. Bu çıkış yöntemlerinden biridir <xref:System.Console> Çalışma Zamanı Kitaplığı'nda sınıfı. Yeni bir satır tarafından izlenen standart çıktı akışında kendi dize parametresini görüntüler. Diğer <xref:System.Console> yöntemleri farklı giriş ve çıkış işlemleri için kullanılabilir. Eklerseniz `using System;` yönerge programın başında, doğrudan kullanabilirsiniz <xref:System> sınıflarını ve yöntemlerini tamamen nitelendirmeden. Örneğin, çağırabilirsiniz `Console.WriteLine` yerine `System.Console.WriteLine`:

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Giriş/Çıkış yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.IO>.

## <a name="command-line-compilation-and-execution"></a>Komut satırı derlemesi ve yürütme

"Hello World!" derlemesi Visual Studio tümleşik geliştirme ortamı (IDE yerine) komut satırını kullanarak program'ı tıklatın.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Derlemek ve bir komut satırından çalıştırmak için

1. Önceki yordamdaki kodu herhangi bir metin düzenleyiciye yapıştırın ve dosyayı bir metin dosyası olarak kaydedin. Dosyayı `Hello.cs` olarak adlandırın. C# kaynak kodu dosyaları uzantısını kullanır `.cs`.

2. Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Windows 10 üzerinde **Başlat** menüsünde `Developer Command Prompt`, seçin ve ardından dokunun **VS 2017 için geliştirici komut istemi**.

         Bir geliştirici komut istemi penceresi görüntülenir.

    - Windows 7'de açın **Başlat** menüsünde, geçerli Visual Studio sürümü için klasörünü genişletin, kısayol menüsünü açın **Visual Studio Araçları**ve ardından **Geliştirici komut istemi VS 2017 için**.

         Bir geliştirici komut istemi penceresi görüntülenir.

    - Standart bir komut istemi penceresinden komut satırı yapılarını etkinleştirin.

         Bkz: [nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).

3. Komut İstemi penceresinde içeren klasöre gidin, `Hello.cs` dosya.

4. Derlemek için aşağıdaki komutu girin `Hello.cs`.

     `csc Hello.cs`

     Programınızı adında bir yürütülebilir dosya hiç derleme hatası varsa `Hello.exe` oluşturulur.

5. Komut İstemi penceresinde, programı çalıştırmak için aşağıdaki komutu girin:

     `Hello`

 C# derleyicisi ve seçenekleri hakkında daha fazla bilgi için bkz: [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Programı İçinde](../../../csharp/programming-guide/inside-a-program/index.md)
- [Dizeler](../../../csharp/programming-guide/strings/index.md)
- [Örnekler ve öğreticiler](../../../samples-and-tutorials/index.md)
- [C# başvurusu](../../../csharp/language-reference/index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Visual C# ve Visual Basic'e Başlarken](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
