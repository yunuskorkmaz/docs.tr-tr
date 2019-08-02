---
title: 'Nasıl yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710221"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="7a28f-102">Nasıl yapılır: Çalışma zamanında C Ile ayarları okuma\#</span><span class="sxs-lookup"><span data-stu-id="7a28f-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="7a28f-103">Özellikler nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a28f-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="7a28f-104">Properties nesnesi, proje için varsayılan ayarların tümünü, içinde tanımlandıkları projenin varsayılan ad alanındaki Özellikler. Settings. Default üyesi aracılığıyla gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a28f-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="7a28f-105">Çalışma zamanında C ile ayarları okumak için\#</span><span class="sxs-lookup"><span data-stu-id="7a28f-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="7a28f-106">Properties. Settings. Default üyesi aracılığıyla uygun ayara erişin.</span><span class="sxs-lookup"><span data-stu-id="7a28f-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="7a28f-107">Aşağıdaki örnekte, BackColor özelliğine adlı `myColor` bir ayarın nasıl atanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a28f-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="7a28f-108">Daha önce türünde `myColor` `System.Drawing.Color`adlı bir ayar içeren bir ayarlar dosyası oluşturmuş olmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7a28f-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="7a28f-109">Bir ayarlar dosyası oluşturma hakkında daha fazla bilgi için [bkz. nasıl yapılır: Tasarım zamanında](how-to-create-a-new-setting-at-design-time.md)yeni bir ayar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a28f-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a28f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a28f-110">See also</span></span>

- [<span data-ttu-id="7a28f-111">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a28f-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="7a28f-112">Nasıl yapılır: Çalışma zamanında Kullanıcı ayarlarını şu şekilde yazın:C#</span><span class="sxs-lookup"><span data-stu-id="7a28f-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="7a28f-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7a28f-113">Application Settings Overview</span></span>](application-settings-overview.md)
