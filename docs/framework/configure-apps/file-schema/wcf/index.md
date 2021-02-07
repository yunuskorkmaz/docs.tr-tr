---
description: 'Daha fazla bilgi edinin: WCF yapılandırma şeması'
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 31307fd299cc1e0b63d92b43b33aabafa28858f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725772"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="d3ac4-103">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="d3ac4-103">WCF Configuration Schema</span></span>

<span data-ttu-id="d3ac4-104">Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-104">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="d3ac4-105">İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-105">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="d3ac4-106">Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-106">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="d3ac4-107">Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-107">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="d3ac4-108">Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-108">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="d3ac4-109">WCF yapılandırma sistemi, ad alanını temel alır <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="d3ac4-109">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="d3ac4-110">Bu nedenle, <xref:System.Configuration> uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-110">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="d3ac4-111">Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-111">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="d3ac4-112">[Yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3ac4-112">[Encrypting Configuration Information](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="d3ac4-113">[Yapılandırma ayarlarını kilitleme](/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3ac4-113">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="d3ac4-114">Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-114">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="d3ac4-115">Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d3ac4-115">The following map illustrates the WCF configuration schema:</span></span>

:::image type="content" source="./media/index/windows-communication-foundation-configuration-schema.gif" alt-text="WCF yapılandırma şemasını gösteren diyagram." lightbox="./media/index/windows-communication-foundation-configuration-schema.gif":::
  
> [!CAUTION]
> <span data-ttu-id="d3ac4-117">Olası güvenlik tehditlerini engellemek için, uygulama yapılandırma dosyalarınızda (app.config) uygun Access Control listeleriyle (ACL) WCF yapılandırma bölümlerini koruyun.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-117">Protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span> <span data-ttu-id="d3ac4-118">Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarını veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümünü erişebileceği veya bu ayarları değiştire, emin olun.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-118">For example, make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3ac4-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d3ac4-119">In This Section</span></span>  

 [\<system.serviceModel>](system-servicemodel.md)  
 <span data-ttu-id="d3ac4-120">Açıklayan `ServiceModel` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-120">Describes the `ServiceModel` element.</span></span>  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 <span data-ttu-id="d3ac4-121">SMSvcHost.exe aracını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-121">Configures the SMSvcHost.exe tool.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 <span data-ttu-id="d3ac4-122">Gibi serileştiriciler kullanılırken seçenekleri ayarlamak için en üst düzey öğe <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d3ac4-122">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3ac4-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d3ac4-123">Related Sections</span></span>  

 [<span data-ttu-id="d3ac4-124">Windows Communication Foundation uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d3ac4-124">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="d3ac4-125">WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3ac4-125">Describes how to configure WCF services and clients.</span></span>
