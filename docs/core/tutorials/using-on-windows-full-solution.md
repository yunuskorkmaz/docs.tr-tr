---
title: Visual Studio 2017 kullanarak Windows'da eksiksiz bir .NET Core çözümü oluşturma
description: Visual Studio 2017 Windows üzerinde tam bir .NET Core çözümde oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak Windows'da eksiksiz bir .NET Core çözümü oluşturma

Visual Studio 2017 .NET Core uygulamaları geliştirmek için bir tam özellikli bir geliştirme ortamı sağlar. Bu belgedeki yordamlar, test ve üçüncü taraf kitaplıklar kullanılarak yeniden kullanılabilir kitaplıklarını içerir tipik bir .NET Core çözümü oluşturmak için gereken adımları açıklar. 

## <a name="prerequisites"></a>Önkoşullar

Yönergeleri izleyerek [Önkoşullar sayfamızı](../windows-prerequisites.md) ortamınızı güncelleştirmek için.

## <a name="a-solution-using-only-net-core-projects"></a>Yalnızca .NET çekirdeği projeleri kullanarak bir çözüm

### <a name="writing-the-library"></a>Kitaplık yazma

1. Visual Studio'da, **dosya**, **yeni**, **proje**. İçinde **yeni proje** iletişim kutusunda, genişletin **Visual C#** düğümü ve seçin **.NET standart** düğümünü ve ardından **(.NET standart)sınıfkitaplığı**. 

2. Adı "Kitaplığı" proje ve Çözüm "Altın". Bırakın **çözüm için dizin oluştur** işaretli. **Tamam**'ı tıklatın.

3. Çözüm Gezgini'nde bağlam menüsünü açın **bağımlılıkları** düğümü seçin **NuGet paketlerini Yönet**.

4. "Nuget.org" olarak seçin **paket kaynağı**ve seçin **Gözat** sekmesi. Göz **Newtonsoft.Json**. Tıklatın **yükleme**ve Lisans Sözleşmesi'ni kabul edin. Paket artık altında görünmelidir **bağımlılıkları/NuGet** ve otomatik olarak geri yüklenir.

5. Yeniden Adlandır `Class1.cs` dosyasını `Thing.cs`. Yeniden Adlandır sınıfının kabul edin. Bir yöntem ekleyin: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Üzerinde **yapı** menüsünde seçin **yapı çözümü**.

   Çözüm hatasız oluşturması gerekir.

### <a name="writing-the-test-project"></a>Oluşturduğunuz test projesinin yazma

1. Çözüm Gezgini'nde bağlam menüsünü açın **çözüm** düğümü seçin **Ekle**, **yeni proje**. İçinde **yeni proje** iletişim altında **Visual C# / .NET Core**, seçin **birim testi projesi (.NET Core)**. "TestLibrary" olarak adlandırın ve Tamam'ı tıklatın. 

2. İçinde **TestLibrary** proje, bağlam menüsünü açın **bağımlılıkları** düğümü seçin **Başvuru Ekle**. Tıklatın **projeleri**, ardından kitaplığı projesi kontrol edin ve Tamam'ı tıklatın. Bu test projesinin kitaplığınıza bir başvuru ekler.

3. Yeniden Adlandır `UnitTest1.cs` dosya `LibraryTests.cs` ve sınıf rename kabul edin. Ekleme `using Library;` dosyasını ve Değiştir üstüne `TestMethod1` aşağıdaki kod ile yöntemi:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Artık çözümü oluşturabiliyor olması gerekir. 
   
4. Üzerinde **Test** menüsünde seçin **Windows**, **Test Gezgini** test Gezgini penceresi çalışma alanınıza alabilmek için. Birkaç saniye sonra `ThingGetsObjectValFromNumber` test test Explorer'da görünmelidir. Seçin **çalıştırması**.
   
   Test geçirmelisiniz.

### <a name="writing-the-console-app"></a>Konsol uygulaması yazma

1. Çözüm Gezgini'nde, çözüm bağlam menüsünü açın ve yeni bir ekleyin **konsol uygulaması (.NET Core)** projesi. "Uygulama" adı.

2. İçinde **uygulama** proje, bağlam menüsünü açın **bağımlılıkları** düğümü seçin **Ekle**, **başvuru**. 

3. İçinde **başvuru Yöneticisi** iletişim kutusunda, onay **Kitaplığı** altında **projeleri**, **çözüm** düğümünü ve ardından **Tamam**

6. Bağlam menüsünü açın **uygulama** düğümü seçin **başlangıç projesi olarak ayarla**. Bu, F5 veya CTRL + F5 tuşuna konsol uygulaması başlangıç sağlar.

7. Açık `Program.cs` dosya, ekleme bir `using Library;` dosyanın en üstüne yönerge ve ardından ekleyin `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` için `Main` yöntemi.

8. Yeni eklediğiniz satırından sonra bir kesme noktası ayarlayın.

9. Uygulamayı çalıştırmak için F5'e basın...

   Uygulama hatasız oluşturmalısınız ve kesme noktası isabet. Uygulama "yanıt 42 var." çıktı denetleyebilmek olmalıdır.
