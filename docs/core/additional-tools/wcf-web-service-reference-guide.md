---
title: "Microsoft WCF Web hizmeti başvuru sağlayıcısı aracı"
description: "Microsoft WCF Web hizmeti başvuru sağlayıcısı .NET Core ve ASP.NET Core projeleri, .NET Framework projeleri için hizmet Başvurusu Ekle benzer işlevsellik ekleyen aracı genel bakış."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 210f0a9bbf393055ebcd582d3accb3d77b1c9539
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a>Microsoft WCF Web hizmeti başvuru sağlayıcısı aracı

Yıllar içinde birçok Visual Studio Geliştirici üretkenliği keyif aldığınızı, [ **hizmet Başvurusu Ekle** ](../../visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) web hizmetlerine erişmek .NET Framework projelerini gerektiğinde sağlanan aracı.  **WCF Web hizmeti başvuru** projeleri .NET Core ve ASP.NET Core için hizmet Başvurusu Ekle işlevleri gibi bir deneyim sağlar bir Visual Studio bağlı hizmet uzantısı araçtır. Bu araç, bir web hizmeti geçerli çözümdeki bir ağ konumu veya WSDL dosya meta verileri alır ve web erişmek için kullanabileceğiniz Windows Communication Foundation (WCF) istemci proxy kodu içeren bir .NET Core uyumlu kaynak dosyası oluşturur hizmet.

> [!IMPORTANT]
> Yalnızca güvenilir bir kaynaktan Hizmetleri başvuruda bulunmalıdır. Güvenilmeyen bir kaynaktan başvuruları ekleme, güvenliği tehlikeye atabilir. 

## <a name="how-to-use-the-extension"></a>Uzantı kullanma

> [!NOTE]
> **WCF Web hizmeti başvuru** seçenektir aşağıdaki proje şablonları kullanılarak oluşturulmuş projeler için geçerlidir:
> * **Visual C#** > **.NET Core**
> * **Visual C#** > **.NET Standard**
> * **Visual C#** > **Web** > **ASP.NET Core Web Application**

Kullanarak **ASP.NET çekirdek Web uygulaması** proje şablonu bir örnek olarak, bu makalede anlatılmaktadır, projeye bir WCF Hizmeti başvuru eklerken size:

1. Çözüm Gezgini'nde çift tıklayarak **bağlantılı Hizmetler** proje düğümünün (için .NET Core veya .NET standart bir proje üzerinde sağ tıklattığınızda bu seçenek kullanılabilir **bağımlılıkları** düğümü Çözüm Gezgini'nde projeye).

**Bağlantılı Hizmetler** sayfası aşağıdaki görüntüde gösterildiği gibi görünür:

![Bağlı hizmetler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. Üzerinde **bağlantılı Hizmetler** sayfasında, **Microsoft WCF Web hizmeti başvuru sağlayıcısı**. Bu işlem sonrasında **yapılandırma WCF Web hizmeti başvuru** Sihirbazı:

![Hizmet uç noktası sekmesi](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. Bir hizmeti seçin.

    3a. Çeşitli hizmetler arama seçenekleri içinde kullanılabilir **yapılandırma WCF Web hizmeti başvuru** Sihirbazı:
    
     * Geçerli çözümde tanımlanan Hizmetleri aramak için tıklatın **bulma** düğmesi. 
     * Belirtilen bir adres barındırılan hizmetleri aramak için bir hizmet URL'si girin **adresi** kutusuna ve tıklatın **Git** düğmesi.
     * Web hizmeti meta veri bilgileri içeren bir WSDL dosya seçmek için tıklatın **Gözat** düğmesi. 
     
    3b. Arama sonuçları listesinden hizmeti seçin **Hizmetleri** kutusu. Gerekirse, karşılık gelen üretilen kod için ad alanı girin **Namespace** metin kutusu.
    
    3c. Tıklatın **sonraki** açmak için düğmeye **veri türü seçenekleri** ve **istemci seçenekleri** sayfaları. Alternatif olarak, **son** düğmesi varsayılan seçenekleri kullanın.


4. **Veri türü seçenekleri** form oluşturulan hizmet başvurusu yapılandırma ayarlarını İyileştir olanak sağlar:

![Veri türü Seçenekler sekmesi](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> **Yeniden başvurulan derlemelerin türlerinde** onay kutusu seçeneği, hizmet başvurusu kod oluşturma için gerekli veri türleri, projenizin başvurulan derlemelerin birinde tanımlandığında yararlıdır.  Derleme zamanı tür çakışmasından veya çalışma zamanı sorunlarını önlemek için bu var olan veri türleri yeniden önemlidir.

Tür bilgileri, proje bağımlılıklarını sayısı ve diğer sistem performans etkenlere bağlı olarak yüklenirken bir gecikme olabilir. **Son** düğmesi devre dışı sürece yükleme sırasında **yeniden başvurulan derlemelerin türlerinde** onay kutusunun işaretli olduğundan.

5. Tıklatın **son** işiniz bittiğinde.


İlerleme durumunu, aracı görüntüleme oluştu:

* WCF hizmetinden meta verileri indirir. 
* Hizmet başvurusu kod adındaki bir dosyada oluşturur *reference.cs*ve altında projenize ekler **bağlantılı Hizmetler** düğümü. 
* NuGet paket başvurularıyla derlemek ve hedef platformu üzerinde çalıştırmak için gerekli proje dosyası (.csproj) güncelleştirir.

![İlerleme penceresi](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

Bu işlemleri tamamladığınızda, oluşturulan WCF istemci türünün bir örneği oluşturun ve hizmet işlemlerini çağırma.

## <a name="next-steps"></a>Sonraki adımlar

### <a name="feedback--questions"></a>Geri bildirim & sorular
Sorularınız veya geri bildirim, varsa [github'da bir sorun açın](https://github.com/dotnet/wcf/issues/new). Herhangi bir varolan sorular veya sorunlar gözden geçirebilirsiniz [WCF bağlantıların github'da adresindeki](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Sürüm Notları
* Başvurmak [sürüm notları](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) güncelleştirilmiş sürüm bilgileri için bilinen sorunlar da dahil olmak üzere. 
