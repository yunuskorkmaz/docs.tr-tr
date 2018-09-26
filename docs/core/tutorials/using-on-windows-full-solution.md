---
title: Visual Studio 2017'yi kullanarak, Windows üzerinde eksiksiz bir .NET Core çözümü derleme
description: Windows üzerinde Visual Studio 2017'de eksiksiz bir .NET Core çözümü oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: 15537ea8c68b5c873bbf26ab0519a19de0b13230
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969567"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Visual Studio 2017'yi kullanarak, Windows üzerinde eksiksiz bir .NET Core çözümü derleme

Visual Studio 2017, .NET Core uygulamaları geliştirmek için bir tam özellikli bir geliştirme ortamı sağlar. Bu belgedeki yordamları, test ve üçüncü taraf kitaplıklar kullanılarak yeniden kullanılabilir kitaplıklar içeren tipik bir .NET Core çözümü oluşturmak gereken adımları açıklar. 

## <a name="prerequisites"></a>Önkoşullar

Yönergeleri takip edin [önkoşulları sayfamızı](../windows-prerequisites.md) ortamınızı güncelleştirilecek.

## <a name="a-solution-using-only-net-core-projects"></a>Yalnızca .NET Core projeleri kullanarak çözümü

### <a name="writing-the-library"></a>Kitaplığı yazma

1. Visual Studio'da **dosya**, **yeni**, **proje**. İçinde **yeni proje** iletişim kutusunda genişletin **Visual C#** düğüm ve **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)**. 

2. Adı ' % s'projesi "Library" ve "Altın" Çözüm. Bırakın **çözüm için dizin oluştur** işaretli. **Tamam**'ı tıklatın.

3. Çözüm Gezgini'nde, bağlam menüsünü açın **bağımlılıkları** düğümünü seçip **NuGet paketlerini Yönet**.

4. "Nuget.org" olarak seçin **paket kaynağı**ve **Gözat** sekmesi. Göz atın **Newtonsoft.Json**. Tıklayın **yükleme**, lisans sözleşmesini kabul edin. Paket artık altında görünmelidir **bağımlılıkları/NuGet** ve otomatik olarak geri yüklenir.

5. Yeniden adlandırma `Class1.cs` dosyasını `Thing.cs`. Sınıfı yeniden adlandırılması kabul edin. Bir yöntem ekleyin: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

   Çözüm, hatasız oluşturması gerekir.

### <a name="writing-the-test-project"></a>Test projesi yazma

1. Çözüm Gezgini'nde, bağlam menüsünü açın **çözüm** düğümünü seçip **Ekle**, **yeni proje**. İçinde **yeni proje** iletişim altında **Visual C# / .NET Core**, seçin **birim testi projesi (.NET Core)**. "TestLibrary" olarak adlandırın ve Tamam'a tıklayın. 

2. İçinde **TestLibrary** için bağlam menüsünü açın, proje **bağımlılıkları** düğüm ve **Başvuru Ekle**. Tıklayın **projeleri**, sonra kitaplık projesi işaretleyin ve Tamam'a tıklayın. Bu test projesinden, kitaplığına bir başvuru ekler.

3. Yeniden adlandırma `UnitTest1.cs` dosyasını `LibraryTests.cs` sınıfı yeniden adlandır kabul edin. Ekleme `using Library;` dosyasını ve değiştirme en üstüne `TestMethod1` yöntemini aşağıdaki kod ile:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Şimdi çözüm oluşturulabiliyor olması gerekir. 
   
4. Üzerinde **Test** menüsünde seçin **Windows**, **Test Gezgini** test Gezgini penceresi çalışma alanınıza almak için. Birkaç saniye sonra `ThingGetsObjectValFromNumber` test, test Gezgini'nde görüntülenmelidir. Seçin **çalıştırması**.
   
   Test geçişi yapılmalıdır.

### <a name="writing-the-console-app"></a>Konsol uygulaması yazma

1. Çözüm Gezgini'nde, çözümü için bağlam menüsünü açın ve yeni bir **konsol uygulaması (.NET Core)** proje. "Uygulama" olarak adlandırın.

2. İçinde **uygulama** için bağlam menüsünü açın, proje **bağımlılıkları** düğüm ve **Ekle**, **başvuru**. 

3. İçinde **başvuru Yöneticisi** iletişim kutusunda, onay **Kitaplığı** altında **projeleri**, **çözüm** düğümünü ve ardından **Tamam**

6. Bağlam menüsünü **uygulama** düğüm ve **başlangıç projesi olarak ayarla**. Bu, F5 veya CTRL + F5 tuşlarına basarak konsol uygulamasını Başlat sağlar.

7. Açık `Program.cs` ekleyin bir `using Library;` dosyanın en üstüne yönerge ve ardından eklemek `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` için `Main` yöntemi.

8. Az önce eklediğiniz bir satırın sonunda bir kesme noktası ayarlayın.

9. Uygulamayı çalıştırmak için F5 tuşuna basın...

   Uygulama hatasız oluşturması gerekir ve kesme noktasına isabet. Aynı zamanda "yanıt 42 sağlıyor." uygulama çıkış denetleme olanağına olmalıdır.
