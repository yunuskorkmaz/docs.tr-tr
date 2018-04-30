---
title: Uygulamanızı Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 170583239ed357904e723aebdaef9809938b5123
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-your-application"></a><span data-ttu-id="2aa4a-102">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2aa4a-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2aa4a-103"> .NET yapılandırma sistemini kullanır ve her iki makine ve uygulama kapsamda hizmetlerini yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="2aa4a-104">Yapılandırma ayarları tarafından tanımlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bulunan `<system.serviceModel>` bölüm grubu.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="2aa4a-105">Nasıl yapılandırılacağı hakkında daha fazla bilgi için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="2aa4a-105">For more information about how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2aa4a-106">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2aa4a-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="2aa4a-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2aa4a-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="2aa4a-108">Uygulama tanımlı yapılandırma ayarları tanımlanmış `<appSettings>` bölüm grubu.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="2aa4a-109">.NET yapılandırma dosyalarında uygulama ayarları hakkında daha fazla bilgi için bkz: [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="2aa4a-109">For more information about application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="2aa4a-110">Yapılandırma Düzenleyicisi'ni kullanarak</span><span class="sxs-lookup"><span data-stu-id="2aa4a-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="2aa4a-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) Yöneticiler ve geliştiriciler oluşturmak ve yapılandırma ayarlarını değiştirmek izin veren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir grafik kullanıcı arabirimini kullanarak hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="2aa4a-112">Bu araçla ayarlarını yönetebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları, davranışları, hizmetleri ve XML yapılandırma dosyalarını doğrudan düzenleyerek olmadan tanılama.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="2aa4a-113">Visual Studio'da yapılandırma dosyalarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="2aa4a-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="2aa4a-114">Yapılandırma dosyasını düzenlemek için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet Visual Studio projesi, sağ tıklayın, **Çözüm Gezgini** ve **Düzenle WCF yapılandırma** bağlam menüsü öğesini.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="2aa4a-115">Bu başlatır [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2aa4a-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2aa4a-116">Yapılandırma dosyası düzenlerseniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Visual Studio'da Web hizmeti projesi içinde tıklanarak **Çözüm Gezgini**, dikkat **Düzenle WCF yapılandırma** bağlam menüsü öğesini eksik.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="2aa4a-117">Geçici çözüm bu sorunu tıklatın **Araçları** menüsünde ve seçin **WCF Hizmeti Yapılandırma Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="2aa4a-118">Bundan sonra bir yapılandırma dosyasına sağ tıklayın ve kullanmak **Düzenle WCF yapılandırma** bağlam menüsü öğesini.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa4a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2aa4a-119">See Also</span></span>  
 [<span data-ttu-id="2aa4a-120">Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="2aa4a-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="2aa4a-121">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2aa4a-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="2aa4a-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2aa4a-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
