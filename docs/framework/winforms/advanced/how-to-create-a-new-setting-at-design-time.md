---
title: "Nasıl Yapılır: Tasarım Zamanında Yeni Ayar Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="9e4ce-102">Nasıl Yapılır: Tasarım Zamanında Yeni Ayar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e4ce-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="9e4ce-103">Tasarım zamanında yeni bir ayar ayarları Tasarımcısını kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="9e4ce-104">Ayarları Tasarımcısı yeni ayarları oluşturur ve bu ayarlar için özellikleri belirtin olanak tanıyan bir kılavuz stili arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="9e4ce-105">Ad, değer, türü ve yeni ayarlarınızı kapsamın belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="9e4ce-106">Bir ayar oluşturulduktan sonra kodda erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="9e4ce-107">C# tasarım zamanında yeni bir ayar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9e4ce-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="9e4ce-108">İçinde **Çözüm Gezgini**, genişletin **özellikleri** projenizin düğümü.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="9e4ce-109">Yeni bir ayar eklemek istediğiniz .settings dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="9e4ce-110">Bu dosya için varsayılan Settings.settings adıdır.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="9e4ce-111">Ayarları Tasarımcısı'nda adını, değeri, türü ve ayarınız kapsamın ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="9e4ce-112">Her satırda tek bir ayar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="9e4ce-113">Visual Basic'te tasarım zamanında yeni bir ayar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9e4ce-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="9e4ce-114">İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="9e4ce-115">İçinde **özellikleri** sayfasında, **ayarları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="9e4ce-116">Ayarları Tasarımcısı'nda adını, değeri, türü ve ayarınız kapsamın ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="9e4ce-117">Her satırda tek bir ayar temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4ce-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e4ce-118">See Also</span></span>  
 [<span data-ttu-id="9e4ce-119">Uygulama ayarları ve kullanıcı ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="9e4ce-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="9e4ce-120">Uygulama ayarlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="9e4ce-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="9e4ce-121">Nasıl yapılır: tasarım zamanında mevcut bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="9e4ce-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
