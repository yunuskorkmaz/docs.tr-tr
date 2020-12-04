---
title: Visual Studio kullanarak .NET sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 6a3f61525ca86afc9ee71d56cbc9450862760ba4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599518"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a>Öğretici: Visual Studio kullanarak .NET sınıf kitaplığı oluşturma

Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir sınıf kitaplığı oluşturacaksınız.

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir. Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir. Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.

Bir sınıf kitaplığı oluşturduğunuzda, bir NuGet paketi olarak veya onu kullanan uygulamayla paketlenmiş bir bileşen olarak dağıtabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,8 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . .NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir. Bu öğreticide, [Visual Studio kullanarak .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde gösterildiği gibi, **Yeni projede tüm .NET Core şablonlarını göster** seçeneğini etkinleştirdiğiniz varsayılmaktadır.

## <a name="create-a-solution"></a>Çözüm oluşturma

' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın. Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür. Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.

Boş çözümü oluşturmak için:

1. Visual Studio’yu çalıştırın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin. **Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio 'da boş çözüm şablonu":::

4. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin. Ardından **Oluştur**’u seçin.

## <a name="create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

1. Çözüme "StringLibrary" adlı yeni bir .NET sınıf kitaplığı projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje** Ekle ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın. Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Sınıf kitaplığı** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** girin ve ardından **İleri**' yi seçin.

   1. **Ek bilgi** sayfasında **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.

1. Kitaplığın doğru .NET sürümünü hedeflediğinden emin olun. **Çözüm Gezgini** kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin. **Hedef Framework** metin kutusu, projenin .NET 5,0 ' i hedeflediğini gösterir.

1. Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="Sınıf kitaplığı için proje özellikleri":::

   Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur. Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .

1. *Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin. Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` . Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.

   `StartsWithUpper` , sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulanır <xref:System.String> .

1. Projenin hatasız derlendiğinden emin olmak için, menü çubuğunda yapı çözümü **Oluştur**' u seçin  >  **Build Solution** veya <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>B</kbd> ' ye basın.

## <a name="add-a-console-app-to-the-solution"></a>Çözüme bir konsol uygulaması ekleme

Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin. Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.

1. Çözüme "gösterimi" adlı yeni bir .NET konsol uygulaması ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje** Ekle ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin. Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.

   1. **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin. Ardından **İleri**' yi seçin.

   1. **Ek bilgiler** sayfasında, **hedef çerçeve** kutusunda **.NET 5,0 (geçerli)** seçeneğini belirleyin. Ardından **Oluştur**’u seçin.

1. *Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez. Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.

1. **Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Visual Studio 'da başvuru bağlam menüsü Ekle":::

1. **Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu":::

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. **Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü":::

1. <kbd>Ctrl</kbd> + Hata ayıklama olmadan programı derlemek ve çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu":::

1. Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="additional-resources"></a>Ek kaynaklar

* [.NET CLı ile Kitaplıklar geliştirme](libraries.md)
* [.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir sınıf kitaplığı oluşturdunuz. Sonraki öğreticide, sınıf kitaplığını birim testi ile öğrenin.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak .NET sınıf kitaplığı ile birim testi](testing-library-with-visual-studio.md)

Ya da otomatik birim testlerini atlayabilir ve bir NuGet paketi oluşturarak kitaplığı nasıl paylaşacağınızı öğrenebilirsiniz:

> [!div class="nextstepaction"]
> [Visual Studio kullanarak paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

Ya da bir konsol uygulamasını yayımlamayı öğrenin. Konsol uygulamasını, bu öğreticide oluşturduğunuz çözümden yayımlarsanız, sınıf kitaplığı bir *. dll* dosyası olarak onunla birlikte görüntülenir.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak bir .NET konsol uygulaması yayımlama](publishing-with-visual-studio.md)
