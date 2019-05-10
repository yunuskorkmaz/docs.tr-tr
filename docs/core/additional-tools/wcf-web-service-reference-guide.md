---
title: WCF Web servisi Başvurusu Ekle
description: Microsoft WCF Web Service Reference Provider .NET Core ve ASP.NET Core projeleri için .NET Framework projeleri için hizmet Başvurusu Ekle benzer işlevsellik ekleyen aracı genel bakış.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 806f6e90aedc669c3a56ce1cde64311bdd4af32c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750500"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>WCF Web hizmeti başvurusu sağlayıcısı aracını kullanma

Yıllar içinde birçok Visual Studio Geliştirici üretkenliğini keyif aldığınızı, [ **hizmet Başvurusu Ekle** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) .NET Framework projelerini web hizmetlerine erişmek gerektiğinde sağlanan aracı.  **WCF Web Service Reference** sağlayan bir hizmet Başvurusu Ekle işlev gibi bir deneyim için .NET Core ve ASP.NET Core projeleri Visual Studio bağlı hizmeti uzantısı bir araçtır. Bu araç, bir ağ konumu üzerinde mevcut çözümde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve web erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren bir .NET Core uyumlu kaynak dosyası oluşturur hizmeti.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvurularının eklenmesi, güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümler

## <a name="how-to-use-the-extension"></a>Uzantısını kullanma

> [!NOTE]
> **WCF Web Service Reference** seçenektir aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:
> * **Görsel C#**   >  **.NET Core**
> * **Görsel C#**   >  **.NET Standard**
> * **Görsel C#**   >  **Web** > **ASP.NET Core Web uygulaması**

Kullanarak **ASP.NET Core Web uygulaması** proje şablonu örnek olarak, bu makalede gösterilmektedir, projeye WCF hizmet başvurusu ekleme yoluyla:

1. Çözüm Gezgini'nde çift tıklayarak **bağlı hizmetler** proje düğümü (.NET Core veya .NET Standard projesi üzerinde sağ tıkladığınızda bu seçenek kullanılabilir **bağımlılıkları** düğümü Çözüm Gezgini'nde projeye).

    **Bağlı hizmetler** sayfası, aşağıdaki görüntüde gösterildiği gibi görünür:

    ![.NET Core için Visual Studio bağlı Hizmetler'i sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Üzerinde **bağlı hizmetler** sayfasında **Microsoft WCF Web Service Reference Provider**. Bu işlem sonrasında **yapılandırma WCF Web Service Reference** Sihirbazı:

    ![.NET Core için Visual Studio hizmet uç noktası sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Bir hizmet seçin.

    3a. Çeşitli Hizmetleri arama seçenekleri kapsamında sunulan **yapılandırma WCF Web Service Reference** Sihirbazı:

     * Geçerli çözümde tanımlanan Hizmetleri aramak için tıklayın **bulma** düğmesi.
     * Belirtilen adresteki barındırılan hizmetler aramak için bir hizmeti URL'sini girin. **adresi** kutusuna ve tıklatın **Git** düğmesi.
     * Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için tıklatın **Gözat** düğmesi.

    3b. Arama sonuçları listesinden hizmeti seçin **Hizmetleri** kutusu. Gerekirse, karşılık gelen oluşturulan kodun ad alanını girin **Namespace** metin kutusu.

    3c. Tıklayın **sonraki** açmak için düğmeyi **veri türü seçenekleri** ve **istemci seçenekleri** sayfaları. Alternatif olarak, **son** düğmesine varsayılan seçenekleri kullanın.

4. **Veri türü seçenekleri** form, oluşturulan hizmet başvurusu yapılandırma ayarları iyileştirmek sağlar:

    ![.NET Core için Visual Studio veri türü Seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > **Bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu seçeneğini, hizmet başvurusu kod oluşturma için gerekli veri türleri, projenizin başvurulan derlemeleri birinde tanımlandığında yararlıdır.  Derleme zamanı tür çakışmasına veya çalışma zamanı sorunlarını önlemek için bu var olan veri türleri yeniden kullan önemlidir.

    Tür bilgileri yüklenirken proje bağımlılıkları sayısı ve diğer sistem performans etkenlere bağlı olarak bir gecikme olabilir. **Son** düğmesi devre sürece yükleme sırasında **bütünleştirilmiş kodlardaki türleri yeniden** onay kutusu olarak işaretli değildir.

5. Tıklayın **son** işiniz bittiğinde.

İlerleme durumunu, aracın görüntüleme oluştu:

* WCF hizmetinden meta verileri indirir.
* Hizmet başvuru kodu adındaki bir dosyada oluşturur *reference.cs*ve projenizi altına ekler **bağlı hizmetler** düğümü.
* Derleme ve hedef platformda çalıştırmak için gerekli NuGet paket başvuruları içeren proje dosyasına (.csproj) güncelleştirir.

![Visual Studio ilerleme durumu penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Bu işlemleri tamamladığınızda, oluşturulan WCF istemci türü örneği oluşturun ve hizmet işlemleri çağırma.

## <a name="next-steps"></a>Sonraki adımlar

### <a name="feedback--questions"></a>Geri bildirim ve sorular

Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Mevcut bir soru veya sorunlarla gözden geçirebilirsiniz [WCF deponun GitHub üzerinde en](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Sürüm notları

* Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere.
