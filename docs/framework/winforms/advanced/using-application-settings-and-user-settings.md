---
title: "Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9544b6af74608bd1b29db3250e887999ae3187f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="80651-102">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="80651-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="80651-103">.NET Framework 2.0 ile başlayarak, oluşturma ve uygulama yürütme oturumları arasında kalıcı değerlere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="80651-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="80651-104">Bu değerler olarak adlandırılan *ayarları*.</span><span class="sxs-lookup"><span data-stu-id="80651-104">These values are called *settings*.</span></span> <span data-ttu-id="80651-105">Ayarları kullanıcı tercihleri gösterebilir veya değerli bilgileri uygulama kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="80651-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="80651-106">Örneğin, bir dizi uygulama renk düzenini ilgili kullanıcı tercihlerini depolamak ayarları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80651-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="80651-107">Veya, uygulamanızın kullandığı bir veritabanını belirtir bağlantı dizesi depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="80651-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="80651-108">Ayarlar, her ikisi de size kod dışında ve bireysel kullanıcıların tercihleri depolamak profilleri oluşturmak için uygulamaya kritik bilgileri kalıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="80651-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="80651-109">Bu bölümdeki konular, ayarları tasarım zamanında ve çalışma zamanı nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80651-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80651-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="80651-110">In This Section</span></span>  
 [<span data-ttu-id="80651-111">Nasıl yapılır: tasarım zamanında yeni ayar oluşturun</span><span class="sxs-lookup"><span data-stu-id="80651-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="80651-112">Visual Studio bir uygulama için yeni bir ayar oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="80651-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="80651-113">Nasıl yapılır: tasarım zamanında mevcut bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="80651-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="80651-114">Mevcut bir ayarın değerini değiştirmek için Visual Studio kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="80651-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="80651-115">Nasıl yapılır: uygulama oturumları arasında bir ayarın değerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="80651-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="80651-116">Uygulama oturumları arasında derlenmiş bir uygulamada bir ayarın değerini değiştirmek nasıl ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80651-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="80651-117">Nasıl yapılır: Çalışma zamanında C# ile ayarları okuma</span><span class="sxs-lookup"><span data-stu-id="80651-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="80651-118">Kod C# ile ayarları okuma için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="80651-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="80651-119">Nasıl yapılır: Çalışma zamanında C# ile kullanıcı ayarlarını yazma</span><span class="sxs-lookup"><span data-stu-id="80651-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="80651-120">Kod yazma ve kullanıcı ayarlarının değerleri C# ile kaydetmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="80651-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="80651-121">Nasıl yapılır: C# uygulamanız birden çok ayar kümesi ekleme</span><span class="sxs-lookup"><span data-stu-id="80651-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="80651-122">C# ile bir uygulama için birden çok ayar kümesi ekleme ayrıntıları verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80651-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80651-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80651-123">See Also</span></span>  
 [<span data-ttu-id="80651-124">Windows Forms için uygulama ayarları</span><span class="sxs-lookup"><span data-stu-id="80651-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
