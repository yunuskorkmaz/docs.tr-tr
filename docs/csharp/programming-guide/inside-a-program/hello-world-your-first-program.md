---
title: Merhaba Dünya--ilk program C# programlama kılavuzunuz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 9a50de0bb583a1dfccfa609be1cca732868505ba
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589380"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Merhaba Dünya--ilk programınız (C# Programlama Kılavuzu)

Aşağıdaki yordam geleneksel bir C# "Merhaba Dünya!" sürümü oluşturuyor programda. Program dizeyi görüntüler`Hello World!`

Tanıtım kavramlarıyla ilgili daha fazla örnek için bkz. [Visual C# ve Visual Basic kullanmaya](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)başlama.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-and-run-a-console-application"></a>Bir konsol uygulaması oluşturmak ve çalıştırmak için

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda, **dosya**, **yeni**, **proje**.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **C#görsel**' i genişletin ve **konsol uygulaması**' nı

4. **Ad** kutusunda, projeniz için bir ad belirtin ve sonra **Tamam** düğmesini seçin.

     Yeni proje **Çözüm Gezgini**görüntülenir.

5. **Kod Düzenleyicisi**'nde program.cs açık değilse, **Çözüm Gezgini**için kısayol menüsünü açın ve sonra **kodu görüntüle**' yi seçin.

6. Program.cs içeriğini aşağıdaki kodla değiştirin.

     [!code-csharp[csProgGuide#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#21)]

7. Projeyi çalıştırmak için F5 tuşunu seçin. Satırı içeren bir komut Istemi penceresi görünür`Hello World!`

Daha sonra, bu programın önemli bölümleri incelenir.

## <a name="comments"></a>Açıklamalar

İlk satır bir açıklama içerir. Karakterler `//` satırın geri kalanını açıklamaya dönüştürür.

 [!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Ayrıca, bir metin bloğunu, `/*` ve `*/` karakterleri arasına ekleyerek açıklama ekleyebilirsiniz. Bu, aşağıdaki örnekte gösterilir.

 [!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

## <a name="main-method"></a>Main yöntemi

C# Konsol uygulaması, denetimin başladığı ve `Main` bittiği bir yöntemi içermelidir. `Main` Yöntemi nesne oluşturduğunuz ve diğer yöntemleri yürütebileceğiniz yerdir.

Yöntemi, bir sınıf veya yapı içinde bulunan statik bir yöntemdir. [](../../language-reference/keywords/static.md) `Main` Önceki "Merhaba Dünya!" örnek, adlı `Hello`bir sınıfta bulunur. `Main` Yöntemi aşağıdaki yöntemlerden biriyle bildirebilirsiniz:

- Bu, döndürebilir `void`.

     [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Ayrıca, bir tamsayı döndürebilir.

     [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Dönüş türlerinden biri ile bağımsız değişken alabilir.

     [!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

     -veya-

     [!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Yönteminin parametresi, programı çağırmak için kullanılan komut satırı `string` bağımsız değişkenlerini içeren bir dizidir. `args` `Main` Öğesinden farklı C++olarak, dizi yürütülebilir (exe) dosyanın adını içermez.

Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için, [ana () ve komut satırı bağımsız değişkenlerinde](../main-and-command-args/index.md) örneklere ve [nasıl yapılacağını görün: Komut satırını](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)kullanarak derlemeleri oluşturun ve kullanın.

`Main` Yönteminin sonunda öğesine yapılan <xref:System.Console.ReadKey%2A> çağrı, F5 tuşuna basarak, programınızı hata ayıklama modunda çalıştırdığınızda çıktıyı okuma şansınız olmadan önce konsol penceresinin bitmesini önler.

## <a name="input-and-output"></a>Girdi ve çıktı

C#programlar genellikle .NET Framework çalışma zamanı kitaplığı tarafından sunulan giriş/çıkış hizmetlerini kullanır. İfade `System.Console.WriteLine("Hello World!");` yöntemini<xref:System.Console.WriteLine%2A> kullanır. Bu, çalışma zamanı kitaplığındaki <xref:System.Console> sınıfının çıkış yöntemlerinden biridir. Dize parametresini standart çıkış akışında ve ardından yeni bir satırla görüntüler. Farklı <xref:System.Console> giriş ve çıkış işlemleri için diğer yöntemler kullanılabilir. Programın başına `using System;` yönergesini eklerseniz, <xref:System> sınıfları ve yöntemleri tamamen nitelemeden doğrudan kullanabilirsiniz. Örneğin, `Console.WriteLine` `System.Console.WriteLine`yerine şunu çağırabilirsiniz:

 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

 [!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Giriş/çıkış yöntemleri hakkında daha fazla bilgi için bkz <xref:System.IO>.

## <a name="command-line-compilation-and-execution"></a>Komut satırı derleme ve yürütme

"Merhaba Dünya!" öğesini derleyebilirsiniz Visual Studio tümleşik geliştirme ortamı (IDE) yerine komut satırını kullanarak program.

### <a name="to-compile-and-run-from-a-command-prompt"></a>Derlemek ve bir komut satırından çalıştırmak için

1. Önceki yordamdan kodu herhangi bir metin düzenleyicisine yapıştırın ve sonra dosyayı bir metin dosyası olarak kaydedin. Dosyayı `Hello.cs` olarak adlandırın. C#kaynak kodu dosyaları uzantısını `.cs`kullanır.

2. Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:

    - Windows 10 ' da, **Başlat** menüsünde, için `Developer Command Prompt`arama yapın ve sonra **vs 2017 için geliştirici komut istemi**' yi seçin.

         Geliştirici Komut İstemi bir pencere görüntülenir.

    - Windows 7 ' de, **Başlat** menüsünü açın, Visual Studio 'nun geçerli sürümüne ait klasörü genişletin, **Visual Studio Araçları**için KıSAYOL menüsünü açın ve **vs 2017 için geliştirici komut istemi**öğesini seçin.

         Geliştirici Komut İstemi bir pencere görüntülenir.

    - Komut satırı derlemelerini standart bir komut Istemi penceresinden etkinleştirin.

         Bkz [. nasıl yapılır: Visual Studio komut satırı](../../language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)için ortam değişkenlerini ayarlayın.

3. Komut istemi penceresinde, `Hello.cs` dosyanızı içeren klasöre gidin.

4. Derlemek `Hello.cs`için aşağıdaki komutu girin.

     `csc Hello.cs`

     Programınızın derleme hatası yoksa, adında `Hello.exe` bir yürütülebilir dosya oluşturulur.

5. Komut istemi penceresinde, programı çalıştırmak için aşağıdaki komutu girin:

     `Hello`

 C# Derleyici ve seçenekleri hakkında daha fazla bilgi için bkz [ C# . derleyici seçenekleri](../../language-reference/compiler-options/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Programı İçinde](./index.md)
- [Dizeler](../strings/index.md)
- [Örnekler ve öğreticiler](../../../samples-and-tutorials/index.md)
- [C#Başvurunun](../../language-reference/index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../main-and-command-args/index.md)
- [Visual C# ve Visual Basic'e Başlarken](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
