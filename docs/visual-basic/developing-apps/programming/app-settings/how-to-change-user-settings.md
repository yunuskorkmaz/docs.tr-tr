---
title: "Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db35a5d63938fcc508c23af5588957d8dc518676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="faab7-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="faab7-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="faab7-103">Kullanıcı ayarı üzerinde ayarın özelliği için yeni bir değer atayarak değiştirebileceğiniz `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="faab7-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="faab7-104">`My.Settings` Nesne her ayar özelliği olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="faab7-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="faab7-105">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="faab7-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="faab7-106">Ayarın **kapsam** özelliği salt okunur olup olmadığını belirler: özelliği için bir **uygulama**-kapsam ayarıdır hatayla özelliği için salt okunur bir **kullanıcı**-kapsamı salt okunur bir ayardır.</span><span class="sxs-lookup"><span data-stu-id="faab7-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="faab7-107">Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="faab7-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faab7-108">Değiştirmek ve çalışma zamanında kullanıcı kapsam ayarlarının değerleri kaydedin, ancak uygulama kapsamı ayarları salt okunurdur ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="faab7-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="faab7-109">Kullanarak uygulama oluşturduğunuzda uygulama kapsamı ayarlarını değiştirebilirsiniz **Proje Tasarımcısı** ya da uygulamanın yapılandırma dosyasını düzenleyerek.</span><span class="sxs-lookup"><span data-stu-id="faab7-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="faab7-110">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="faab7-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faab7-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="faab7-111">Example</span></span>  
 <span data-ttu-id="faab7-112">Bu örnek değerini değiştirir `Nickname` kullanıcı ayarı.</span><span class="sxs-lookup"><span data-stu-id="faab7-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 <span data-ttu-id="faab7-113">Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü kullanıcı ayarı `String`.</span><span class="sxs-lookup"><span data-stu-id="faab7-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="faab7-114">Uygulama kapatıldığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="faab7-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="faab7-115">Ayarlar hemen kaydetmek için arama `My.Settings.Save` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="faab7-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="faab7-116">Daha fazla bilgi için bkz: [nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="faab7-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faab7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="faab7-117">See Also</span></span>  
 [<span data-ttu-id="faab7-118">My.Settings nesnesi</span><span class="sxs-lookup"><span data-stu-id="faab7-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="faab7-119">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="faab7-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="faab7-120">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="faab7-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="faab7-121">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="faab7-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="faab7-122">Uygulama ayarları (.NET) yönetme</span><span class="sxs-lookup"><span data-stu-id="faab7-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
