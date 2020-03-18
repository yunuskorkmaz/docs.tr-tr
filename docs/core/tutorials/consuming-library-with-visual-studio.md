---
title: Visual Studio’da bir .NET Standard kitaplığını kullanma
description: Visual Studio 2019 ile başka bir sınıf kitaplığı üyelerini çağıran bir .NET Core uygulaması oluşturun.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920450"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Visual Studio’da bir .NET Standard kitaplığını kullanma

Bir .NET Standart sınıf kitaplığı oluşturduktan, test ettikten ve kitaplığın sürüm sürümünü oluşturduktan sonra, bir sonraki adım arayanların kullanımına açmaktır. Bunu iki şekilde yapabilirsiniz:

- Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamada bir bileşense), bunu çözüme proje olarak ekleyebilirsiniz.
- Kitaplık herkese açık olacaksa, bunu NuGet paketi olarak dağıtabilirsiniz.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
>
> - Çözüme bir .NET Standart kitaplık projesine atıfta bulunulan bir konsol uygulaması ekleyin.
> - .NET Standart kitaplık projesi içeren bir NuGet paketi oluşturun.

## <a name="add-a-console-app-to-your-solution"></a>Çözümünüze konsol uygulaması ekleme

[Visual Studio'daki Test a .NET Standart kitaplığında](testing-library-with-visual-studio.md)sınıf kitaplığınız ile aynı çözüme birim testleri eklediğiniz gibi, uygulamanızı da bu çözümün bir parçası olarak ekleyebilirsiniz. Örneğin, sınıf kitaplığınızı, kullanıcıdan bir dize girmesini gerektiren ve ilk karakterinin büyük harf olup olmadığını bildiren bir konsol uygulamasında kullanabilirsiniz:

1. Visual `ClassLibraryProjects` Studio makalesinde [Bir .NET Standart kitaplığı oluştur'da](library-with-visual-studio.md) oluşturduğunuz çözümü açın.

1. Çözüme "ShowCase" adlı yeni bir .NET Core konsol uygulaması ekleyin.

   1. **Solution Explorer'da** çözüme sağ tıklayın ve**Yeni proje** **Ekle'yi** > seçin.

   1. Yeni **proje** ekle sayfasında, arama kutusuna **konsolgirin.** Dil listesinden **C#** veya **Visual Basic'i** seçin ve ardından Platform listesindeki **tüm platformları** seçin. Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.

   1. Yeni **proje sayfanızı Yapılandır'da** Proje **adı** kutusuna **ShowCase'i** girin. Ardından **Oluştur'u**seçin.

1. **Solution**Explorer'da, **ShowCase** projesini sağ tıklatın ve bağlam menüsünde **Başlangıç Projesi olarak ayarla'yı** seçin.

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur. Sınıf kitaplığınızda yöntemleri aramasına izin vermek için sınıf kitaplığına bir başvuru oluşturursunuz. **Çözüm Gezgini'nde,** `ShowCase` projenin **Bağımlılıklar** düğümünü sağ tıklatın ve **Başvuru Ekle'yi**seçin.

   ![Visual Studio'da referans bağlam menüsü ekleme](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. Başvuru **Yöneticisi** iletişim kutusunda **StringLibrary'yi,** sınıf kitaplığı projenizi seçin ve **Tamam** düğmesini seçin.

   ![StringLibrary seçili Başvuru Yöneticisi iletişim kutusu](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. *Program.cs* veya *Program.vb* dosyasının kod penceresinde, kodun tümünün yerine aşağıdaki kod la değiştirin:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod, konsol `row` penceresine yazılan veri satırlarının sayısını korumak için değişkeni kullanır. 25'ten büyük veya eşit olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program, kullanıcıdan bir dize girmesini ister. Dize bir büyük harf karakteri ile başlayıp başlamadığını gösterir. Kullanıcı dize girmeden Enter tuşuna basarsa, uygulama biter ve konsol penceresi kapanır.

1. Gerekirse, projenin **Hata Ayıklama** yayınını derlemek `ShowCase` için araç çubuğunu değiştirin. **ShowCase** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.

   ![Hata Ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

[Visual Studio'yu kullanarak C# veya Visual Basic .NET Core Hello World uygulamanızı hata ayıklama](debugging-with-visual-studio.md) adımlarını izleyerek bu kitaplığı kullanan uygulamayı hata ayıklayabilir ve yayımlayabilir ve [.NET Core Hello World uygulamanızı Visual Studio ile](publishing-with-visual-studio.md)yayınlayabilirsiniz.

## <a name="create-a-nuget-package"></a>NuGet paketi oluşturma

Sınıf kitaplığınızı NuGet paketi olarak yayımlayarak yaygın olarak kullanılabilir hale getirebilirsiniz. Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez. Bir tane oluşturmak için .NET Core CLI komutlarını kullanmanız gerekir:

1. Konsol pencereyi açın.

   Örneğin, Windows görev çubuğundaki arama kutusuna **Komut İstemi** girin. Komut **İstem** masaüstü uygulamasını seçin veya arama sonuçlarında zaten seçiliyse **Enter** tuşuna basın.

1. Kitaplığınızın proje dizinine gidin. Dizin kaynak kodunuzu ve bir proje dosyası, *StringLibrary.csproj* veya *StringLibrary.vbproj*içerir.

1. *.nupkg* uzantılı bir paket oluşturmak için [dotnet paketi](../tools/dotnet-pack.md) komutunu çalıştırın:

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > *dotnet.exe* içeren dizin PATH'inizde değilse, konsol penceresine girerek `where dotnet.exe` konumunu bulabilirsiniz.

NuGet paketleri oluşturma hakkında daha fazla bilgi için [.NET Core CLI ile NuGet paketi nasıl oluşturulur.](../deploying/creating-nuget-packages.md)
