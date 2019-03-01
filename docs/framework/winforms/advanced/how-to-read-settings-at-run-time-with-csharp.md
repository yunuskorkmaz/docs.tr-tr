---
title: 'Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974854"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b0f44-102">Nasıl yapılır: Çalışma zamanında C ile ayarları okuma\#</span><span class="sxs-lookup"><span data-stu-id="b0f44-102">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="b0f44-103">Çalışma zamanında özellikleri nesnesi aracılığıyla hem uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f44-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="b0f44-104">Özellikler nesnesinin tüm Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0f44-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="b0f44-105">Çalışma zamanında C ile ayarları okunamadı\#</span><span class="sxs-lookup"><span data-stu-id="b0f44-105">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="b0f44-106">Uygun ayarı Properties.Settings.Default üye aracılığıyla erişin.</span><span class="sxs-lookup"><span data-stu-id="b0f44-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="b0f44-107">Aşağıdaki örnek adlı bir ayar atama gösterir `myColor` BackColor özelliği.</span><span class="sxs-lookup"><span data-stu-id="b0f44-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="b0f44-108">Adlı bir ayarı içeren bir ayarlar dosyası daha önce oluşturmuş olmanız gerekir `myColor` türü `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="b0f44-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="b0f44-109">Ayarları dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarım zamanında yeni ayar oluşturma](how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b0f44-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0f44-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0f44-110">See also</span></span>

- [<span data-ttu-id="b0f44-111">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0f44-111">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="b0f44-112">Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#</span><span class="sxs-lookup"><span data-stu-id="b0f44-112">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="b0f44-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b0f44-113">Application Settings Overview</span></span>](application-settings-overview.md)
