---
title: Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma
ms.date: 03/30/2017
description: Uygulama ayarları ve Kullanıcı ayarlarını kullanarak uygulama yürütme oturumları arasında kalıcı olan değerler oluşturma ve bunları erişme hakkında bilgi edinin.
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903174"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="09ac0-103">Uygulama Ayarları ve Kullanıcı Ayarlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="09ac0-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="09ac0-104">2,0 .NET Framework başlayarak, uygulama yürütme oturumları arasında kalıcı olan değerler oluşturabilir ve erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ac0-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="09ac0-105">Bu değerler *Ayarlar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="09ac0-105">These values are called *settings*.</span></span> <span data-ttu-id="09ac0-106">Ayarlar, Kullanıcı tercihlerini veya uygulamanın kullanması gereken değerli bilgileri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="09ac0-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="09ac0-107">Örneğin, bir uygulamanın renk düzeni için Kullanıcı tercihlerini depolayan bir dizi ayar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ac0-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="09ac0-108">Ya da uygulamanızın kullandığı bir veritabanını belirten bağlantı dizesini saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ac0-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="09ac0-109">Ayarlar, uygulama için önemli olan bilgileri her ikisi de kod dışında kalıcı hale getirebilmeniz ve bireysel kullanıcıların tercihlerini depolayan profiller oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="09ac0-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="09ac0-110">Bu bölümdeki konularda, tasarım zamanında ve çalışma zamanında ayarların nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="09ac0-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09ac0-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="09ac0-111">In This Section</span></span>  
 [<span data-ttu-id="09ac0-112">Nasıl Yapılır: Tasarım Zamanında Yeni Ayar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09ac0-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="09ac0-113">Bir uygulama için yeni bir ayar oluşturmak üzere Visual Studio 'Nun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ac0-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="09ac0-114">Nasıl yapılır: Tasarım Zamanında Mevcut Bir Ayarın Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="09ac0-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="09ac0-115">Mevcut bir ayarın değerini değiştirmek için Visual Studio 'nun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ac0-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="09ac0-116">Nasıl yapılır: Uygulama Oturumları Arasında Bir Ayarın Değerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="09ac0-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="09ac0-117">Uygulama oturumları arasında derlenmiş bir uygulamadaki bir ayarın değerini değiştirme hakkında ayrıntılı bilgi.</span><span class="sxs-lookup"><span data-stu-id="09ac0-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="09ac0-118">Nasıl Yapılır: Çalışma Zamanında C# ile Ayarları Okuma</span><span class="sxs-lookup"><span data-stu-id="09ac0-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="09ac0-119">C# ile ayarları okumak için kodun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ac0-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="09ac0-120">Nasıl Yapılır: Çalışma Zamanında C# ile Kullanıcı Ayarlarını Yazma</span><span class="sxs-lookup"><span data-stu-id="09ac0-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="09ac0-121">C# ile Kullanıcı ayarlarının değerlerini yazmak ve kaydetmek için kodun nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09ac0-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="09ac0-122">Nasıl Yapılır: Uygulamanıza C#'de Birden Çok Ayar Kümesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="09ac0-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="09ac0-123">C# ile bir uygulamaya birden çok ayar kümesi ekleme hakkında ayrıntılı bilgi.</span><span class="sxs-lookup"><span data-stu-id="09ac0-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ac0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09ac0-124">See also</span></span>

- [<span data-ttu-id="09ac0-125">Windows Forms için Uygulama Ayarları</span><span class="sxs-lookup"><span data-stu-id="09ac0-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
