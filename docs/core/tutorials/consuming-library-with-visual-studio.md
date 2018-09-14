---
title: Visual Studio 2017'de bir .NET Standard kitaplığı kullanma
description: Visual Studio 2017 ile bir sınıf kitaplığı'nda üyeleri çağırma hakkında bilgi edinin.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52ec46c23bb928b49f034270ed1d510d1acf992e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518171"
---
# <a name="consuming-a-net-standard-library-in-visual-studio-2017"></a>Visual Studio 2017'de bir .NET Standard kitaplığı kullanma

İçindeki adımları izleyerek bir .NET Standard sınıf kitaplığı oluşturduktan sonra [bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [Visual Studio 2017'de .NET Core ile bir Visual Basic sınıf kitaplığı oluşturma ](vb-library-with-visual-studio.md), içinde test [Visual Studio 2017'de .NET Core ile bir sınıf kitaplığını test](testing-library-with-visual-studio.md), ve kitaplığı sürümü oluşturulan arayanlar için kullanılabilir hale getirmek için sonraki adım içerir. Bunu iki şekilde yapabilirsiniz:

* (Örneğin, bir tek büyük bir uygulama bileşeni ise) tek bir çözüm tarafından kullanılacak kitaplık, çözümünüze bir proje olarak içerebilir.

* Kitaplığa Genel olarak erişilebilir olacaksa, bir NuGet paketi olarak dağıtabilirsiniz.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Bir çözümde bir proje olarak kitaplığı dahil olmak üzere

Sınıf kitaplığınıza aynı çözümde birim testlerini dahil olarak, uygulamanızı bu çözümün parçası olarak dahil edebilirsiniz. Örneğin, bir dize ve raporları, ilk karakterin büyük harf olup olmadığını girmesini isteyen bir konsol uygulamasında, sınıf kitaplığı kullanabilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) konu. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm ve select **Ekle** > **yeni proje** gelen bağlam menüsü.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual C#** düğümünü seçip alt **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** Proje şablonu. İçinde **adı** metin kutusuna "Gösterimi" yazın ve seçin **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu Ekle](./media/consuming-library-with-visual-studio/addnewproject.png)

1. İçinde **Çözüm Gezgini**, sağ **gösterimi** seçin ve proje **başlangıç projesi olarak ayarla** bağlam menüsünde. 

   ![ShowCase bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Başlangıçta, projenize Sınıf Kitaplığı'na erişimi yok. Sınıf kitaplığınıza yöntemlerini çağırmaya izin vermek için bir başvuru sınıf kitaplığı oluşturun. İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümünü seçip alt **Başvuru Ekle**.

   ![ShowCase bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı projesi ve seçin **Tamam** düğmesi.

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Kod penceresinde *Program.cs* dosya, tüm kodu aşağıdaki kodla değiştirin:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod `row` konsol penceresine yazılan veri satırı sayısını korumak için değişkeni. Büyüktür veya eşittir 25 olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program bir dize girmesini ister. Dizeyi büyük harfli bir karakterle başlayıp başlamadığını gösterir. Kullanıcı, bir dize girmeden Enter tuşuna bastığında, uygulama sonlandırır ve konsol penceresini kapatır.

1. Gerekirse, derleme için araç çubuğunda değiştirin **hata ayıklama** sürüm `ShowCase` proje. Derleme ve yeşil bir ok seçerek programı çalıştırın **gösterimi** düğmesi.

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir sınıf kitaplığı Visual Basic ve Visual Studio 2017'de .NET Core ile oluşturmaya](vb-library-with-visual-studio.md) konu. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözüm ve select **Ekle** > **yeni proje** gelen bağlam menüsü.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda genişletin **Visual Basic** düğümünü seçip alt **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusuna "Gösterimi" yazın ve seçin **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu Ekle](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. İçinde **Çözüm Gezgini**, sağ **gösterimi** seçin ve proje **başlangıç projesi olarak ayarla** bağlam menüsünde. 

   ![ShowCase bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Başlangıçta, projenize Sınıf Kitaplığı'na erişimi yok. Sınıf kitaplığınıza yöntemlerini çağırmaya izin vermek için bir başvuru sınıf kitaplığı oluşturun. İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümünü seçip alt **Başvuru Ekle**.

   ![ShowCase bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı projesi ve seçin **Tamam** düğmesi.

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Kod penceresinde *Program.vb* dosya, tüm kodu aşağıdaki kodla değiştirin:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod `row` konsol penceresine yazılan veri satırı sayısını korumak için değişkeni. Büyüktür veya eşittir 25 olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.

   Program bir dize girmesini ister. Dizeyi büyük harfli bir karakterle başlayıp başlamadığını gösterir. Kullanıcı, bir dize girmeden Enter tuşuna bastığında, uygulama sonlandırır ve konsol penceresini kapatır.

1. Gerekirse, derleme için araç çubuğunda değiştirin **hata ayıklama** sürüm `ShowCase` proje. Derleme ve yeşil bir ok seçerek programı çalıştırın **gösterimi** düğmesi.

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
---

Hata ayıklama ve yayımlama adımları izleyerek bu kitaplığı kullanan uygulama [Merhaba Dünya uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md) ve [Hello World uygulamanızı Visual Studio ile yayımlama 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Bir NuGet paketi kitaplıkta dağıtma

Bir NuGet paketi olarak yayımlayarak, sınıf kitaplığı yaygın olarak kullanılabilir hale getirebilirsiniz. Visual Studio, NuGet paketlerini oluşturulmasını desteklemiyor. Oluşturmak için kullandığınız [ `dotnet` komut satırı yardımcı programını](../../core/tools/dotnet.md):

1. Bir konsol penceresi açın. Örneğin **bana istediğini Sorabilirsin** metin kutusunda Windows görev çubuğunda, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açıyor **komut istemi** masaüstü uygulaması veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.

1. Kitaplığınızın proje dizinine gidin. Tipik dosya konumunu yeniden sürece, konusu *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* dizin. Kaynak kodunuzu ve bir proje dosyası dizini içeriyor *StringLibrary.csproj*.

1. Komutu Yürüt `dotnet pack --no-build`. `dotnet` Yardımcı olan bir paket oluşturur bir *.nupkg* uzantısı.

   > [!TIP]
   > Dizin, içerip içermediğini *dotnet.exe* olduğu değil, yolu girerek konumunda bulabilirsiniz `where dotnet.exe` konsol penceresinde.

NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz: [Çapraz Platform araçları ile bir NuGet paketi oluşturma](../../core/deploying/creating-nuget-packages.md).
