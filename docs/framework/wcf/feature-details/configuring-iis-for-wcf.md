---
title: Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 6b0cc48c7a817f71339fb6d7eea35baf1d97b245
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556661"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="b99de-102">Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b99de-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="b99de-103">Internet Information Services (IIS) 7,0, gereken bileşenleri seçmeli olarak yüklemenize olanak sağlayan modüler bir tasarıma sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b99de-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="b99de-104">Bu tasarım, Windows Vista 'da tanıtılan yeni bildirim temelli bileşen teknolojisini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b99de-104">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="b99de-105">IIS 7,0 ' ün bağımsız olarak tek başına yüklenebilen 40 ' den fazla bağımsız Özellik bileşeni vardır.</span><span class="sxs-lookup"><span data-stu-id="b99de-105">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="b99de-106">Bu, BT uzmanlarının yüklemeyi gerektiği şekilde kolayca özelleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b99de-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="b99de-107">Bu konuda, IIS 7,0 ' ü Windows Communication Foundation (WCF) ile kullanım için yapılandırma ve hangi bileşenlerin gerekli olduğunu belirleme konusu ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b99de-107">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="b99de-108">En az yükleme: yükleme WAS</span><span class="sxs-lookup"><span data-stu-id="b99de-108">Minimal Installation: Installing WAS</span></span>
 <span data-ttu-id="b99de-109">Tüm IIS 7,0 paketinin en düşük yüklemesi, Windows Işlem etkinleştirme hizmeti 'ni (WAS) yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="b99de-109">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="b99de-110">, Tek başına bir özelliktir ve IIS 7,0 ' den tüm Windows Vista işletim sistemleri (Home Basic, Home Premium, Business ve Ultimate ve Enterprise) için kullanılabilen tek özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b99de-110">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="b99de-111">Denetim Masası ' nda, **Programlar** ' a ve ardından **Programlar ve Özellikler**altında listelenen **Windows özelliklerini aç veya kapat** ' a tıklayın, aşağıdaki çizimde gösterildiği gibi, was bileşeni listede gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b99de-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="b99de-112">![Özellikleri aç veya kapat Iletişim kutusu](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="b99de-112">![Turn Features On or Off Dialog](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="b99de-113">Bu özellik aşağıdaki alt bileşenlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b99de-113">This feature has the following sub-components:</span></span>

- <span data-ttu-id="b99de-114">.NET ortamı</span><span class="sxs-lookup"><span data-stu-id="b99de-114">.NET Environment</span></span>

- <span data-ttu-id="b99de-115">Yapılandırma API 'Leri</span><span class="sxs-lookup"><span data-stu-id="b99de-115">Configuration APIs</span></span>

