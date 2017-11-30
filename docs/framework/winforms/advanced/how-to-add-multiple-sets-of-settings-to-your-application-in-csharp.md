---
title: "Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec541a8f83990eec79226be7fb4880ef8dda639d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="78af2-102">Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="78af2-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="78af2-103">Bazı durumlarda, bir uygulamada birden çok ayar kümesi sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78af2-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="78af2-104">Belirli bir ayar grubu sık değiştirmek için beklenirken bir uygulama geliştiriyorsanız, örneğin, diğer ayarları etkilenmemesini değiştirmeden dosyası tümden değiştirilebilir böylece tüm tek bir dosyaya ayırmak akıllıca olabilir.</span><span class="sxs-lookup"><span data-stu-id="78af2-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="78af2-105">Visual Studio projenize birden çok ayar kümesi eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="78af2-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="78af2-106">Ek ayarları kümesi Properties.Settings nesnesi erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="78af2-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="78af2-107">Ek bir ayar kümesini uygulamanıza eklemek için</span><span class="sxs-lookup"><span data-stu-id="78af2-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="78af2-108">Gelen **proje** menüsünde seçin **Yeni Öğe Ekle**.</span><span class="sxs-lookup"><span data-stu-id="78af2-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="78af2-109">**Yeni Öğe Ekle** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="78af2-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="78af2-110">İçinde **Yeni Öğe Ekle** iletişim kutusunda **ayarları dosyası**, dosya için bir ad yazın ve tıklayın **Ekle** çözümünüz için yeni bir ayarları dosyası eklemek için.</span><span class="sxs-lookup"><span data-stu-id="78af2-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="78af2-111">İçinde **Çözüm Gezgini**, yeni ayarları dosyasına sürükleyin **özellikleri** klasör.</span><span class="sxs-lookup"><span data-stu-id="78af2-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="78af2-112">Bu yeni ayarlarınızı kodda kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="78af2-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="78af2-113">Ekleyin ve diğer ayarları dosyası gibi bu dosyada ayarları kullanın.</span><span class="sxs-lookup"><span data-stu-id="78af2-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="78af2-114">Bu ayar grubu Properties.Settings nesnesi aracılığıyla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="78af2-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78af2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78af2-115">See Also</span></span>  
 [<span data-ttu-id="78af2-116">Uygulama ayarları ve kullanıcı ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="78af2-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="78af2-117">Uygulama ayarlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="78af2-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
