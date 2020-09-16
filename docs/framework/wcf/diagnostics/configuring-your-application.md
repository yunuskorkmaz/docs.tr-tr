---
title: Uygulamanızı Yapılandırma
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 04ddce4755ce30b7d46c3bd54024af08361d96ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536087"
---
# <a name="configuring-your-application"></a><span data-ttu-id="4e264-102">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e264-102">Configuring Your Application</span></span>
<span data-ttu-id="4e264-103">Windows Communication Foundation (WCF), .NET yapılandırma sistemini kullanır ve hem makine hem de uygulama kapsamında hizmetleri yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e264-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="4e264-104">WCF tarafından tanımlanan yapılandırma ayarları, `<system.serviceModel>` bölüm grubunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e264-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="4e264-105">Bir WCF hizmetini yapılandırma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="4e264-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="4e264-106">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e264-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="4e264-107">Uygulama tanımlı yapılandırma ayarları, `<appSettings>` bölüm grubunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4e264-107">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="4e264-108">.NET yapılandırma dosyalarındaki uygulama ayarları hakkında daha fazla bilgi için bkz [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)) ..</span><span class="sxs-lookup"><span data-stu-id="4e264-108">For more information about application settings in .NET configuration files, see [\<appSettings>](/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="4e264-109">Yapılandırma düzenleyicisini kullanma</span><span class="sxs-lookup"><span data-stu-id="4e264-109">Using the Configuration Editor</span></span>  
 <span data-ttu-id="4e264-110">WCF [yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) , yöneticilerin ve geliştiricilerin bir grafik kullanıcı ARABIRIMI kullanarak WCF Hizmetleri için yapılandırma ayarlarını oluşturmalarına ve değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4e264-110">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="4e264-111">Bu araçla, WCF bağlamaları, davranışlar, hizmetler ve Tanılamalar için, XML yapılandırma dosyalarını doğrudan düzenlemeden ayarları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e264-111">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="4e264-112">Visual Studio 'da yapılandırma dosyalarını düzenlemeyle</span><span class="sxs-lookup"><span data-stu-id="4e264-112">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="4e264-113">Visual Studio 'da bir WCF hizmeti projesinin yapılandırma dosyasını düzenlemek için **Çözüm Gezgini** ' de sağ tıklayın ve **WCF yapılandırma bağlamını Düzenle** menü öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="4e264-113">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="4e264-114">Bu, [yapılandırma Düzenleyicisi aracını (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)başlatır.</span><span class="sxs-lookup"><span data-stu-id="4e264-114">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e264-115">Visual Studio 'da bir WCF Web hizmeti projesinin yapılandırma dosyasını **Çözüm Gezgini**' de sağ tıklayarak DÜZENLERSENIZ, **WCF yapılandırma bağlamını Düzenle** bağlam menü öğesinin eksik olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4e264-115">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="4e264-116">Bu soruna geçici bir çözüm olarak, **Araçlar** menüsünü ve **WCF hizmeti yapılandırma Düzenleyicisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="4e264-116">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="4e264-117">Bundan sonra, bir yapılandırma dosyasına sağ tıklayıp **WCF yapılandırma bağlamını Düzenle** menü öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e264-117">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e264-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e264-118">See also</span></span>

- [<span data-ttu-id="4e264-119">Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="4e264-119">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="4e264-120">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e264-120">Configuring Services</span></span>](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
