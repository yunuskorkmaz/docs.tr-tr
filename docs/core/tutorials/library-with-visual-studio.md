---
title: Visual Studio 'da .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005297"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a>Öğretici: Visual Studio 'da .NET Standard kitaplığı oluşturma

Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar. .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir. Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.

> [!NOTE]
> .NET Standard sürümlerinin ve destekledikleri platformların listesi için bkz. [.NET Standard](../../standard/net-standard.md).

Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız. Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .

## <a name="prerequisites"></a>Ön koşullar

- **.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) . .NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.

  Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.

## <a name="create-a-visual-studio-solution"></a>Visual Studio çözümü oluşturma

' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın. Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür. Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.

Boş çözümü oluşturmak için:

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin. **Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin. Ardından **Oluştur**’u seçin.

## <a name="create-a-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

1. Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın. Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın. Ardından **Oluştur**' u seçin.

1. Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun. **Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin. **Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

   Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur. Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .

1. *Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin. Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` . Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür. Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.

1. **Build**  >  Projenin hatasız derlendiğinden emin olmak için menü çubuğunda, derleme**çözümü** oluştur ' u seçin.

## <a name="add-a-console-app-to-the-solution"></a>Çözüme bir konsol uygulaması ekleme

Bir konsol uygulamasında sınıf kitaplığını kullanarak, dizenin büyük harfli bir karakterle başlayıp başlamamadığını bir dize ve rapor girmesini ister.

1. Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin. Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.

   1. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin. Ardından **Oluştur**’u seçin.

1. **Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez. Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun. **Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](media/library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](media/library-with-visual-studio/manage-project-references.png)

1. *Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

1. Gerekirse, projenin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin `ShowCase` . **Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. Dizeleri girerek ve **ENTER**'a basarak programı deneyin ve çıkmak için **ENTER** tuşuna basın.

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik. Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.

> [!div class="nextstepaction"]
> [Visual Studio 'da .NET Core ile .NET Standard kitaplığı test etme](testing-library-with-visual-studio.md)
