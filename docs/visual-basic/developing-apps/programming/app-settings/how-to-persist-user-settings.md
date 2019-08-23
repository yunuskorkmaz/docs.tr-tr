---
title: 'Nasıl yapılır: Visual Basic Kullanıcı ayarlarını kalıcı yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 0683a5c359da1c4d082f7312c1ed8f43e1c151f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968372"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="8d579-102">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="8d579-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="8d579-103">Kullanıcı ayarlarındaki değişiklikleri kalıcı `My.Settings.Save` hale getirmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d579-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="8d579-104">Genellikle, uygulamalar, uygulama kapandığında Kullanıcı ayarlarındaki değişiklikleri kalıcı hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8d579-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="8d579-105">Bunun nedeni, ayarların kaydedilmesi birkaç etmene bağlı olarak birkaç saniyeye göre yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d579-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="8d579-106">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="8d579-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d579-107">Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8d579-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="8d579-108">Uygulamayı oluştururken, **Proje Tasarımcısı**aracılığıyla veya uygulamanın yapılandırma dosyasını düzenleyerek uygulama kapsamı ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d579-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="8d579-109">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8d579-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d579-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d579-110">Example</span></span>  
 <span data-ttu-id="8d579-111">Bu örnek, `LastChanged` Kullanıcı ayarının değerini değiştirir ve `My.Settings.Save` yöntemini çağırarak bu değişikliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8d579-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="8d579-112">Bu örneğin çalışması için, uygulamanızın türünde `LastChanged` `Date`bir Kullanıcı ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d579-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="8d579-113">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8d579-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d579-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d579-114">See also</span></span>

- [<span data-ttu-id="8d579-115">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="8d579-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="8d579-116">Nasıl yapılır: Visual Basic uygulama ayarlarını okuyun</span><span class="sxs-lookup"><span data-stu-id="8d579-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="8d579-117">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="8d579-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="8d579-118">Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d579-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="8d579-119">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="8d579-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
