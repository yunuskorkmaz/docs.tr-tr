---
title: Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı kullanma
description: Visual Studio 2017 ile bir sınıf kitaplığı'nda üyeleri çağrı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.openlocfilehash: 0a7002f2a5dba5a5aad32a83a43a933cd2cc5722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a>Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı kullanma

Bir sınıf kitaplığı'ndaki adımları izleyerek oluşturduktan sonra [bir Visual Studio 2017 .NET çekirdek ile C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [bir Visual Basic sınıf kitaplığı ile Visual Studio 2017 .NET çekirdek oluşturma](vb-library-with-visual-studio.md), içinde test [Visual Studio 2017 içinde bir sınıf kitaplığı .NET Core ile test](testing-library-with-visual-studio.md), ve bir kitaplık sürümü oluşturulmuş, sonraki adıma arayanlara kullanılabilir hale getirmek için. Bunu iki şekilde yapabilirsiniz:

* (Örneğin, bir bileşenin tek bir büyük uygulama ise) tek bir çözüm tarafından kullanılacak kitaplık, çözümünüz içinde bir proje olarak ekleyebilirsiniz.

* Kitaplık genellikle erişilemese, bir NuGet paketi olarak dağıtabilirsiniz.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Bir kitaplık bir çözümdeki bir proje ile dahil olmak üzere

