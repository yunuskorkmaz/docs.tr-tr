---
title: "Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c23fd88d33ff4ca480c435f2058f4c568320578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="493cd-102">Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma</span><span class="sxs-lookup"><span data-stu-id="493cd-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="493cd-103">Özellikleri nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı hem de kullanıcı kapsamlı ayarlarını okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="493cd-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="493cd-104">Özellikleri nesnesi Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarlar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="493cd-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="493cd-105">Çalışma zamanında C# ile ayarları okunamıyor</span><span class="sxs-lookup"><span data-stu-id="493cd-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="493cd-106">Uygun ayarı Properties.Settings.Default üye üzerinden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="493cd-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="493cd-107">Aşağıdaki örnek adlı bir ayarı atama gösterilmiştir `myColor` BackColor özelliği.</span><span class="sxs-lookup"><span data-stu-id="493cd-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="493cd-108">Adlı bir ayar içeren ayarlar dosyası önceden oluşturulmuş gerekir `myColor` türü `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="493cd-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="493cd-109">Ayarlar dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: tasarım zamanında yeni ayar oluşturun](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="493cd-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="493cd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="493cd-110">See Also</span></span>  
 [<span data-ttu-id="493cd-111">Uygulama ayarları ve kullanıcı ayarlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="493cd-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="493cd-112">Nasıl yapılır: Çalışma zamanında C# ile kullanıcı ayarlarını yazma</span><span class="sxs-lookup"><span data-stu-id="493cd-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="493cd-113">Uygulama ayarlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="493cd-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
