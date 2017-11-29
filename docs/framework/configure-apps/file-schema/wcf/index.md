---
title: "WCF Yapılandırma Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05aeeea7d10c012804fe083890bcc8516aa8c8bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="24079-102">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="24079-102">WCF Configuration Schema</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="24079-103">yapılandırma öğeleri etkinleştirmek, yapılandırmak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet ve istemci uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="24079-103"> configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="24079-104">Kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturmak ve istemciler ve hizmetler için yapılandırma dosyaları değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="24079-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="24079-105">Yapılandırma dosyaları XML olarak biçimlendirilir olduğundan, el ile bir metin düzenleyicisi kullanarak bunları düzenlemek istiyorsanız XML ile bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24079-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="24079-106">Aksi halde, bir sınıfı XML öğesi etiketi veya öznitelik gibi sorunları içine çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="24079-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="24079-107">Bunun nedeni, XML öğesi etiketleri ve öznitelikleri küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="24079-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="24079-108">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Yapılandırma sistemi temel <xref:System.Configuration> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="24079-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="24079-109">Bu nedenle, tarafından sağlanan tüm standart özellikleri kullanabilirsiniz <xref:System.Configuration> kilitleme, şifreleme ve uygulamanızı ve yapılandırmasıyla güvenliğini artırmak için birleştirme yapılandırması gibi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="24079-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="24079-110">Bu kavramlarla ilgili daha fazla bilgi için aşağıdaki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="24079-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="24079-111">Yapılandırma bilgilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="24079-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="24079-112">Yapılandırma ayarlarını kilitleme</span><span class="sxs-lookup"><span data-stu-id="24079-112">Locking Configuration Settings</span></span>](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="24079-113">Bu bölümde her yapılandırma öğesinin tüm olası değerler ve diğer WCF yapılandırma öğeleri ile nasıl etkileşim kurduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="24079-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="24079-114">Aşağıdaki harita WCF yapılandırma şeması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24079-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="24079-115">![WCF yapılandırma şeması](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="24079-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="24079-116">Korumanız gerekir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] yapılandırma bölümlerinin, uygulama yapılandırma dosyaları (app.config) ile ilgili erişim denetim listeleri (tüm olası güvenlik tehditlerini önlemek için ACL).</span><span class="sxs-lookup"><span data-stu-id="24079-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="24079-117">Örneğin, yalnızca uygun kişilerin erişmek veya uygulama bağlamaları ya da hizmet modeli bölümü yapılandırma dosyasının bir hizmet için güvenlik ayarlarını değiştirme emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24079-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24079-118">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="24079-118">In This Section</span></span>  
 [<span data-ttu-id="24079-119">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="24079-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="24079-120">Açıklayan `ServiceModel` öğesi.</span><span class="sxs-lookup"><span data-stu-id="24079-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="24079-121">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="24079-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="24079-122">SMSvcHost.exe aracı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="24079-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="24079-123">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="24079-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="24079-124">Ayar seçenekleri serileştiricileri gibi kullanırken en üst düzey öğesi <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="24079-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="24079-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="24079-125">Related Sections</span></span>  
 [<span data-ttu-id="24079-126">Windows Communication Foundation uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24079-126">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 <span data-ttu-id="24079-127">Nasıl yapılandırılacağını açıklar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmetler ve istemcileri.</span><span class="sxs-lookup"><span data-stu-id="24079-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
