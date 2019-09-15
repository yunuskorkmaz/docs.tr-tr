---
title: Merhaba Dünya--Windows veya Mac 'te Visual Studio 'Yu kullanan ilk programınız- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 0807e46d36a4cf031bc44ae0dc4efab79dd51d03
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991337"
---
# <a name="hello-world----your-first-program"></a>Merhaba Dünya--ilk programınız

Bu makalede, geleneksel "Merhaba Dünya!" öğesini oluşturmak için Visual Studio 'Yu kullanacaksınız programda. Visual Studio, .NET geliştirmesi için tasarlanan çok sayıda özelliği olan profesyonel tümleşik bir geliştirme ortamıdır (IDE). Bu programı oluşturmak için Visual Studio 'daki özelliklerden yalnızca birkaçını kullanacaksınız. Visual Studio hakkında daha fazla bilgi edinmek için bkz. [Visual C# ve Visual Basic kullanmaya](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)başlama.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Yeni bir uygulama oluşturun

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

Visual Studio’yu çalıştırın. Windows 'da aşağıdaki görüntüyü görürsünüz:

![Windows 'da Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Görüntünün sağ alt köşesinde **Yeni proje oluştur** ' u seçin. Visual Studio **Yeni proje** iletişim kutusunu görüntüler:

![Windows 'da Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Visual Studio 'Yu ilk kez başlattıysanız, **son kullanılan proje şablonları** listesi boştur.

Yeni proje iletişim kutusunda, "konsol uygulaması (.NET Core)" öğesini seçin ve ardından **İleri**' ye basın. Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın.

Visual Studio, projenizi açar. Zaten temel bir "Merhaba Dünya!" örneğinde. Projenizi `Ctrl` çalıştırmak için tuşuna basın  +  `F5` . Visual Studio, projenizi oluşturup kaynak kodu yürütülebilir dosyaya dönüştürür. Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır. Pencerede aşağıdaki metni görmeniz gerekir:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Pencereyi kapatmak için bir tuşa basın.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Mac için Visual Studio başlatın. Mac üzerinde aşağıdaki görüntüyü görürsünüz:

![Mac üzerinde Visual Studio hoş geldiniz ekranı](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Mac için Visual Studio ilk kez başladıysanız, **son projeler** listesi boştur.

Görüntünün sağ üst köşesindeki **Yeni** ' yi seçin. **Yeni proje** iletişim kutusunu Mac için Visual Studio görüntüler:

![Mac 'te Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

Yeni proje iletişim kutusunda ".NET Core" ve "konsol uygulaması" ' nı seçin ve ardından **İleri**' ye basın. Hedef Framework 'ü seçmeniz gerekir. Varsayılan değer iyidir, bu nedenle ileri ' ye basın. Projenize "HelloWorld" gibi bir ad verin ve ardından **Oluştur**' a basın. Varsayılan proje konumunu kullanabilirsiniz. Bu projeyi kaynak denetimine eklemeyin.

Mac için Visual Studio projenizi açar. Zaten temel bir "Merhaba Dünya!" örneğinde. Projenizi `Ctrl` çalıştırmak için tuşuna basın.  +  `Fn`  +  `F5` Mac için Visual Studio, projenizi derleme ve kaynak kodu çalıştırılabilir dosyaya dönüştürme. Ardından, yeni uygulamanızı çalıştıran bir komut penceresi başlatır. Pencerede aşağıdaki metni görmeniz gerekir:

```console
Hello World!

Press any key to close this window . . .
```

Oturumu sonlandırmak için bir tuşa basın.

---

## <a name="elements-of-a-c-program"></a>Bir C# programın öğeleri

Bu programın önemli kısımlarını inceleyelim. İlk satır bir açıklama içerir. Karakterler `//` satırın geri kalanını açıklamaya dönüştürür.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Ayrıca, bir metin bloğunu, `/*` ve `*/` karakterleri arasına ekleyerek açıklama ekleyebilirsiniz. Bu, aşağıdaki örnekte gösterilir.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

C# Konsol uygulaması, denetimin başladığı ve `Main` bittiği bir yöntemi içermelidir. `Main` Yöntemi nesne oluşturduğunuz ve diğer yöntemleri yürütebileceğiniz yerdir.

Yöntemi, bir sınıf veya yapı içinde bulunan statik bir yöntemdir. [](../../language-reference/keywords/static.md) `Main` Önceki "Merhaba Dünya!" örnek, adlı `Hello`bir sınıfta bulunur. `Main` Yöntemi aşağıdaki yöntemlerden biriyle bildirebilirsiniz:

- Bu, döndürebilir `void`. Bu, programınızın bir değer döndürmeyeceği anlamına gelir.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Ayrıca, bir tamsayı döndürebilir. Tamsayı, uygulamanız için **Çıkış kodudur** .

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- Dönüş türlerinden biri ile bağımsız değişken alabilir.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-veya-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

Yönteminin parametresi, programı çağırmak için kullanılan komut satırı `string` bağımsız değişkenlerini içeren bir dizidir. `args` `Main`

Komut satırı bağımsız değişkenlerinin nasıl kullanılacağı hakkında daha fazla bilgi için, [ana () ve komut satırı bağımsız değişkenlerinde](../main-and-command-args/index.md)örneklere bakın.

## <a name="input-and-output"></a>Girdi ve çıktı

C#programlar genellikle .NET Framework çalışma zamanı kitaplığı tarafından sunulan giriş/çıkış hizmetlerini kullanır. İfade `System.Console.WriteLine("Hello World!");` yöntemini<xref:System.Console.WriteLine%2A> kullanır. Bu, çalışma zamanı kitaplığındaki <xref:System.Console> sınıfının çıkış yöntemlerinden biridir. Dize parametresini standart çıkış akışında ve ardından yeni bir satırla görüntüler. Farklı <xref:System.Console> giriş ve çıkış işlemleri için diğer yöntemler kullanılabilir. Programın başına `using System;` yönergesini eklerseniz, <xref:System> sınıfları ve yöntemleri tamamen nitelemeden doğrudan kullanabilirsiniz. Örneğin, `Console.WriteLine` `System.Console.WriteLine`yerine şunu çağırabilirsiniz:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Giriş/çıkış yöntemleri hakkında daha fazla bilgi için bkz <xref:System.IO>.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Örnekler ve öğreticiler](../../../samples-and-tutorials/index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../main-and-command-args/index.md)
- [Visual C# ve Visual Basic'e Başlarken](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
