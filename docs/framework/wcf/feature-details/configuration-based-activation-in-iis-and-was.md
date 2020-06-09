---
title: IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 5e1672f4dd67950178c95d3e043e16072fcd0ef4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593587"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="70a65-102">IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="70a65-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="70a65-103">Normal olarak, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında bir Windows Communication Foundation (WCF) hizmeti barındırdığında bir. svc dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70a65-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="70a65-104">. Svc dosyası, hizmetin adını ve isteğe bağlı bir özel hizmet ana bilgisayar fabrikası içerir.</span><span class="sxs-lookup"><span data-stu-id="70a65-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="70a65-105">Bu ek dosya yönetilebilirlik ek yükü ekler.</span><span class="sxs-lookup"><span data-stu-id="70a65-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="70a65-106">Yapılandırma tabanlı etkinleştirme özelliği, gereksinimi bir. svc dosyasına ve bu nedenle ilişkili ek yüke karşı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="70a65-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="70a65-107">Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="70a65-107">Configuration-Based Activation</span></span>

<span data-ttu-id="70a65-108">Yapılandırma tabanlı etkinleştirme,. svc dosyasına yerleştirilmesi için kullanılan meta verileri alır ve Web. config dosyasına koyar.</span><span class="sxs-lookup"><span data-stu-id="70a65-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="70a65-109"><`serviceHostingEnvironment`> öğesi içinde <bir `serviceActivations`> öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="70a65-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="70a65-110"><`serviceActivations`> öğesi içinde, bir veya daha fazla <`add`> öğesi, her barındırılan hizmet için bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="70a65-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="70a65-111"><`add`> öğesi, hizmet ve hizmet türü ya da hizmet ana bilgisayar fabrikası için göreli adresi ayarlamanıza olanak sağlayan öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="70a65-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="70a65-112">Aşağıdaki yapılandırma örnek kodu, bu bölümün nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70a65-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="70a65-113">Her <`add`> öğesi bir hizmet veya bir fabrika özniteliği belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="70a65-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="70a65-114">Hem Service hem de Factory özniteliklerinin belirtilmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="70a65-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="70a65-115">Web. config dosyasında, hizmet kaynak kodunu uygulamanın App_Code dizinine veya uygulamanın bin dizinine karmaşık bir derlemeye yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70a65-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="70a65-116">Yapılandırma tabanlı etkinleştirme kullanılırken,. svc dosyalarında satır içi kod desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="70a65-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="70a65-117">`relativeAddress`Öznitelik, " \<sub-directory> /Service.exe" veya "~/ \< Sub-Directory/Service. svc" gibi göreli bir adrese ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70a65-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="70a65-118">WCF ile ilişkili bilinen bir uzantısı olmayan göreli bir adresi kaydettiğinizde bir yapılandırma özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="70a65-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="70a65-119">Belirtilen göreli adres, sanal uygulamanın köküne göredir.</span><span class="sxs-lookup"><span data-stu-id="70a65-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="70a65-120">Yapılandırma hiyerarşik modeli nedeniyle, makine ve site düzeyindeki kayıtlı göreli adresler sanal uygulamalar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="70a65-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="70a65-121">Bir yapılandırma dosyasındaki kayıtlar, bir. svc,. xamlx,. xoml veya başka bir dosyanın ayarlarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="70a65-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="70a65-122">IIS/WAS 'a gönderilen URI içindeki herhangi bir ' \ ' (ters eğik çizgi), otomatik olarak bir '/' (eğik çizgi) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="70a65-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="70a65-123">' \ ' İçeren bir göreli adres eklenirse ve IIS 'yi göreli adresi kullanan bir URI gönderirseniz, ters eğik çizgi eğik çizgiye dönüştürülür ve IIS onunla ilgili adresle eşleşemez.</span><span class="sxs-lookup"><span data-stu-id="70a65-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="70a65-124">IIS, hiçbir eşleşme bulunamadığını belirten izleme bilgilerini gönderir.</span><span class="sxs-lookup"><span data-stu-id="70a65-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="70a65-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70a65-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="70a65-126">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="70a65-126">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="70a65-127">İş Akışı Hizmetlerini Barındırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="70a65-127">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="70a65-128">[Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="70a65-128">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
