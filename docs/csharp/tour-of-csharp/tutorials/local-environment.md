---
title: C# ' ye giriş-geliştirme araçları hakkında bilgi sahibi olun
description: Bu makalede, makinenizde C# ve .NET uygulamaları geliştirmek için kullanacağınız araçlara temel bir giriş sunulmaktadır.
ms.date: 02/02/2021
ms.openlocfilehash: 72116154126b0a97fffe417b2807576b1d9689df
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626811"
---
# <a name="set-up-your-local-environment"></a>Yerel ortamınızı ayarlama

Makinenizde bir öğretici çalıştırmanın ilk adımı bir geliştirme ortamı kurmak. Aşağıdaki seçeneklerden birini belirleyin:

* .NET CLı 'yı ve seçtiğiniz metin veya kod düzenleyicisini kullanmak için bkz. [10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).net öğreticisi Merhaba dünya. Öğreticide, Windows, Linux veya macOS 'ta bir geliştirme ortamı ayarlamaya yönelik yönergeler bulunur.
* .NET CLı ve Visual Studio Code kullanmak için [.NET SDK](https://dotnet.microsoft.com/download) ve [Visual Studio Code](https://code.visualstudio.com/)' yi yükleyip.
* Visual Studio 2019 ' i kullanmak için bkz. [öğretici: Visual Studio 'da basit bir C# konsol uygulaması oluşturma](/visualstudio/get-started/csharp/tutorial-console).

## <a name="basic-application-development-flow"></a>Temel uygulama geliştirme akışı

Bu öğreticilerde yer alan yönergeler, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullandığınızı varsayar. Aşağıdaki komutları kullanacaksınız:

* [`dotnet new`](../../../core/tools/dotnet-new.md) bir uygulama oluşturur. Bu komut, uygulamanız için gerekli olan dosyaları ve varlıkları oluşturur. C# öğreticilerine giriş, `console` uygulama türünü kullanır. Temel bilgileri aldıktan sonra diğer uygulama türlerine genişletebilirsiniz.
* [`dotnet build`](../../../core/tools/dotnet-build.md) yürütülebilir dosyayı oluşturur.
* [`dotnet run`](../../../core/tools/dotnet-run.md) yürütülebilir dosyayı çalıştırır.

Bu öğreticiler için Visual Studio 2019 kullanıyorsanız, bir öğretici bu CLı komutlarından birini çalıştırmaya yönlendirirse bir Visual Studio menü seçimi seçersiniz:

* **Dosya**  >  **Yeni**  >  **Proje** bir uygulama oluşturur.
* **Derleme**  >   **Yapı çözümü** yürütülebilir dosyayı oluşturur.
* **Hata Ayıkla**  >  **Hata ayıklama olmadan Başlat** yürütülebilir dosyayı çalıştırır.

## <a name="pick-your-tutorial"></a>Öğreticinizi seçin

Aşağıdaki öğreticilerden herhangi biriyle başlayabilirsiniz:

## <a name="numbers-in-c"></a>C 'deki sayılar\#

C# öğreticisindeki [sayılarda](numbers-in-csharp-local.md) , bilgisayarların sayıları nasıl depolayacağınızı ve farklı sayısal türlerle hesaplamaların nasıl gerçekleştirileceğini öğreneceksiniz. Yuvarlama hakkında temel bilgileri ve C# kullanarak matematik hesaplamaları yapmayı öğreneceksiniz.

Bu öğreticide, [Hello World](hello-world.yml) ders 'i tamamladığınız varsayılmaktadır.

## <a name="branches-and-loops"></a>Dal ve döngüler

[Dallar ve döngüler](branches-and-loops-local.md) öğreticisinde, değişkenlerde depolanan değerlere göre farklı kod yürütme yolları seçmenin temelleri öğretilir. Denetim akışının temel bilgilerini öğrenirsiniz. Bu, programların kararlar alma ve farklı eylemler seçme işlemlerinin temelini oluşturur.

Bu öğreticide, [Hello World](hello-world.yml) ve C# dersleri Ile ilgili [sayıların](numbers-in-csharp-local.md) tamamlandığını varsayılmaktadır.

## <a name="list-collection"></a>Liste koleksiyonu

[Liste koleksiyonu](arrays-and-collections.md) dersi, veri dizilerini depolayan liste koleksiyonu türünün bir turuna sahip olmanızı sağlar. Öğe ekleme ve kaldırma, öğe arama ve listeleri sıralama hakkında bilgi edineceksiniz. Farklı liste türleri keşfedebilirsiniz.

Bu öğreticide, yukarıda listelenen dersleri tamamladığınız varsayılmaktadır.
