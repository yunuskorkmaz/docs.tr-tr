---
title: Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6962ed1dccca6db2e55554459742adab210585ef
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654991"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="ac082-102">Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac082-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="ac082-103">Internet Information Services (IIS) 7.0 seçmeli olarak gerekli olan bileşenler yüklemenize olanak sağlayan modüler bir tasarım sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac082-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="ac082-104">Bu tasarım, sunulan yeni bildirim temelli temsilinde teknolojisi dayalı [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac082-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="ac082-105">40'tan fazla tek başına özelliği bileşenleri bağımsız olarak yüklenebilir bir IIS 7.0 vardır.</span><span class="sxs-lookup"><span data-stu-id="ac082-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="ac082-106">Bu, BT uzmanları yüklemenin gerekli kolayca özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac082-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="ac082-107">Bu konuda, IIS 7.0, Windows Communication Foundation (WCF) ile kullanım için yapılandırın ve hangi bileşenlerin gerektiğini belirlemek nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac082-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="ac082-108">En düşük düzeyde yükleme: WAS'ı yükleme</span><span class="sxs-lookup"><span data-stu-id="ac082-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="ac082-109">Windows İşlem Etkinleştirme Hizmeti (WAS) tüm IIS 7.0 paketin en düşük düzeyde yükleme yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="ac082-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="ac082-110">Tek başına bir özellik olan ve yalnızca tüm kullanılabilir IIS 7.0 özellikten olan [!INCLUDE[wv](../../../../includes/wv-md.md)] işletim sistemleri (Home Basic, Home Premium, iş ve Ultimate ve Enterprise).</span><span class="sxs-lookup"><span data-stu-id="ac082-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="ac082-111">Denetim Masası'ndan tıklayın **programlar** ve ardından **kapatma Windows özelliklerini aç veya Kapat** altında listelenen **programlar ve Özellikler**, WAS bileşen gösterilir Aşağıdaki resimde olduğu gibi liste.</span><span class="sxs-lookup"><span data-stu-id="ac082-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="ac082-112">![Özelliklerini açma veya kapatma iletişim](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="ac082-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="ac082-113">Bu özellik aşağıdaki alt bileşenlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ac082-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="ac082-114">.NET ortamı</span><span class="sxs-lookup"><span data-stu-id="ac082-114">.NET Environment</span></span>

- <span data-ttu-id="ac082-115">Yapılandırma API'leri</span><span class="sxs-lookup"><span data-stu-id="ac082-115">Configuration APIs</span></span>

- <span data-ttu-id="ac082-116">İşlem modeli</span><span class="sxs-lookup"><span data-stu-id="ac082-116">Process Model</span></span>

 <span data-ttu-id="ac082-117">Yalnızca kök düğümünü WAS, seçerseniz **işlem modeli** alt düğümünde, varsayılan olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ac082-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="ac082-118">Bir Web sunucusu desteği olduğundan bu yükleme işlemine yalnızca WAS, yüklemekte olduğunuz olduğunu lütfen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ac082-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="ac082-119">WCF veya herhangi bir ASP.NET uygulaması iş yapmak için kontrol **.NET ortamını** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="ac082-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="ac082-120">Bu, WAS bileşenlerinin tümünü WCF ve ASP.NET iyi çalışması için gerekli olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ac082-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="ac082-121">Bu bileşenlerden birini yükledikten sonra bu otomatik olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ac082-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="ac082-122">IIS 7.0: Varsayılan yükleme</span><span class="sxs-lookup"><span data-stu-id="ac082-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="ac082-123">Denetleyerek **Internet Information Services** özelliğini, alt düğümlerinden bazıları aşağıdaki çizimde gösterildiği gibi otomatik olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="ac082-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="ac082-124">![IIS 7.0 özellikleri için varsayılan ayarlar](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="ac082-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="ac082-125">IIS 7.0, bu varsayılan yüklemedir.</span><span class="sxs-lookup"><span data-stu-id="ac082-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="ac082-126">Bu yükleme işlemine hizmet statik içerik (örneğin, HTML sayfaları ve diğer içerik) için IIS 7.0 kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac082-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="ac082-127">Ancak, ASP.NET veya CGI uygulaması veya WCF hizmetlerini barındırmak çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="ac082-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="ac082-128">IIS 7.0: ASP.NET desteği ile yükleme</span><span class="sxs-lookup"><span data-stu-id="ac082-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="ac082-129">ASP.NET IIS 7.0 üzerinde çalışır hale getirmek için ASP.NET yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac082-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="ac082-130">Denetledikten sonra **ASP.NET**, ekranınızın aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac082-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="ac082-131">![Asp.NET gerekli ayarları](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="ac082-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="ac082-132">IIS 7. 0'çalışması hem WCF ve ASP.NET uygulamaları için en az ortamı budur.</span><span class="sxs-lookup"><span data-stu-id="ac082-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="ac082-133">IIS 7.0: IIS 6.0 Uyumluluk bileşenleri ile yükleme</span><span class="sxs-lookup"><span data-stu-id="ac082-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="ac082-134">IIS 7.0, Visual Studio 2005 veya bazı diğer Otomasyon betikleri ya da IIS 6.0 metatabanı API kullanan sanal uygulamaları yapılandırma araçları (örneğin, Adsutil.vbs) bir sistemde yüklerken, IIS 6.0 kontrol etmenizi sağlamak **komut dosyası oluşturma araçları**.</span><span class="sxs-lookup"><span data-stu-id="ac082-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="ac082-135">IIS 6.0 diğer alt düğümlerini otomatik olarak denetler **Yönetim uyumluluğu**.</span><span class="sxs-lookup"><span data-stu-id="ac082-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="ac082-136">Bunu yaptıktan sonra aşağıdaki çizim ekran gösterir:</span><span class="sxs-lookup"><span data-stu-id="ac082-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="ac082-137">![IIS 6.0 Yönetim uyumluluk ayarları](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="ac082-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="ac082-138">Bu yükleme ile IIS 7.0, ASP.NET ve WCF özellikler ve örnekler kullanılabilir Web üzerinde kullanmak için gereken her şeye sahip.</span><span class="sxs-lookup"><span data-stu-id="ac082-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="ac082-139">İstek sınırları</span><span class="sxs-lookup"><span data-stu-id="ac082-139">Request Limits</span></span>
 <span data-ttu-id="ac082-140">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] IIS 7'in varsayılan değer, `maxUri` ve `maxQueryStringSize` ayarları değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ac082-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="ac082-141">İstek Filtreleme IIS 7. 0 ', varsayılan olarak, bir URL uzunluğu 4096 karakter ve bir sorgu dizesi uzunluğu 2048 karakter sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac082-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="ac082-142">Değiştirmek için bu varsayılan, App.config dosyanıza aşağıdaki XML'i ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac082-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="ac082-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac082-143">See also</span></span>

- [<span data-ttu-id="ac082-144">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="ac082-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [<span data-ttu-id="ac082-145">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac082-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="ac082-146">Nasıl yapılır: WCF etkinleştirme bileşenlerini yükleme ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac082-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [<span data-ttu-id="ac082-147">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="ac082-147">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
