---
title: 'Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521757"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="bfe4f-102">Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#</span><span class="sxs-lookup"><span data-stu-id="bfe4f-102">How To: Read Settings at Run Time With C#</span></span> #
<span data-ttu-id="bfe4f-103">Çalışma zamanında özellikleri nesnesi aracılığıyla hem uygulama kapsamlı ve kullanıcı kapsamlı ayarları okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-103">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="bfe4f-104">Özellikler nesnesinin tüm Properties.Settings.Default üye aracılığıyla proje için varsayılan ayarları gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-104">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member.</span></span>  
  
### <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="bfe4f-105">Çalışma zamanında ile ayarları okunamadıC#</span><span class="sxs-lookup"><span data-stu-id="bfe4f-105">To Read Settings at Run Time with C#</span></span>  
  
-   <span data-ttu-id="bfe4f-106">Uygun ayarı Properties.Settings.Default üye aracılığıyla erişin.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-106">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="bfe4f-107">Aşağıdaki örnek adlı bir ayar atama gösterir `myColor` BackColor özelliği.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-107">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="bfe4f-108">Adlı bir ayarı içeren bir ayarlar dosyası daha önce oluşturmuş olmanız gerekir `myColor` türü `System.Drawing.Color`.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-108">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="bfe4f-109">Ayarları dosyası oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Tasarım zamanında yeni ayar oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="bfe4f-109">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bfe4f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe4f-110">See also</span></span>
- [<span data-ttu-id="bfe4f-111">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfe4f-111">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="bfe4f-112">Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#</span><span class="sxs-lookup"><span data-stu-id="bfe4f-112">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="bfe4f-113">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bfe4f-113">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
