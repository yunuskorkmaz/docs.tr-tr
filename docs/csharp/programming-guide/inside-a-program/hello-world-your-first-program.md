---
title: Hello World -- Windows veya Mac'te Visual Studio'yu kullanan ilk programınız - C# Programlama Kılavuzu
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 910fa4af1b4e45ce627b589a06910dc168490047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712149"
---
# <a name="hello-world----your-first-program"></a>Hello World -- İlk programınız

Bu makalede, geleneksel "Hello World!" oluşturmak için Visual Studio'yu kullanacaksınız. Program. Visual Studio, .NET geliştirme için tasarlanmış birçok özelliğe sahip profesyonel bir Entegre Geliştirme Ortamıdır (IDE). Bu programı oluşturmak için Visual Studio'daki özelliklerden yalnızca birkaçını kullanırsınız. Visual Studio hakkında daha fazla bilgi edinmek için Visual [C# ile Başlarken'e](/visualstudio/ide/quickstart-csharp-console)bakın.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a>Yeni uygulama oluşturma

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Visual Studio’yu çalıştırın. Windows'da aşağıdaki resmi görürsünüz:

![Windows'da Visual Studio karşılama ekranı](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

Görüntünün sağ alt köşesinde **yeni bir proje oluştur'u** seçin. Visual Studio **Yeni Proje** iletişim kutusunu görüntüler:

![Windows'da Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> Visual Studio'yu ilk kez başlattıysanız, **Son proje şablonları** listesi boştur.

Yeni proje iletişim kutusunda "Console App (.NET Core)" seçeneğini belirleyin ve **ardından İleri**tuşuna basın. Projenize "HelloWorld" gibi bir ad verin ve **Oluştur'a**basın.

Visual Studio projenizi açar. Zaten temel bir "Merhaba Dünya!" Örnek. Projenizi çalıştırmak için basın. `Ctrl`  +  `F5` Visual Studio, kaynak kodu çalıştırılabilir e dönüştürerek projenizi oluşturur. Daha sonra, yeni uygulamanızı çalıştıran bir komut penceresi başlatıyor. Pencerede aşağıdaki metni görmeniz gerekir:

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

Pencereyi kapatmak için bir tuşa basın.

# <a name="macos"></a>[Macos](#tab/macos)

Mac için Visual Studio'u başlatın. Mac'te aşağıdaki resmi görürsünüz:

![Mac'te Visual Studio karşılama ekranı](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> Mac için Visual Studio'yu ilk kez başlattıysanız, **Son projeler** listesi boştur.

Görüntünün sağ üst köşesinde **Yeni'yi** seçin. Mac için Visual **Studio, Yeni Proje** iletişim kutusunu görüntüler:

![Mac Visual Studio yeni proje ekranı](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

Yeni proje iletişim kutusunda ".NET Core" ve "Console App" seçeneğini belirleyin ve **Ardından İleri**tuşuna basın. Hedef çerçeveyi seçmeniz gerekir. Varsayılan değer gayet iyi, bu yüzden bir sonrakine basın. Projenize "HelloWorld" gibi bir ad verin ve **Oluştur'a**basın. Varsayılan proje konumunu kullanabilirsiniz. Bu projeyi kaynak denetimine eklemeyin.

Mac için Visual Studio projenizi açar. Zaten temel bir "Merhaba Dünya!" Örnek. Projenizi çalıştırmak için basın. `Ctrl`  +  `Fn`  +  `F5` Mac için Visual Studio, kaynak kodu çalıştırılabilire dönüştürerek projenizi oluşturur. Daha sonra, yeni uygulamanızı çalıştıran bir komut penceresi başlatıyor. Pencerede aşağıdaki metni görmeniz gerekir:

```console
Hello World!

Press any key to close this window . . .
```

Oturumu sonlamak için bir tuşa basın.

---

## <a name="elements-of-a-c-program"></a>C# programının öğeleri

Bu programın önemli bölümlerini inceleyelim. İlk satır bir yorum içerir. Karakterler satırın geri kalanını yoruma `//` dönüştürür.

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

Ayrıca, bir metin bloğunu `/*` karakterlerle `*/` karakterler arasına ekleyerek yorum yapabilirsiniz. Bu, aşağıdaki örnekte gösterilir.

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

C# konsol uygulaması, `Main` denetimin başlayıp sona erdiği bir yöntem içermelidir. Yöntem, `Main` nesneleri oluşturduğunuz ve diğer yöntemleri yürüttüğüğün yerdir.

Yöntem, `Main` bir sınıf veya bir yapı içinde bulunan [statik](../../language-reference/keywords/static.md) bir yöntemdir. Önceki "Hello World!" örneğin, adlı `Hello`bir sınıfta bulunur. `Main` Yöntemi aşağıdaki yollardan biriyle bildirebilirsiniz:

- Geri dönebilir. `void` Bu, programınızın bir değer döndürmediği anlamına gelir.

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- Ayrıca bir sonda döndürebilir. Sonda, uygulamanızın **çıkış kodudur.**

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- İade türlerinden herhangi biriyle, bağımsız değişkenler alabilir.

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

-veya-

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

`Main` Yöntemin parametresi, `args`programı `string` çağırmak için kullanılan komut satırı bağımsız değişkenlerini içeren bir dizidir.

Komut satırı bağımsız değişkenleri nasıl kullanılacağı hakkında daha fazla bilgi için [Main() ve Command-Line Bağımsız](../main-and-command-args/index.md)Değişkenleri'ndeki örneklere bakın.

## <a name="input-and-output"></a>Girdi ve çıktı

C# programları genellikle .NET Framework'ün çalışma zamanı kitaplığı tarafından sağlanan giriş/çıktı hizmetlerini kullanır. İfade `System.Console.WriteLine("Hello World!");` yöntemini <xref:System.Console.WriteLine%2A> kullanır. Bu, çalışma zamanı kitaplığında <xref:System.Console> sınıfın çıktı yöntemlerinden biridir. Dize parametresini standart çıktı akışında yeni bir çizgi yle görüntüler. Farklı <xref:System.Console> giriş ve çıkış işlemleri için başka yöntemler de mevcuttur. Yönergeyi `using System;` programın başına eklerseniz, <xref:System> sınıfları ve yöntemleri tam olarak nitelemeden doğrudan kullanabilirsiniz. Örneğin, bunun yerine `Console.WriteLine` `System.Console.WriteLine`arayabilirsiniz:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Giriş/çıkış yöntemleri hakkında daha fazla <xref:System.IO>bilgi için bkz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Örnekler ve öğreticiler](../../../samples-and-tutorials/index.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../main-and-command-args/index.md)
- [Görsel C ile Başlarken #](/visualstudio/ide/quickstart-csharp-console)
