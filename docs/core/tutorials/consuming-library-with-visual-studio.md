---
title: Visual Studio’da bir .NET Standard kitaplığını kullanma
description: Visual Studio 2019 ile başka bir sınıf kitaplığının üyelerini çağıran bir .NET Core uygulaması oluşturun.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ec9c6f992bcd4a76e2f70018f3facca42b7b660c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714066"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Visual Studio’da bir .NET Standard kitaplığını kullanma

Bir .NET Standard sınıf kitaplığı oluşturduktan, sınadıktan ve kitaplığın bir yayın sürümünü oluşturduktan sonra, bir sonraki adım, çağıranlar için kullanılabilir hale gelir. Bunu iki şekilde yapabilirsiniz:

- Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamadaki bir bileşen ise) çözümünüze bir proje olarak dahil edebilirsiniz.
- Kitaplık herkese açık hale gelir, bir NuGet paketi olarak dağıtabilirsiniz.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Çözümünüze bir .NET Standard kitaplığı projesine başvuran bir konsol uygulaması ekleyin.
> - .NET Standard kitaplığı projesi içeren bir NuGet paketi oluşturun.

## <a name="add-a-console-app-to-your-solution"></a>Çözümünüze bir konsol uygulaması ekleme

Birim testlerini, [Visual Studio 'da bir .NET Standard kitaplığı test](testing-library-with-visual-studio.md)etme bölümünde yer alan sınıf kitaplısınız ile aynı çözümde bulundurmadığınız gibi, uygulamanızı bu çözümün bir parçası olarak dahil edebilirsiniz. Örneğin, sınıf kitaplığınızı, kullanıcıdan ilk karakterinin büyük harf olup olmadığını belirten bir dize ve rapor girmesini isteyen bir konsol uygulamasında kullanabilirsiniz:

1. [Visual Studio 'da bir .NET Standard kitaplığı oluşturun](library-with-visual-studio.md) makalesindeki oluşturduğunuz `ClassLibraryProjects` çözümünü açın.

1. Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.

   1. **Çözüm Gezgini** çözüme sağ tıklayın ve > **Yeni proje** **Ekle** ' yi seçin.

   1. **Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin. Dil **C#** listesinden seçin veya **Visual Basic** ve ardından platform listesinden **tüm platformlar** ' ı seçin. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   1. **Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin. Ardından **Oluştur**' u seçin.

1. **Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur. Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz. **Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. *Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

1. Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin. **Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

[Visual Studio 'yu kullanarak C# veya Visual Basic .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md) ve [.NET Core Merhaba Dünya uygulamanızı Visual Studio ile yayımlama](publishing-with-visual-studio.md)bölümündeki adımları izleyerek, bu kitaplığı kullanan uygulamayı ayıklayabilir ve yayımlayabilirsiniz.

## <a name="create-a-nuget-package"></a>NuGet paketi oluşturma

Sınıf kitaplığınızı, bir NuGet paketi olarak yayımlayarak geniş oranda kullanılabilir hale getirebilirsiniz. Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez. Bir tane oluşturmak için .NET Core CLI komutlarını kullanmanız gerekir:

1. Bir konsol penceresi açın.

   Örneğin, Windows görev çubuğundaki arama kutusuna **komut istemi** yazın. **Komut istemi** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **ENTER** tuşuna basın.

1. Kitaplığınızın proje dizinine gidin. Dizin, kaynak kodunuzu ve *StringLibrary. csproj* veya *StringLibrary. vbproj*proje dosyasını içerir.

1. *. Nupkg* uzantılı bir paket oluşturmak için [DotNet Pack](../tools/dotnet-pack.md) komutunu çalıştırın:

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > *DotNet. exe* IÇEREN Dizin yolunuzda değilse, konsol penceresine `where dotnet.exe` girerek konumunu bulabilirsiniz.

NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz. [platformlar arası araçlarla NuGet paketi oluşturma](../deploying/creating-nuget-packages.md).
