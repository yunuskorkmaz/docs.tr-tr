---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 37330b571553bb5e8f17ffad85faafbcaf19d217
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041280"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="f472f-102">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="f472f-102">WCF Configuration Schema</span></span>
<span data-ttu-id="f472f-103">Windows Communication Foundation (WCF) yapılandırma öğeleri, WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f472f-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="f472f-104">İstemci ve hizmet yapılandırma dosyalarını oluşturmak ve değiştirmek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f472f-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="f472f-105">Yapılandırma dosyaları XML olarak biçimlendirildiğinden, bunları bir metin düzenleyicisi kullanarak el ile düzenlemek istiyorsanız XML ile ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f472f-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="f472f-106">Aksi takdirde, bulunamayan bir XML öğesi etiketi veya özniteliği gibi sorunlar yaşayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f472f-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="f472f-107">Bunun nedeni, XML öğesi etiketlerinin ve özniteliklerin büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="f472f-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="f472f-108">WCF yapılandırma sistemi, <xref:System.Configuration> ad alanını temel alır.</span><span class="sxs-lookup"><span data-stu-id="f472f-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="f472f-109">Bu nedenle, uygulamanızın güvenliğini ve yapılandırmasını artırmak için yapılandırma kilitleme, <xref:System.Configuration> şifreleme ve birleştirme gibi ad alanı tarafından sunulan tüm standart özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f472f-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="f472f-110">Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="f472f-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="f472f-111">Yapılandırma bilgilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="f472f-111">Encrypting Configuration Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="f472f-112">Yapılandırma ayarlarını kilitleme</span><span class="sxs-lookup"><span data-stu-id="f472f-112">Locking Configuration Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="f472f-113">Bu bölüm, her yapılandırma öğesinin olası tüm değerlerini ve diğer WCF yapılandırma öğeleriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f472f-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="f472f-114">Aşağıdaki haritada WCF yapılandırma şeması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f472f-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![WCF yapılandırma şemasını gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> <span data-ttu-id="f472f-116">Olası güvenlik tehditlerini engellemek için uygulama yapılandırma dosyalarınızda (App. config) WCF yapılandırma bölümlerini uygun Access Control listeleriyle (ACL) korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f472f-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="f472f-117">Örneğin, yalnızca uygun kişilerin uygulama bağlamalarında güvenlik ayarlarına veya bir hizmetin yapılandırma dosyasının hizmet modeli bölümüne erişebildiğinizden veya değiştirebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f472f-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f472f-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f472f-118">In This Section</span></span>  
 [<span data-ttu-id="f472f-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f472f-119">\<system.serviceModel></span></span>](system-servicemodel.md)  
 <span data-ttu-id="f472f-120">Açıklayan `ServiceModel` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f472f-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="f472f-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f472f-121">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)  
 <span data-ttu-id="f472f-122">SMSvcHost. exe aracını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f472f-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="f472f-123">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="f472f-123">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
 <span data-ttu-id="f472f-124">Gibi serileştiriciler <xref:System.Runtime.Serialization.DataContractSerializer>kullanılırken seçenekleri ayarlamak için en üst düzey öğe.</span><span class="sxs-lookup"><span data-stu-id="f472f-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f472f-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f472f-125">Related Sections</span></span>  
 [<span data-ttu-id="f472f-126">Windows Communication Foundation uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f472f-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="f472f-127">WCF Hizmetleri ve istemcilerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f472f-127">Describes how to configure WCF services and clients.</span></span>
