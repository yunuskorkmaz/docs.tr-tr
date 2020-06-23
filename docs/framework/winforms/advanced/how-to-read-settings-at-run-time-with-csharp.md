---
title: 'Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma'
description: Özellikler nesnesi aracılığıyla C# ile çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarların nasıl okunacağını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903368"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b2ea7-103">Nasıl yapılır: çalışma zamanında C Ile ayarları okuma\#</span><span class="sxs-lookup"><span data-stu-id="b2ea7-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="b2ea7-104">Özellikler nesnesi aracılığıyla çalışma zamanında uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2ea7-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="b2ea7-105">Properties nesnesi, proje için varsayılan ayarların tümünü, içinde tanımlandıkları projenin varsayılan ad alanındaki Özellikler. Settings. Default üyesi aracılığıyla gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2ea7-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b2ea7-106">Çalışma zamanında C ile ayarları okumak için\#</span><span class="sxs-lookup"><span data-stu-id="b2ea7-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="b2ea7-107">Properties. Settings. Default üyesi aracılığıyla uygun ayara erişin.</span><span class="sxs-lookup"><span data-stu-id="b2ea7-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="b2ea7-108">Aşağıdaki örnekte, BackColor özelliğine adlı bir ayarın nasıl atanacağı gösterilmektedir `myColor` .</span><span class="sxs-lookup"><span data-stu-id="b2ea7-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="b2ea7-109">Daha önce türünde adlı bir ayar içeren bir ayarlar dosyası oluşturmuş olmanızı gerektirir `myColor` `System.Drawing.Color` .</span><span class="sxs-lookup"><span data-stu-id="b2ea7-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="b2ea7-110">Bir ayarlar dosyası oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tasarım zamanında yeni ayar oluşturma](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b2ea7-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2ea7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ea7-111">See also</span></span>

- [<span data-ttu-id="b2ea7-112">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b2ea7-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="b2ea7-113">Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma</span><span class="sxs-lookup"><span data-stu-id="b2ea7-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="b2ea7-114">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2ea7-114">Application Settings Overview</span></span>](application-settings-overview.md)
