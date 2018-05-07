---
title: Hello World -- İlk Programınız (C# Programlama Kılavuzu)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 904657175d87e0d78e518248ed89b3720227360f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hello-world----your-first-program-c-programming-guide"></a>Hello World -- İlk Programınız (C# Programlama Kılavuzu)
Aşağıdaki yordam bir C# sürümünü geleneksel "Hello World!" oluşturur Program. Program dize görüntüler `Hello World!`  
  
 Giriş kavramları daha fazla örnekleri için bkz: [Visual C# ve Visual Basic ile çalışmaya başlama](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a>Bir konsol uygulaması oluşturmak ve çalıştırmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Menü çubuğunda seçin **dosya**, **yeni**, **proje**.  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  Genişletme **yüklü**, genişletin **şablonları**, genişletin **Visual C#** ve ardından **konsol uygulaması**.  
  
4.  İçinde **adı** kutusunda projeniz için bir ad belirtin ve ardından **Tamam** düğmesi.  
  
     Yeni Proje görünür **Çözüm Gezgini**.  
  
5.  Program.cs içinde açık değilse **Kod düzenleyicisinde**, kısayol menüsünü açın **Program.cs** içinde **Çözüm Gezgini**ve ardından **görünümü kodu**.  
  
6.  Program.cs içeriğini aşağıdaki kodla değiştirin.  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Projeyi çalıştırmak için F5 tuşuna seçin. Bir çizgi içeren bir komut istemi penceresi görüntülenir `Hello World!`  
  
 Ardından, bu program önemli kısımlarını incelenir.  
  
## <a name="comments"></a>Açıklamalar  
 İlk satır yorum içerir. Karakterleri `//` açıklama satırı kalan Dönüştür.  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Bir metin bloğunu arasında kapsayan tarafından da yorum yapabileceği `/*` ve `*/` karakter. Bu, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a>Ana Yöntem  
 Bir C# konsol uygulaması içermesi gereken bir `Main` denetim başlar ve biter yöntemi. `Main` Yöntemdir burada nesneleri oluşturmak ve diğer bir yöntem yürütülemez.  
  
 `Main` Yöntemi bir [statik](../../../csharp/language-reference/keywords/static.md) bir sınıf veya yapı içinde bulunduğu yöntemi. Önceki "Hello World!" Örneğin, adlı bir sınıf içinde bulunduğu `Hello`. Bildirebilirsiniz `Main` aşağıdaki yollardan biriyle yöntemi:  
  
-   Geri dönebilirsiniz `void`.  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Ayrıca bir tamsayı geri dönebilirsiniz.  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Dönüş türleri birini kullanarak, bağımsız değişkenleri alabilir.  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     -veya-  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Parametresi, `Main` yöntemi, `args`, olan bir `string` program çağırmak için kullanılan komut satırı bağımsız değişkenleri içeren bir dizi. Aksine C++'da, dizi yürütülebilir (exe) dosyasının adı içermez.  
  
 Örneklerde komut satırı bağımsız değişkenleri kullanma hakkında daha fazla bilgi için bkz: [ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md) ve [nasıl yapılır: oluşturma ve kullanma derlemeler kullanma komut satırı](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
 Çağrı <xref:System.Console.ReadKey%2A> sonunda `Main` yöntemi, F5 tuşuna basarak programınızı hata ayıklama modunda çalıştırdığınızda, çıktı okuma fırsatına sahip önce kapatma konsol penceresi önler.  
  
## <a name="input-and-output"></a>Girdi ve Çıktı  
 C# programları genellikle .NET Framework çalışma zamanı kitaplığı tarafından sağlanan giriş/çıkış Hizmetleri kullanın. Deyim `System.Console.WriteLine("Hello World!");` kullanan <xref:System.Console.WriteLine%2A> yöntemi. Çıktı yöntemlerinden birini budur <xref:System.Console> Çalışma Zamanı Kitaplığı'nda sınıfı. Yeni bir satırla tarafından izlenen standart çıktı akışı, dize parametresinin görüntüler. Diğer <xref:System.Console> yöntemleri farklı bir giriş ve çıkış işlemleri için kullanılabilir. Dahil ederseniz `using System;` yönerge program başında doğrudan kullanabileceğiniz <xref:System> sınıflar ve yöntemler tam olarak niteleme olmadan. Örneğin, çağırabilirsiniz `Console.WriteLine` yerine `System.Console.WriteLine`:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Giriş/Çıkış yöntemleri hakkında daha fazla bilgi için bkz: <xref:System.IO>.  
  
## <a name="command-line-compilation-and-execution"></a>Komut Satırı Derlemesi ve Yürütme  
 "Hello World!" derleme Visual Studio tümleşik geliştirme ortamı (IDE yerine) komut satırını kullanarak programı.  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a>Derlemek ve bir komut satırından çalıştırmak için  
  
1.  Yukarıdaki yordamı koddan bir metin düzenleyicisine yapıştırın ve dosyayı bir metin dosyası olarak kaydedin. Dosya adı `Hello.cs`. C# kaynak kodu dosyaları kullanmak uzantısı `.cs`.  
  
2.  Bir komut istemi penceresi açmak için aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Windows 10 ' daki üzerinde **Başlat** menüsü, arama `Developer Command Prompt`ve ardından dokunun veya seçin **VS 2017 için geliştirici komut istemi**.  
  
         Bir geliştirici komut istemi penceresi görüntülenir.  
  
    -   Windows 7'de açmak **Başlat** menüsü, Visual Studio'nun geçerli sürümü için klasörü genişletin, kısayol menüsünü açın **Visual Studio Araçları**ve ardından **Geliştirici komut istemi VS 2017 için**.  
  
         Bir geliştirici komut istemi penceresi görüntülenir.  
  
    -   Standart bir komut istemi penceresinden komut satırı derlemeleri etkinleştirin.  
  
         Bkz: [nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  Komut İstemi penceresinde içeren klasöre gidin, `Hello.cs` dosya.  
  
4.  Derlemek için aşağıdaki komutu girin `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Programınızı adlı bir yürütülebilir dosya hiç derleme hatası olup olmadığını `Hello.exe` oluşturulur.  
  
5.  Komut İstemi penceresinde programı çalıştırmak için aşağıdaki komutu girin:  
  
     `Hello`  
  
 C# Derleyici ve seçenekleri hakkında daha fazla bilgi için bkz: [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md).
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Programı İçinde](../../../csharp/programming-guide/inside-a-program/index.md)  
 [Dizeler](../../../csharp/programming-guide/strings/index.md)  
 [\<paveover > C# örnek uygulamaları](http://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Visual C# ve Visual Basic'e Başlarken](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
