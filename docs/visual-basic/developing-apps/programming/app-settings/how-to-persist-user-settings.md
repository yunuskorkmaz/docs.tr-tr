---
description: 'Daha fazla bilgi: nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale getirme'
title: 'Nasıl yapılır: Kullanıcı Ayarlarını Kalıcı Yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 43ca82442678356afacb8e05149a35d485603059
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797841"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="6963b-103">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="6963b-103">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="6963b-104">`My.Settings.Save`Kullanıcı ayarlarındaki değişiklikleri kalıcı hale getirmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6963b-104">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="6963b-105">Genellikle, uygulamalar, uygulama kapandığında Kullanıcı ayarlarındaki değişiklikleri kalıcı hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6963b-105">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="6963b-106">Bunun nedeni, ayarların kaydedilmesi birkaç etmene bağlı olarak birkaç saniyeye göre yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="6963b-106">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="6963b-107">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="6963b-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6963b-108">Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6963b-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="6963b-109">Uygulamayı oluştururken, **Proje Tasarımcısı** aracılığıyla veya uygulamanın yapılandırma dosyasını düzenleyerek uygulama kapsamı ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6963b-109">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="6963b-110">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6963b-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6963b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6963b-111">Example</span></span>  

 <span data-ttu-id="6963b-112">Bu örnek, Kullanıcı ayarının değerini değiştirir `LastChanged` ve yöntemini çağırarak bu değişikliği kaydeder `My.Settings.Save` .</span><span class="sxs-lookup"><span data-stu-id="6963b-112">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="6963b-113">Bu örneğin çalışması için, uygulamanızın `LastChanged` türünde bir Kullanıcı ayarı olması gerekir `Date` .</span><span class="sxs-lookup"><span data-stu-id="6963b-113">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="6963b-114">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6963b-114">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6963b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6963b-115">See also</span></span>

- [<span data-ttu-id="6963b-116">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="6963b-116">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="6963b-117">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="6963b-117">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="6963b-118">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6963b-118">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="6963b-119">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6963b-119">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="6963b-120">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="6963b-120">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
