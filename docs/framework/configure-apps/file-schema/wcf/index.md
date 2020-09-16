---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 160be2ea43d1530cdb2ccd3de1f9e6a2e4d0aca3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536398"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="8e518-102">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="8e518-102">WCF Configuration Schema</span></span>
<span data-ttu-id="8e518-103">Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e518-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="8e518-104">İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e518-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="8e518-105">Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e518-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="8e518-106">Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e518-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="8e518-107">Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="8e518-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="8e518-108">WCF yapılandırma sistemi, ad alanını temel alır <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="8e518-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="8e518-109">Bu nedenle, <xref:System.Configuration> uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e518-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="8e518-110">Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="8e518-110">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="8e518-111">[Yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e518-111">[Encrypting Configuration Information](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="8e518-112">[Yapılandırma ayarlarını kilitleme](/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8e518-112">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="8e518-113">Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e518-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="8e518-114">Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8e518-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![WCF yapılandırma şemasını gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> <span data-ttu-id="8e518-116">Olası güvenlik tehditlerini engellemek için, uygulama yapılandırma dosyalarınızda (app.config) uygun Access Control listeleriyle (ACL) WCF yapılandırma bölümlerini korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e518-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="8e518-117">Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarına veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümüne erişebildiğinizden veya değiştirebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e518-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8e518-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8e518-118">In This Section</span></span>  
 [\<system.serviceModel>](system-servicemodel.md)  
 <span data-ttu-id="8e518-119">Açıklayan `ServiceModel` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8e518-119">Describes the `ServiceModel` element.</span></span>  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 <span data-ttu-id="8e518-120">SMSvcHost.exe aracını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8e518-120">Configures the SMSvcHost.exe tool.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 <span data-ttu-id="8e518-121">Gibi serileştiriciler kullanılırken seçenekleri ayarlamak için en üst düzey öğe <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8e518-121">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e518-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e518-122">Related Sections</span></span>  
 [<span data-ttu-id="8e518-123">Windows Communication Foundation uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8e518-123">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="8e518-124">WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e518-124">Describes how to configure WCF services and clients.</span></span>
