---
title: WCF Web Hizmeti Başvurusu Ekle
description: .NET Framework projeleri için Hizmet Başvurusu Ekle'ye benzer şekilde .NET Core ve ASP.NET Core projeleri için işlevsellik ekleyen Microsoft WCF Web Hizmeti Başvuru Sağlayıcısı Aracına genel bakış.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715680"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>WCF Web Hizmeti Başvuru Sağlayıcı Aracını Kullanma

Yıllar içinde, birçok Visual Studio geliştiricisi, [**.NET**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) Framework projelerinin web hizmetlerine erişmek için gerekli olduğunda Hizmet Başvurusu Ekle aracının sağladığı üretkenliğin keyfini çıkarmış oldu.  **WCF Web Service Reference** aracı, .NET Core ve ASP.NET Core projeleri için Hizmet Başvurusu Ekle işlevi gibi bir deneyim sağlayan Visual Studio'ya bağlı bir hizmet uzantısıdır. Bu araç, geçerli çözümdeki bir web hizmetinden, ağ konumundan veya WSDL dosyasından meta verileri alır ve web'e erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodunu içeren bir .NET Core uyumlu kaynak dosyası oluşturur Hizmet.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan gelen hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan referans eklemek güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 sürüm 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümler

## <a name="how-to-use-the-extension"></a>Uzantı nasıl kullanılır?

> [!NOTE]
> **WCF Web Hizmeti Başvurusu** seçeneği, aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:
>
> - **Görsel C#** > **.NET Çekirdek**
> - **Görsel C#** > **.NET Standardı**
> - **Visual C#** > **Web** > **ASP.NET Çekirdek Web Uygulaması**

ASP.NET **Çekirdek Web Uygulaması** proje şablonu örnek olarak kullanarak, bu makale projeye bir WCF hizmet başvurusu ekleyerek size yol gösterir:

1. Çözüm Gezgini'nde, projenin **Bağlı Hizmetler** düğümüne çift tıklayın (.NET Core veya .NET Standard projesi için bu seçenek, Çözüm Gezgini'nde projenin **Bağımlılıklar** düğümüne sağ tıkladığınızda kullanılabilir).

    **Bağlı Hizmetler** sayfası aşağıdaki resimde gösterildiği gibi görünür:

    ![.NET Core için Visual Studio Bağlantılı Hizmetler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Bağlı **Hizmetler** sayfasında, **Microsoft WCF Web Hizmeti Başvuru Sağlayıcısı'nı**tıklatın. Bu, **Yapılandırılan WCF Web Hizmeti Başvurusu** sihirbazını getirir:

    ![.NET Core için Visual Studio Service Endpoint sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Bir hizmet seçin.

    3a. **Yapılandırma WCF Web Hizmeti Başvuru** sihirbazı içinde çeşitli hizmetler arama seçenekleri vardır:

     * Geçerli çözümde tanımlanan hizmetleri aramak için **Keşfet** düğmesini tıklatın.
     * Belirli bir adreste barındırılan hizmetleri aramak için **Adres** kutusuna bir hizmet URL'si girin ve **Git** düğmesini tıklatın.
     * Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için **Gözat** düğmesini tıklatın.

    3b' ye kadar. **Hizmetler** kutusundaki arama sonuçları listesinden hizmeti seçin. Gerekirse, ilgili **Namespace** metin kutusuna oluşturulan kodun ad alanını girin.

    3c' ye kadar. **Veri Türü Seçenekleri** ve **İstemci Seçenekleri** sayfalarını açmak için **İleri** düğmesini tıklatın. Alternatif olarak, varsayılan seçenekleri kullanmak için **Bitir** düğmesini tıklatın.

4. **Veri Türü Seçenekleri** formu, oluşturulan hizmet başvurusu yapılandırma ayarlarını hassaslaştırmanızı sağlar:

    ![.NET Core için Visual Studio Veri türü seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > Başvurulan derlemeler onay kutusu **seçeneğindeki Yeniden Kullanım türleri,** hizmet başvuru kodu oluşturma için gereken veri türleri projenizin başvurulan derlemelerinden birinde tanımlandığında yararlıdır.  Derleme zamanı türü çakışmasını veya çalışma zamanı sorunlarını önlemek için bu varolan veri türlerini yeniden kullanmak önemlidir.

    Proje bağımlılıklarının ve diğer sistem performans faktörlerinin sayısına bağlı olarak, tür bilgileri yüklenirken gecikme olabilir. **Başvurulan derlemeler** onay kutusundaki Yeniden Kullan türleri işaretlenmemiş sayılmadığı sürece, Yükleme sırasında **Bitiş** düğmesi devre dışı bırakılır.

5. Bittiğinde **Bitir'i** tıklatın.

İlerleme görüntülerken, araç:

- WCF hizmetinden meta veri indirir.
- *reference.cs*adlı bir dosyada hizmet başvuru kodunu oluşturur ve **Bağlı Hizmetler** düğümü altında projenize ekler.
- Proje dosyasını (.csproj) hedef platformda derlemek ve çalıştırmak için gereken NuGet paket referanslarıyla güncelleştirir.

![Visual Studio İlerleme penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Bu işlemler tamamlandığında, oluşturulan WCF istemci türünün bir örneğini oluşturabilir ve hizmet işlemlerini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Communication Foundation uygulamaları yla başlayın](../../framework/wcf/getting-started-tutorial.md)
- [Visual Studio'da Windows Communication Foundation hizmetleri ve WCF veri hizmetleri](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [WCF desteklenen özellikler .NET Core'da](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a>Geri bildirim & sorular

Herhangi bir sorunuz veya geri bildiriminiz varsa, [sorun bildir](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) aracını kullanarak [Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/) bildirin.

## <a name="release-notes"></a>Sürüm notları

- Bilinen sorunlar da dahil olmak üzere güncelleştirilmiş sürüm bilgileri için [Yayın notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) bakın.
