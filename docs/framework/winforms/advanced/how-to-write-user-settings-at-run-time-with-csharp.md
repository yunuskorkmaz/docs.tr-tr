---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma'
description: Save metodunu çağırarak uygulama oturumları arasındaki ayarları değişikliklerle kalıcı hale getirerek, çalışma zamanında C# ile ayarları yazmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904331"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="3e085-103">Nasıl yapılır: çalışma zamanında C ile Kullanıcı ayarlarını yazma\#</span><span class="sxs-lookup"><span data-stu-id="3e085-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="3e085-104">Uygulama kapsamlı olan ayarlar salt okunurdur ve yalnızca tasarım zamanında veya uygulama oturumları arasındaki. config dosyasını değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e085-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="3e085-105">Ancak, kullanıcı kapsamlı olan ayarlar, tıpkı herhangi bir özellik değerini değiştirdiğiniz gibi çalışma zamanında yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e085-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="3e085-106">Yeni değer, uygulama oturumunun süresi boyunca devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="3e085-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="3e085-107">Save metodunu çağırarak uygulama oturumları arasındaki ayarları değişikliklerle kalıcı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e085-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="3e085-108">Nasıl yapılır: çalışma zamanında C ile Kullanıcı ayarlarını yazma ve kalıcı hale getirme\#</span><span class="sxs-lookup"><span data-stu-id="3e085-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="3e085-109">Bu ayara erişin ve bu örnekte gösterildiği gibi yeni bir değer atayın:</span><span class="sxs-lookup"><span data-stu-id="3e085-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="3e085-110">Değişiklikleri uygulama oturumları arasında kalıcı hale getirmek istiyorsanız, bu örnekte gösterildiği gibi Save metodunu çağırın:</span><span class="sxs-lookup"><span data-stu-id="3e085-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="3e085-111">Kullanıcı ayarları, kullanıcının yerel gizli uygulama verileri klasörünün bir alt klasörü içindeki bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3e085-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e085-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e085-112">See also</span></span>

- [<span data-ttu-id="3e085-113">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="3e085-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="3e085-114">Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma</span><span class="sxs-lookup"><span data-stu-id="3e085-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="3e085-115">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e085-115">Application Settings Overview</span></span>](application-settings-overview.md)