Sınıf kitaplığı olarak aynı çözümde birim testleri dahil gibi uygulamanız bu çözümün parçası olarak dahil edebilirsiniz. Örneğin, sınıf kitaplığınızda ilk karakter büyük olup bir dize ve raporları girmesini ister bir konsol uygulaması kullanarak şunları yapabilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Açık `ClassLibraryProjects` oluşturduğunuz çözüm [bir Visual Studio 2017 .NET çekirdek ile C# sınıf kitaplığı oluşturmak](./library-with-visual-studio.md) konu. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözümü ve select **Ekle** > **yeni proje** gelen bağlam menüsü.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual C#** düğümü ve select **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** Proje şablonu. İçinde **adı** metin kutusu, "Gösterimi" yazın ve seçin **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu ekleme](./media/consuming-library-with-visual-studio/addnewproject.png)

1. İçinde **Çözüm Gezgini**, sağ **gösterimi** proje ve seçin **başlangıç projesi olarak ayarla** bağlam menüsünde. 

   ![Gösterimi bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Başlangıçta, projenizin Sınıf Kitaplığı'na erişimi yok. Sınıf Kitaplığı'nda yöntemlerini çağırmaya izin vermek için sınıf kitaplığına bir başvuru oluşturun. İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümü ve select **Başvuru Ekle**.

   ![Gösterimi bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı proje ve seçin **Tamam** düğmesi.

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Kod penceresinde *Program.cs* dosya, tüm kodu aşağıdaki kodla değiştirin:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod kullanan [Console.WindowHeight](xref:System.Console.WindowHeight) konsol penceresinde satır sayısını belirlemek için özelliği. Her [Console.CursorTop](xref:System.Console.CursorTop) özelliği büyüktür veya konsol penceresi satır sayısına eşit, kod konsol penceresini temizler ve kullanıcı için bir ileti görüntülenir.

   Program kullanıcının bir dize girmesini ister. Bu dize bir büyük harf karakter ile başlayıp başlamadığını gösterir. Kullanıcı, bir dize girmeden Enter tuşuna basarsa, uygulama sonlandırır ve konsol penceresi kapanır.

1. Gerekirse, derleme için araç çubuğunda değiştirmek **hata ayıklama** sürümü, `ShowCase` projesi. Derleme ve üzerinde yeşil ok seçerek program çalıştırma **gösterimi** düğmesi.

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
1. Açık `ClassLibraryProjects` oluşturduğunuz çözüm [sınıfı Visual Basic ve Visual Studio 2017 .NET Core kitaplığı oluşturma](vb-library-with-visual-studio.md) konu. İçinde **Çözüm Gezgini**, sağ **ClassLibraryProjects** çözümü ve select **Ekle** > **yeni proje** gelen bağlam menüsü.

1. İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual Basic** düğümü ve select **.NET Core** düğümünü ve ardından **konsol uygulaması (.NET Core)** proje şablonu. İçinde **adı** metin kutusu, "Gösterimi" yazın ve seçin **Tamam** düğmesi.

   ![Yeni Proje iletişim kutusu ekleme](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. İçinde **Çözüm Gezgini**, sağ **gösterimi** proje ve seçin **başlangıç projesi olarak ayarla** bağlam menüsünde. 

   ![Gösterimi bağlam menüsü](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. Başlangıçta, projenizin Sınıf Kitaplığı'na erişimi yok. Sınıf Kitaplığı'nda yöntemlerini çağırmaya izin vermek için sınıf kitaplığına bir başvuru oluşturun. İçinde **Çözüm Gezgini**, sağ `ShowCase` projenin **bağımlılıkları** düğümü ve select **Başvuru Ekle**.

   ![Gösterimi bağımlılıkları bağlam menüsü](./media/consuming-library-with-visual-studio/addreference.png)

1. İçinde **başvuru Yöneticisi** iletişim kutusunda **StringLibrary**, sınıf kitaplığı proje ve seçin **Tamam** düğmesi.

   ![Başvuru Yöneticisi](./media/consuming-library-with-visual-studio/referencemanager.png)

1. Kod penceresinde *Program.vb* dosya, tüm kodu aşağıdaki kodla değiştirin:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod kullanan [Console.WindowHeight](xref:System.Console.WindowHeight) konsol penceresinde satır sayısını belirlemek için özelliği. Her [Console.CursorTop](xref:System.Console.CursorTop) özelliği büyüktür veya konsol penceresi satır sayısına eşit, kod konsol penceresini temizler ve kullanıcı için bir ileti görüntülenir.

   Program kullanıcının bir dize girmesini ister. Bu dize bir büyük harf karakter ile başlayıp başlamadığını gösterir. Kullanıcı, bir dize girmeden Enter tuşuna basarsa, uygulama sonlandırır ve konsol penceresi kapanır.

1. Gerekirse, derleme için araç çubuğunda değiştirmek **hata ayıklama** sürümü, `ShowCase` projesi. Derleme ve üzerinde yeşil ok seçerek program çalıştırma **gösterimi** düğmesi.

   ![Görüntü](./media/consuming-library-with-visual-studio/toolbar.png)
---

Hata ayıklama ve içindeki adımları izleyerek bu kitaplığı kullanan uygulama yayımlama [Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md) ve [Hello World uygulamanızı Visual Studio ile yayımlama 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Bir NuGet paketi kitaplıkta dağıtma

Bir NuGet paketi olarak yayımlayarak, sınıf kitaplığı yaygın olarak kullanılabilir hale getirebilirsiniz. Visual Studio NuGet paketlerini oluşturulmasını desteklemiyor. Oluşturmak için kullandığınız [ `dotnet` komut satırı yardımcı programı](../../core/tools/dotnet.md):

1. Bir konsol penceresi açın. Örneğin **herhangi bir şey sor** metin kutusunda Windows görev çubuğundaki, girin `Command Prompt` (veya `cmd` kısaca) ve seçerek bir konsol penceresi açın **komut istemi** masaüstü uygulaması veya arama sonuçlarında seçtiyseniz Enter tuşuna basın.

1. Kitaplığınızın proje dizinine gidin. Tipik dosya konumunu yeniden sürece, konusu *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* dizini. Kaynak kodunuz ve bir proje dosyası dizini içeren *StringLibrary.csproj*.

1. Komutu Yürüt `dotnet pack --no-build`. `dotnet` Yardımcı olan bir paket oluşturur bir *.nupkg* uzantısı.

   > [!TIP]
   > Dizin, içeriyorsa *dotnet.exe* olduğundan, YOLUNUZDA değil girerek konumunda bulabilirsiniz `where dotnet.exe` konsol penceresinde.

NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz: [Çapraz Platform araçları ile bir NuGet paketi oluşturmak nasıl](../../core/deploying/creating-nuget-packages.md).
