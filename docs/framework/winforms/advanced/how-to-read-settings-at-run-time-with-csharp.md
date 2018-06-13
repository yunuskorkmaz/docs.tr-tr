---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521020"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="2898e-102">Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma</span><span class="sxs-lookup"><span data-stu-id="2898e-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="2898e-103">Özellikleri nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı hem de kullanıcı kapsamlı ayarlarını okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2898e-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="2898e-104">Özellikleri nesnesi Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarlar kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2898e-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="2898e-105">Çalışma zamanında C# ile ayarları okunamıyor</span><span class="sxs-lookup"><span data-stu-id="2898e-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="2898e-106">Uygun ayarı Properties.Settings.Default üye üzerinden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2898e-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="2898e-107">Aşağıdaki örnek adlı bir ayarı atama gösterilmiştir `myColor` BackColor özelliği.</span><span class="sxs-lookup"><span data-stu-id="2898e-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="2898e-108">Adlı bir ayar içeren ayarlar dosyası önceden oluşturulmuş gerekir `myColor` türü `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="2898e-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="2898e-109">Ayarlar dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: tasarım zamanında yeni ayar oluşturun](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="2898e-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2898e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2898e-110">See Also</span></span>  
 [<span data-ttu-id="2898e-111">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="2898e-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="2898e-112">Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma</span><span class="sxs-lookup"><span data-stu-id="2898e-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="2898e-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2898e-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
