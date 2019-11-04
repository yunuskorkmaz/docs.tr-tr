---
title: Visual Studio 2017’de bir .NET Standard kitaplığı kullanma
description: Visual Studio 2017 ile başka bir sınıf kitaplığının üyelerini çağıran bir .NET Core uygulaması oluşturun.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cfceb7ba384a28a09f172032f6edb6f5e495e9c0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420909"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a>Visual Studio 2017’de bir .NET Standard kitaplığı kullanma

[Visual studio 2017 ' de .NET Core ile bir C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [Visual Studio 2017 ' de .NET Core ile bir Visual Basic sınıf kitaplığı](vb-library-with-visual-studio.md)oluşturma bölümündeki adımları izleyerek bir .NET Standard sınıf kitaplığı oluşturduktan sonra, bu, içinde [test edilmiştir Visual Studio 2017 ' de .NET Core ile bir sınıf kitaplığını test etme](testing-library-with-visual-studio.md)ve kitaplığın yayın sürümü oluşturma bir sonraki adım, arayanlara hazır hale getirmek için kullanılır. Bunu iki şekilde yapabilirsiniz:

* Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamadaki bir bileşen ise) çözümünüze bir proje olarak dahil edebilirsiniz.

* Kitaplığın genel olarak erişilebilir olacağı bir NuGet paketi olarak dağıtabilirsiniz.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Bir kitaplığı bir çözüme proje olarak dahil etme

Birim testlerini, sınıf kitaplısınız ile aynı çözümde bulundurmadığınız gibi, uygulamanızı bu çözümün bir parçası olarak dahil edebilirsiniz. Örneğin, sınıf kitaplığınızı, kullanıcıdan ilk karakterinin büyük harf olup olmadığını belirten bir dize ve rapor girmesini isteyen bir konsol uygulamasında kullanabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. [Visual Studio 'da .NET Core ile bir C# sınıf kitaplığı oluşturma 2017](./library-with-visual-studio.md) konusunun oluşturduğunuz `ClassLibraryProjects` çözümünü açın. **Çözüm Gezgini**, **classlibraryprojects** çözümüne sağ tıklayın ve bağlam menüsünden **Yeni > proje** **Ekle** ' yi seçin.

1. **Yeni Proje Ekle** iletişim kutusunda, **görsel C#**  düğümünü genişletin ve ardından **konsol uygulaması (.NET Core)** proje şablonu tarafından izlenen **.NET Core** düğümünü seçin. **Ad** metin kutusuna "gösterimi" yazın ve **Tamam** düğmesini seçin.

   ![Visual Studio yeni proje Ekle iletişim kutusu-C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. **Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.

   ![Başlangıç projesini ayarlamaya yönelik Visual Studio proje bağlam menüsü-C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur. Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz. **Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

   ![Visual Studio proje başvuru ekleme bağlam menüsü-C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.

   ![Visual Studio başvuruları Yönet iletişim kutusu-C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. *Program.cs* dosyası için kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

1. Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin. **Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu-C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. [Visual Studio 'da Visual Basic ve .NET Core ile bir sınıf kitaplığı oluşturma 2017](vb-library-with-visual-studio.md) konusunun oluşturduğunuz `ClassLibraryProjects` çözümünü açın. **Çözüm Gezgini**, **classlibraryprojects** çözümüne sağ tıklayın ve bağlam menüsünden **Yeni > proje** **Ekle** ' yi seçin.

1. **Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü genişletin ve ardından **konsol uygulaması (.NET Core)** proje şablonu tarafından izlenen **.NET Core** düğümünü seçin. **Ad** metin kutusuna "gösterimi" yazın ve **Tamam** düğmesini seçin.

   ![Visual Studio yeni proje Ekle iletişim kutusu-Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. **Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin. 

   ![Başlangıç projesini ayarlamaya yönelik Visual Studio proje bağlam menüsü-Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur. Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz. **Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

   ![Visual Studio proje başvuru ekleme bağlam menüsü-Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. **Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.

   ![Visual Studio başvuruları Yönet iletişim kutusu-Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. *Program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır. 25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program kullanıcıdan bir dize girmesini ister. Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir. Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.

1. Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin. **Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.

   ![Araç çubuğunda Hata Ayıkla-Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

[Visual studio 2017 ile Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md) ve [Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama](publishing-with-visual-studio.md)bölümündeki adımları izleyerek, bu kitaplığı kullanan uygulamayı ayıklayabilir ve yayımlayabilirsiniz.

## <a name="distributing-the-library-in-a-nuget-package"></a>Kitaplığı bir NuGet paketinde dağıtma

Sınıf kitaplığınızı, bir NuGet paketi olarak yayımlayarak geniş oranda kullanılabilir hale getirebilirsiniz. Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez. Bir tane oluşturmak için [`dotnet` komut satırı yardımcı programını](../tools/dotnet.md)kullanın:

1. Bir konsol penceresi açın. Örneğin, Windows görev çubuğundaki bir **şeyi bana sor** metin kutusunda `Command Prompt` (veya short için `cmd`) girin ve **komut istemi** masaüstü uygulamasını seçerek veya arama sonuçlarında seçiliyse ENTER tuşuna basarak bir konsol penceresi açın.

1. Kitaplığınızın proje dizinine gidin. Normal dosya konumunu yeniden yapılandırmadığınız takdirde, bu, bu,, bu,, bu,, bu,, bu, The *Studio 2017 \ projeleri* Dizin, kaynak kodunuzu ve *StringLibrary. csproj*proje dosyasını içerir.

1. Komutu `dotnet pack --no-build`verin. `dotnet` yardımcı programı, *. nupkg* uzantılı bir paket oluşturur.

   > [!TIP]
   > *DotNet. exe* IÇEREN Dizin yolunuzda değilse, konsol penceresine `where dotnet.exe` girerek konumunu bulabilirsiniz.

NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz. [platformlar arası araçlarla NuGet paketi oluşturma](../deploying/creating-nuget-packages.md).
