---
title: Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: 70af7054353886757af81910f780e62001f0c9d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685119"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="473cd-102">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="473cd-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="473cd-103">.NET Framework 2.0 ile başlayarak, oluşturma ve uygulama yürütme oturumları arasında kalıcı değerleri erişim.</span><span class="sxs-lookup"><span data-stu-id="473cd-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="473cd-104">Bu değerler olarak adlandırılan *ayarları*.</span><span class="sxs-lookup"><span data-stu-id="473cd-104">These values are called *settings*.</span></span> <span data-ttu-id="473cd-105">Ayarları kullanıcı tercihlerini temsil edebilir veya değerli bilgileri uygulama kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="473cd-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="473cd-106">Örneğin, bir uygulamanın renk şeması için kullanıcı tercihlerini depolamak ayarları bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="473cd-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="473cd-107">Veya, uygulamanızın kullandığı bir veritabanını belirten bir bağlantı dizesi depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="473cd-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="473cd-108">Ayarlar, her iki uygulamanın kodu dışında ve tek tek kullanıcıların tercihleri depolamak profilleri oluşturmak için önemli olan bilgileri kalıcı hale sağlar.</span><span class="sxs-lookup"><span data-stu-id="473cd-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="473cd-109">Bu bölümdeki konular, tasarım zamanında ve çalışma zamanı ayarları nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="473cd-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="473cd-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="473cd-110">In This Section</span></span>  
 [<span data-ttu-id="473cd-111">Nasıl yapılır: Tasarım zamanında yeni ayar oluşturma</span><span class="sxs-lookup"><span data-stu-id="473cd-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="473cd-112">Bir uygulama için yeni bir ayar oluşturmak için Visual Studio kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="473cd-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="473cd-113">Nasıl yapılır: Tasarım zamanında mevcut bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="473cd-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="473cd-114">Mevcut bir ayarın değerini değiştirmek için Visual Studio kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="473cd-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="473cd-115">Nasıl yapılır: Uygulama oturumları arasında bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="473cd-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="473cd-116">Uygulama oturumları arasında derlenmiş bir uygulamada bir ayarın değerini değiştirme işlemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="473cd-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="473cd-117">Nasıl yapılır: Çalışma zamanında ile ayarları okumaC#</span><span class="sxs-lookup"><span data-stu-id="473cd-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="473cd-118">Ayarlarla okumayı kod kullanmayı açıklar C#.</span><span class="sxs-lookup"><span data-stu-id="473cd-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="473cd-119">Nasıl yapılır: Çalışma zamanında ile kullanıcı ayarlarını yazmaC#</span><span class="sxs-lookup"><span data-stu-id="473cd-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="473cd-120">Kod yazma ve değerleri ile kullanıcı ayarlarını kaydetmek için kullanmayı açıklar C#.</span><span class="sxs-lookup"><span data-stu-id="473cd-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="473cd-121">Nasıl yapılır: Uygulamanızda birden çok ayar kümesi eklemeC#</span><span class="sxs-lookup"><span data-stu-id="473cd-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="473cd-122">Bir uygulama ile birden çok ayar kümesi ekleme hakkında ayrıntılı C#.</span><span class="sxs-lookup"><span data-stu-id="473cd-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473cd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="473cd-123">See also</span></span>
- [<span data-ttu-id="473cd-124">Windows Forms için Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="473cd-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
