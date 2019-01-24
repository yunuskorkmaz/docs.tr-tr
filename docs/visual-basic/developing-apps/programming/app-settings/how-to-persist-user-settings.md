---
title: "Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: dab285f175838fb71e4218cbafdd4f7593c9e786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611300"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="e150c-102">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="e150c-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="e150c-103">Kullanabileceğiniz `My.Settings.Save` kullanıcı ayarlarında yapılan değişiklikleri kalıcı hale getirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e150c-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="e150c-104">Genellikle, uygulamalar, uygulama kapatıldığında yapılan kullanıcı ayarlarını kalıcı hale getirmek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e150c-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="e150c-105">Ayarlar kaydedilirken, birkaç etkene bağlı olarak birkaç saniye sürebilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e150c-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="e150c-106">Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e150c-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e150c-107">Değiştirin ve çalışma zamanında kullanıcı kapsamlı ayarların değerleri kaydedin olsa da, uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e150c-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="e150c-108">Uygulama kapsamı ayarları aracılığıyla uygulama oluştururken değiştirebilirsiniz **Proje Tasarımcısı**, ya da uygulama yapılandırma dosyasını düzenleyerek.</span><span class="sxs-lookup"><span data-stu-id="e150c-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="e150c-109">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e150c-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e150c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e150c-110">Example</span></span>  
 <span data-ttu-id="e150c-111">Bu örnekte değiştirir `LastChanged` kullanıcı ayarı ve çağırarak değiştirme kaydeder `My.Settings.Save` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e150c-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 <span data-ttu-id="e150c-112">Bu örneğin çalışması, uygulamanız olmalıdır bir `LastChanged` türü kullanıcı ayarı `Date`.</span><span class="sxs-lookup"><span data-stu-id="e150c-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="e150c-113">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="e150c-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e150c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e150c-114">See also</span></span>
- [<span data-ttu-id="e150c-115">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e150c-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="e150c-116">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="e150c-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="e150c-117">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="e150c-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="e150c-118">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e150c-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="e150c-119">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="e150c-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
