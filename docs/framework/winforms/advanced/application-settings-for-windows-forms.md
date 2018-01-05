---
title: "Windows Forms için Uygulama Ayarları"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ClientApplicationSettings
helpviewer_keywords:
- application settings [Windows Forms]
- Windows Forms, application settings
ms.assetid: 64090a34-8556-4904-8ea0-20efe9f8c886
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63248009497152a41a6313a50ed6e7544ac62cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-for-windows-forms"></a><span data-ttu-id="7d6a7-102">Windows Forms için Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="7d6a7-102">Application Settings for Windows Forms</span></span>
<span data-ttu-id="7d6a7-103">Windows Forms uygulamaları ayarlarını özelliğidir oluşturmak, depolamak ve özel uygulama ve istemci üzerindeki kullanıcı tercihlerini korumak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-103">The Applications Settings feature of Windows Forms makes it easy to create, store, and maintain custom application and user preferences on the client.</span></span> <span data-ttu-id="7d6a7-104">Uygulama ayarları, yalnızca veritabanı bağlantı dizelerini gibi uygulama verilerini, aynı zamanda araç çubuğu konumları gibi kullanıcıya özgü verileri depolamak ve en son listeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-104">With Application Settings, you can store not only application data such as database connection strings, but also user-specific data, such as toolbar positions and most-recently used lists.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d6a7-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7d6a7-105">In This Section</span></span>  
 [<span data-ttu-id="7d6a7-106">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d6a7-106">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)  
 <span data-ttu-id="7d6a7-107">Uygulamanız ve kullanıcılarınızın adına ayarları veri depolamak ve oluşturmak nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-107">Discusses how to create and store settings data on behalf of your application and your users.</span></span>  
  
 [<span data-ttu-id="7d6a7-108">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="7d6a7-108">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)  
 <span data-ttu-id="7d6a7-109">Uygulama ayarları nasıl çalışır özellik açıklar ve mimarisinin gruplandırılmış ayarları ve ayarları anahtarları gibi gelişmiş özellikler araştırır.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-109">Describes how the Application Settings feature works, and explores advanced features of the architecture such as grouped settings and settings keys.</span></span>  
  
 [<span data-ttu-id="7d6a7-110">Uygulama Ayarları Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="7d6a7-110">Application Settings Attributes</span></span>](~/docs/framework/winforms/advanced/application-settings-attributes.md)  
 <span data-ttu-id="7d6a7-111">Listeler ve bir uygulama ayarları sarmalayıcı sınıfı veya ayarları özelliklerine uygulanan öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-111">Lists and describes the attributes that can be applied to an application settings wrapper class or its settings properties.</span></span>  
  
 [<span data-ttu-id="7d6a7-112">Özel Denetimler için Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="7d6a7-112">Application Settings for Custom Controls</span></span>](~/docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 <span data-ttu-id="7d6a7-113">Özel denetimler üçüncü taraf uygulamalarda barındırıldığında uygulama ayarlarını sürdürmek vermek için yapılması gerekir açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-113">Discusses what must be done to give your custom controls the ability to persist application settings when hosted in third-party applications.</span></span>  
  
 [<span data-ttu-id="7d6a7-114">Nasıl yapılır: Uygulama Ayarları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d6a7-114">How to: Create Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-create-application-settings.md)  
 <span data-ttu-id="7d6a7-115">Uygulama oturumları arasında kalıcı yeni uygulama ayarları oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-115">Demonstrates creating new application settings that are persisted between application sessions.</span></span>  
  
 [<span data-ttu-id="7d6a7-116">Nasıl yapılır: Uygulama Ayarlarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="7d6a7-116">How to: Validate Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 <span data-ttu-id="7d6a7-117">Kalıcı yapılan önce doğrulama uygulama ayarlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-117">Demonstrates validating application settings before they are persisted.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="7d6a7-118">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="7d6a7-118">Related topics</span></span>

<span data-ttu-id="7d6a7-119">[Windows Forms yapılandırma bölümü](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span><span class="sxs-lookup"><span data-stu-id="7d6a7-119">[Windows Forms Configuration Section](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span></span>  
<span data-ttu-id="7d6a7-120">Belgeleri Windows Forms ile .NET Framework 4.7 başlangıç uygulaması yüksek DPI etkinleştirmek için ayarlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-120">Documents the settings to enable High DPI support in Windows Forms Application starting with the .NET Framework 4.7.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d6a7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6a7-121">See also</span></span>  
  
[<span data-ttu-id="7d6a7-122">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7d6a7-122">Windows Forms</span></span>](../index.md)