- <span data-ttu-id="b99de-116">İşlem modeli</span><span class="sxs-lookup"><span data-stu-id="b99de-116">Process Model</span></span>

 <span data-ttu-id="b99de-117">WAS kök düğümünü seçerseniz, yalnızca **Işlem modeli** alt düğümü varsayılan olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b99de-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="b99de-118">Lütfen bu yüklemede, Web sunucusu için destek bulunmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b99de-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="b99de-119">WCF veya ASP.NET uygulamasının çalışmasını sağlamak için **.net ortamı** onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="b99de-119">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="b99de-120">Bu, WCF ve ASP.NET 'in düzgün çalışmasını sağlamak için tüm WAS bileşenlerinin gerekli olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b99de-120">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="b99de-121">Bunlar, bu bileşenlerden herhangi birini yükledikten sonra otomatik olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b99de-121">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="b99de-122">IIS 7,0: varsayılan yükleme</span><span class="sxs-lookup"><span data-stu-id="b99de-122">IIS 7.0: Default Installation</span></span>
 <span data-ttu-id="b99de-123">**Internet Information Services** özelliğini denetleyerek, bazı alt düğümlerden bazıları aşağıdaki çizimde gösterildiği gibi otomatik olarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b99de-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="b99de-124">![IIS 7,0 özellikleri için varsayılan ayarlar](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="b99de-124">![Default settings for IIS 7.0 features](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="b99de-125">Bu, varsayılan IIS 7,0 yüklemesidir.</span><span class="sxs-lookup"><span data-stu-id="b99de-125">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="b99de-126">Bu yüklemeyle, IIS 7,0 kullanarak statik içeriğe (örneğin, HTML sayfaları ve diğer içerikler) hizmet sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b99de-126">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="b99de-127">Ancak, ASP.NET veya CGI uygulamalarını çalıştıramazsınız veya WCF hizmetlerini barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b99de-127">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="b99de-128">IIS 7,0: ASP.NET desteğiyle yükleme</span><span class="sxs-lookup"><span data-stu-id="b99de-128">IIS 7.0: Installation with ASP.NET Support</span></span>
 <span data-ttu-id="b99de-129">IIS 7,0 üzerinde ASP.NET çalışması yapmak için ASP.NET yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b99de-129">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="b99de-130">**ASP.net**denetledikten sonra, ekranınız aşağıdaki şekilde görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="b99de-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="b99de-131">![Gerekli Asp.NET ayarları](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="b99de-131">![Asp.NET required settings](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="b99de-132">Bu, hem WCF hem de ASP.NET uygulamalarının IIS 7,0 ' de çalışması için en düşük ortamdır.</span><span class="sxs-lookup"><span data-stu-id="b99de-132">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="b99de-133">IIS 7,0: IIS 6,0 uyumluluk bileşenleriyle yükleme</span><span class="sxs-lookup"><span data-stu-id="b99de-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>
 <span data-ttu-id="b99de-134">IIS 7,0 ' i Visual Studio 2005 içeren bir sisteme veya IIS 6,0 metatabanı API 'SI kullanan sanal uygulamaları yapılandıran başka bazı Otomasyon betikleri ya da araçlarına (adsutil. vbs gibi) yüklerken IIS 6,0 **Scripting araçları**' nı denetletdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b99de-134">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="b99de-135">Bu, IIS 6,0 **Yönetim uyumluluğun**diğer alt düğümlerini otomatik olarak denetler.</span><span class="sxs-lookup"><span data-stu-id="b99de-135">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="b99de-136">Aşağıdaki çizimde, Bu yapıldıktan sonra ekran gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b99de-136">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="b99de-137">![IIS 6,0 yönetimi uyumluluk ayarları](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="b99de-137">![IIS 6.0 Management Compatibility Settings](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="b99de-138">Bu yüklemeyle, Web 'de bulunan IIS 7,0, ASP.NET ve WCF özelliklerini ve örneklerini kullanmak için gereken her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="b99de-138">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="b99de-139">İstek sınırları</span><span class="sxs-lookup"><span data-stu-id="b99de-139">Request Limits</span></span>
 <span data-ttu-id="b99de-140">IIS 7 ile Windows Vista 'da, ve ayarlarının varsayılan değeri `maxUri` `maxQueryStringSize` değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b99de-140">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="b99de-141">Varsayılan olarak, IIS 7,0 ' de istek filtreleme, 4096 karakterlik bir URL uzunluğu ve bir sorgu dizesi uzunluğu olan 2048 karakter olarak izin verir.</span><span class="sxs-lookup"><span data-stu-id="b99de-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="b99de-142">Bu Varsayılanları değiştirmek için aşağıdaki XML 'i App.config dosyanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b99de-142">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="b99de-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b99de-143">See also</span></span>

- [<span data-ttu-id="b99de-144">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="b99de-144">WAS Activation Architecture</span></span>](was-activation-architecture.md)
- [<span data-ttu-id="b99de-145">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b99de-145">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="b99de-146">Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b99de-146">How to: Install and Configure WCF Activation Components</span></span>](how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="b99de-147">[Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b99de-147">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
