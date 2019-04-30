---
title: 'Nasıl yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 264fa9706f9255d7324cad6d02c36cc424e28995
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778839"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="27e34-102">Nasıl yapılır: Çalışma zamanında C ile kullanıcı ayarlarını yazma\#</span><span class="sxs-lookup"><span data-stu-id="27e34-102">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="27e34-103">Uygulama kapsamlı ayarlar salt okunurdur ve yalnızca tasarım zamanında ya da uygulama oturumları arasında .config dosyasını değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="27e34-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="27e34-104">Herhangi bir özelliğin değerini değiştirmek gibi kullanıcı kapsamlı ayarları ancak çalışma zamanında yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="27e34-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="27e34-105">Yeni değer, uygulama oturum süresi boyunca devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="27e34-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="27e34-106">Ayarları kaydetme yöntemini çağırarak uygulama oturumları arasında yapılan değişiklikleri kalıcı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27e34-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="27e34-107">Nasıl yapılır: Yazma ve çalışma zamanında C ile kullanıcı ayarlarını kalıcı yapma\#</span><span class="sxs-lookup"><span data-stu-id="27e34-107">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="27e34-108">Ayar erişmek ve bu örnekte gösterildiği gibi yeni bir değer atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27e34-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="27e34-109">Uygulama oturumları arasında ayarlarındaki değişiklikler kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi Save metoduna çağrı:</span><span class="sxs-lookup"><span data-stu-id="27e34-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="27e34-110">Kullanıcı ayarları kullanıcının yerel gizli uygulama veri klasörünün bir alt dosyasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="27e34-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e34-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27e34-111">See also</span></span>

- [<span data-ttu-id="27e34-112">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="27e34-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="27e34-113">Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#</span><span class="sxs-lookup"><span data-stu-id="27e34-113">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="27e34-114">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="27e34-114">Application Settings Overview</span></span>](application-settings-overview.md)
