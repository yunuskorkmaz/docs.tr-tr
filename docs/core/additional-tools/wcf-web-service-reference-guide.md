---
title: WCF Web hizmeti başvurusu Ekle
description: .NET Framework projelerine yönelik Hizmet Başvurusu Ekle benzer şekilde .NET Core ve ASP.NET Core projelerine yönelik işlevsellik ekleyen Microsoft WCF Web Service Reference Provider aracına genel bakış.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 11a18161db0fde522442e2412c4522811c5dd40a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926453"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a>WCF Web hizmeti başvuru sağlayıcısı aracını kullanma

Yıllarca, birçok Visual Studio geliştiricisi, .NET Framework projeleri Web hizmetlerine erişmek için gereken [**hizmet başvurusu Ekle**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) aracın üretkenliğini sağladı.  **WCF Web hizmeti başvuru** Aracı, .NET Core ve ASP.NET Core projeleri için hizmet başvurusu Ekle işlevselliği gibi bir deneyim sağlayan Visual Studio bağlı bir hizmet uzantısıdır. Bu araç, geçerli çözümdeki bir Web hizmetinden, bir ağ konumunda veya bir WSDL dosyasından meta verileri alır ve Web 'e erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren .NET Core ile uyumlu bir kaynak dosyası oluşturur hizmetle.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan hizmetlere başvurmanız gerekir. Güvenilmeyen bir kaynaktan başvuruları eklemek güvenliği tehlikeye atabilir.

## <a name="prerequisites"></a>Önkoşullar

* [Visual Studio 2017 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) veya sonraki sürümleri

## <a name="how-to-use-the-extension"></a>Uzantıyı kullanma

> [!NOTE]
> **WCF Web hizmeti başvuru** seçeneği, aşağıdaki proje şablonları kullanılarak oluşturulan projeler için geçerlidir:
>
> * **Visual C#**  .net >  **Core**
> * **Görsel C#**  .NET Standard  > 
> * **Visual C#**  Web >  ASP.NET CoreWeb > uygulaması

Örnek olarak **ASP.NET Core Web uygulaması** proje şablonunu kullanarak, bu makalede projeye bir WCF hizmeti başvurusu ekleme işlemi adım adım gösterilmektedir:

1. Çözüm Gezgini, projenin **bağlı hizmetler** düğümüne çift tıklayın (bir .NET Core veya .NET Standard projesi için, Çözüm Gezgini) projenin **Bağımlılıklar** düğümüne sağ tıkladığınızda bu seçenek kullanılabilir.

    **Bağlı hizmetler** sayfası, aşağıdaki görüntüde gösterildiği gibi görünür:

    ![.NET Core için Visual Studio bağlı hizmetler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. **Bağlı hizmetler** sayfasında, **Microsoft WCF Web Service Reference Provider**' ye tıklayın. Bu, **WCF Web hizmeti başvurusunu yapılandırma** Sihirbazı 'nı getirir:

    ![.NET Core için Visual Studio hizmeti uç noktası sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Bir hizmet seçin.

    3a. **WCF Web hizmeti başvurusunu yapılandırma** Sihirbazı 'nda kullanılabilen birkaç hizmet arama seçeneği vardır:

     * Geçerli çözümde tanımlanan Hizmetleri aramak için **bul** düğmesine tıklayın.
     * Belirtilen bir adreste barındırılan Hizmetleri aramak için, **Adres** kutusuna bir hizmet URL 'si girin ve **Git** düğmesine tıklayın.
     * Web hizmeti meta veri bilgilerini içeren bir WSDL dosyası seçmek için, **Gözden** geçirme düğmesine tıklayın.

    3b. **Hizmetler** kutusundaki arama sonuçları listesinden hizmeti seçin. Gerekirse, ilgili **ad alanı** metin kutusunda oluşturulan kod için ad alanını girin.

    3c. **Veri türü seçeneklerini** ve **istemci seçenekleri** sayfalarını açmak için **İleri** düğmesine tıklayın. Alternatif olarak, varsayılan seçenekleri kullanmak için **son** düğmesine tıklayın.

4. **Veri türü seçenekleri** formu, oluşturulan hizmet başvurusu yapılandırma ayarlarını iyileştirmenize olanak sağlar:

    ![.NET Core için Visual Studio veri türü seçenekleri sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > **Başvurulan derlemelerde türleri yeniden kullan** onay kutusu seçeneği, hizmet başvuru kodu oluşturma için gereken veri türleri projenizin Başvurulmuş derlemelerinden birinde tanımlandığında yararlıdır.  Derleme zamanı türü çakışmasına veya çalışma zamanı sorunlarından kaçınmak için bu mevcut veri türlerini yeniden kullanmak önemlidir.

    Proje bağımlılıklarının sayısına ve diğer sistem performansı faktörlere bağlı olarak tür bilgisi yüklenirken bir gecikme olabilir. **Başvurulan derlemelerde türleri yeniden kullan** onay kutusu Işaretli değilse **son** düğmesi yükleme sırasında devre dışıdır.

5. İşiniz bittiğinde **son** ' a tıklayın.

İlerleme durumunu görüntülerken araç:

* WCF hizmetinden meta verileri indirir.
* Hizmet başvuru kodunu *Reference.cs*adlı bir dosyada oluşturur ve **bağlı hizmetler** düğümü altında projenize ekler.
* Hedef platformda derlemek ve çalıştırmak için gereken NuGet paket başvuruları ile proje dosyasını (. csproj) güncelleştirir.

![Visual Studio Ilerleme penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Bu işlemler tamamlandığında, oluşturulan WCF istemci türünün bir örneğini oluşturabilir ve hizmet işlemlerini çağırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

### <a name="feedback--questions"></a>Geri bildirim & soruları

Sorularınız veya geri bildiriminiz varsa [GitHub ' da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Ayrıca, [GitHub 'DAKI WCF](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)deposundaki mevcut soruları veya sorunları da inceleyebilirsiniz.

### <a name="release-notes"></a>Sürüm notları

* Bilinen sorunlar da dahil olmak üzere, güncelleştirilmiş sürüm bilgileri için [sürüm notlarına](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) bakın.
