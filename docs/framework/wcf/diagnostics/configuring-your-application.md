---
title: Uygulamanızı Yapılandırma
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 4e19e4d0ecb6bc90402f99dddd280ee1dbcf7ea0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798156"
---
# <a name="configuring-your-application"></a><span data-ttu-id="07d95-102">Uygulamanızı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07d95-102">Configuring Your Application</span></span>
<span data-ttu-id="07d95-103">Windows Communication Foundation (WCF), .NET yapılandırma sistemini kullanır ve hem makine hem de uygulama kapsamında hizmetleri yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="07d95-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="07d95-104">WCF tarafından tanımlanan yapılandırma ayarları, `<system.serviceModel>` bölüm grubunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="07d95-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="07d95-105">Bir WCF hizmetini yapılandırma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="07d95-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="07d95-106">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07d95-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [<span data-ttu-id="07d95-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="07d95-107">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="07d95-108">Uygulama tanımlı yapılandırma ayarları, `<appSettings>` bölüm grubunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="07d95-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="07d95-109">.NET yapılandırma dosyalarındaki uygulama ayarları hakkında daha fazla bilgi için bkz [ \<. AppSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="07d95-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="07d95-110">Yapılandırma düzenleyicisini kullanma</span><span class="sxs-lookup"><span data-stu-id="07d95-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="07d95-111">WCF [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) , yöneticilerin ve geliştiricilerin bir grafik kullanıcı ARABIRIMI kullanarak WCF Hizmetleri için yapılandırma ayarlarını oluşturmalarına ve değiştirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="07d95-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="07d95-112">Bu araçla, WCF bağlamaları, davranışlar, hizmetler ve Tanılamalar için, XML yapılandırma dosyalarını doğrudan düzenlemeden ayarları yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07d95-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="07d95-113">Visual Studio 'da yapılandırma dosyalarını düzenlemeyle</span><span class="sxs-lookup"><span data-stu-id="07d95-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="07d95-114">Visual Studio 'da bir WCF hizmeti projesinin yapılandırma dosyasını düzenlemek için **Çözüm Gezgini** ' de sağ tıklayın ve **WCF yapılandırma bağlamını Düzenle** menü öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="07d95-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="07d95-115">Bu, [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md)başlatır.</span><span class="sxs-lookup"><span data-stu-id="07d95-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07d95-116">Visual Studio 'da bir WCF Web hizmeti projesinin yapılandırma dosyasını **Çözüm Gezgini**' de sağ tıklayarak DÜZENLERSENIZ, **WCF yapılandırma bağlamını Düzenle** bağlam menü öğesinin eksik olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="07d95-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="07d95-117">Bu soruna geçici bir çözüm olarak, **Araçlar** menüsünü ve **WCF hizmeti yapılandırma Düzenleyicisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="07d95-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="07d95-118">Bundan sonra, bir yapılandırma dosyasına sağ tıklayıp **WCF yapılandırma bağlamını Düzenle** menü öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07d95-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d95-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07d95-119">See also</span></span>

- [<span data-ttu-id="07d95-120">Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="07d95-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="07d95-121">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="07d95-121">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="07d95-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="07d95-122">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
