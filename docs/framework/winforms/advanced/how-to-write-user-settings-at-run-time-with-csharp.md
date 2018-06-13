---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: f289b6a6a4a726ffa6bb2c9df99c665e2872e8d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522301"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="2cb56-102">Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma</span><span class="sxs-lookup"><span data-stu-id="2cb56-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="2cb56-103">Uygulama kapsamlı ayarları salt okunurdur ve yalnızca tasarım zamanında veya uygulama oturumları arasında .config dosyasını değiştirmeden tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2cb56-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="2cb56-104">Herhangi bir özelliğin değerini değiştirmek gibi kullanıcı kapsamlı ayarları ancak, çalışma zamanında yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cb56-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="2cb56-105">Yeni değer uygulama oturumu boyunca devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="2cb56-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="2cb56-106">Save yöntemi çağrılarak uygulama oturumları arasında ayarlarında yapılan değişiklikler devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="2cb56-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="2cb56-107">Nasıl yapılır: Yazma ve çalışma zamanında C# ile kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="2cb56-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="2cb56-108">Ayar erişmek ve bu örnekte gösterildiği gibi yeni bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2cb56-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="2cb56-109">Uygulama oturumları arasında ayarlarında yapılan değişiklikler kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi kaydetme yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="2cb56-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="2cb56-110">Kullanıcı ayarları kullanıcının yerel gizli uygulama veri klasörünün bir alt dosyasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2cb56-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb56-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cb56-111">See Also</span></span>  
 [<span data-ttu-id="2cb56-112">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2cb56-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="2cb56-113">Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma</span><span class="sxs-lookup"><span data-stu-id="2cb56-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="2cb56-114">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2cb56-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
