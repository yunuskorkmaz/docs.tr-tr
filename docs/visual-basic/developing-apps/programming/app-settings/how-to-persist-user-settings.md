---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1cf424a4e587818a8e2766a5e27c084010c084c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="0b788-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="0b788-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="0b788-103">Kullanabileceğiniz `My.Settings.Save` kullanıcı ayarlarında yapılan değişiklikler kalıcı hale getirmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0b788-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="0b788-104">Genellikle, uygulamalar, uygulama kapatıldığında kullanıcı ayarlarında yapılan değişiklikler kalıcı hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b788-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="0b788-105">Ayarları kaydetme, birkaç etkene bağlı olarak birkaç saniye sürebilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0b788-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="0b788-106">Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="0b788-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b788-107">Değiştirmek ve çalışma zamanında kullanıcı kapsam ayarlarının değerleri kaydedin, ancak uygulama kapsamı ayarları salt okunurdur ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0b788-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="0b788-108">Aracılığıyla uygulama oluştururken, uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı**, ya da uygulamanın yapılandırma dosyasını düzenleyerek.</span><span class="sxs-lookup"><span data-stu-id="0b788-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="0b788-109">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0b788-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b788-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b788-110">Example</span></span>  
 <span data-ttu-id="0b788-111">Bu örnek değerini değiştirir `LastChanged` kullanıcı ayarı ve çağırarak değiştirmek kaydeder `My.Settings.Save` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b788-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 <span data-ttu-id="0b788-112">Bu örnekte çalışması, uygulamanızın olmalıdır bir `LastChanged` türü kullanıcı ayarı `Date`.</span><span class="sxs-lookup"><span data-stu-id="0b788-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="0b788-113">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0b788-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b788-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b788-114">See Also</span></span>  
 [<span data-ttu-id="0b788-115">My.Settings nesnesi</span><span class="sxs-lookup"><span data-stu-id="0b788-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="0b788-116">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="0b788-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="0b788-117">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="0b788-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="0b788-118">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="0b788-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="0b788-119">Uygulama ayarları (.NET) yönetme</span><span class="sxs-lookup"><span data-stu-id="0b788-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
