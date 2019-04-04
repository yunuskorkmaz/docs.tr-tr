---
title: WCF Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: baea1e49bce10054530afa5b6f282023d5ceb981
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463338"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="48aa2-102">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="48aa2-102">WCF Configuration Schema</span></span>
<span data-ttu-id="48aa2-103">Windows Communication Foundation (WCF) yapılandırma öğeleri WCF hizmet ve istemci uygulamaları yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48aa2-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="48aa2-104">Kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturup istemciler ve hizmetler için yapılandırma dosyalarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48aa2-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="48aa2-105">Yapılandırma dosyaları XML olarak biçimlendirilir olduğundan, bir metin düzenleyicisi kullanarak bunları el ile düzenlemek istiyorsanız, XML'e alışık olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48aa2-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="48aa2-106">Aksi takdirde içine sorunları unfound XML öğesi etiketi veya öznitelik gibi çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="48aa2-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="48aa2-107">Bunun nedeni, XML öğesi etiketleri ve öznitelikleri duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="48aa2-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="48aa2-108">WCF yapılandırma sistemi dayanır <xref:System.Configuration> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="48aa2-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="48aa2-109">Bu nedenle, tarafından sağlanan tüm standart özellikler kullanabilirsiniz <xref:System.Configuration> kilitleme, şifreleme ve uygulamanız ve yapılandırmasına güvenliğini artırmak için birleştirme yapılandırması gibi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="48aa2-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="48aa2-110">Bu kavramlarla ilgili daha fazla bilgi için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="48aa2-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="48aa2-111">Şifreleme yapılandırma bilgileri</span><span class="sxs-lookup"><span data-stu-id="48aa2-111">Encrypting Configuration Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="48aa2-112">Kilitleme yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="48aa2-112">Locking Configuration Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="48aa2-113">Bu bölümde, her bir yapılandırma öğesinin tüm olası değerlerini ve diğer WCF yapılandırma öğeleri ile nasıl etkileşim kurduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="48aa2-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="48aa2-114">Aşağıdaki harita WCF yapılandırma şeması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="48aa2-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![WCF yapılandırma şeması gösteren diyagram.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  <span data-ttu-id="48aa2-116">WCF yapılandırma bölümlerini, uygulama yapılandırma dosyalarında (app.config) ile uygun erişim denetim listeleri (tüm olası güvenlik tehditlerini önlemek için ACL) korur.</span><span class="sxs-lookup"><span data-stu-id="48aa2-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="48aa2-117">Örneğin, yalnızca uygun kişilerle erişme veya uygulama bağlamaları veya hizmet modeli bölümü yapılandırma dosyasının bir hizmet için güvenlik ayarlarını değiştirme emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48aa2-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48aa2-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="48aa2-118">In This Section</span></span>  
 [<span data-ttu-id="48aa2-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="48aa2-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="48aa2-120">Açıklayan `ServiceModel` öğesi.</span><span class="sxs-lookup"><span data-stu-id="48aa2-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="48aa2-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="48aa2-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="48aa2-122">SMSvcHost.exe aracı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="48aa2-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="48aa2-123">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="48aa2-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="48aa2-124">Seri hale getiricileri genişletme gibi kullanırken seçenekleri ayarlamak için üst düzey öğe <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="48aa2-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="48aa2-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="48aa2-125">Related Sections</span></span>  
 [<span data-ttu-id="48aa2-126">Windows Communication Foundation uygulamaları için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48aa2-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="48aa2-127">WCF hizmetleri ve istemcilerin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="48aa2-127">Describes how to configure WCF services and clients.</span></span>
