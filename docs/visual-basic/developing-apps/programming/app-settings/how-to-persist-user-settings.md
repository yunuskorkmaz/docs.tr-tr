---
title: 'Nasıl Yapılır: Kullanıcı Ayarlarını Kalıcı Yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329636"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="12755-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="12755-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="12755-103">Kullanıcı ayarlarındaki `My.Settings.Save` değişiklikleri sürdürmek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12755-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="12755-104">Genellikle, uygulamalar kapatıldığında kullanıcı ayarlarındaki değişiklikleri sürdürmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="12755-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="12755-105">Bunun nedeni, ayarları kaydetmenin birkaç etkene bağlı olarak birkaç saniye sürebileceğidir.</span><span class="sxs-lookup"><span data-stu-id="12755-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="12755-106">Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.</span><span class="sxs-lookup"><span data-stu-id="12755-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12755-107">Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirip kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunur ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="12755-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="12755-108">Uygulamayı oluştururken, **Proje Tasarımcısı**aracılığıyla veya uygulamanın yapılandırma dosyasını düzenleyerek uygulama kapsamı ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12755-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="12755-109">Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="12755-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12755-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="12755-110">Example</span></span>  

 <span data-ttu-id="12755-111">Bu örnek, `LastChanged` kullanıcı ayarı değerini değiştirir ve `My.Settings.Save` yöntemi çağırarak bu değişikliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="12755-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="12755-112">Bu örneğin çalışabilmesi için, uygulamanızın bir `LastChanged` kullanıcı `Date`ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="12755-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="12755-113">Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="12755-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12755-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12755-114">See also</span></span>

- [<span data-ttu-id="12755-115">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="12755-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="12755-116">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="12755-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="12755-117">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="12755-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="12755-118">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12755-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="12755-119">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="12755-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
