---
title: 'Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 553ebc5b0d6381f56783df8be83344f96a21dd8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968399"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="b8296-102">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b8296-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="b8296-103">`My.Settings` Nesnenin nesne üzerindeki özelliğine yeni bir değer atayarak, bir kullanıcı ayarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8296-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="b8296-104">`My.Settings` Nesnesi her ayarı bir özellik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8296-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="b8296-105">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b8296-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="b8296-106">Ayarın **kapsamı** özelliğin salt okunurdur belirler: Bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="b8296-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="b8296-107">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="b8296-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8296-108">Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b8296-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="b8296-109">Uygulamayı **Proje tasarımcısını** kullanarak oluştururken veya uygulamanın yapılandırma dosyasını düzenleyerek, uygulama kapsamı ayarlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8296-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="b8296-110">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b8296-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8296-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8296-111">Example</span></span>  
 <span data-ttu-id="b8296-112">Bu örnek, `Nickname` Kullanıcı ayarının değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b8296-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="b8296-113">Bu örneğin çalışması için, uygulamanızın türünde `Nickname` `String`bir Kullanıcı ayarı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8296-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="b8296-114">Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b8296-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="b8296-115">Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="b8296-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="b8296-116">Daha fazla bilgi için [nasıl yapılır: Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Kullanıcı ayarlarını kalıcı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="b8296-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8296-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8296-117">See also</span></span>

- [<span data-ttu-id="b8296-118">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b8296-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="b8296-119">Nasıl yapılır: Visual Basic uygulama ayarlarını okuyun</span><span class="sxs-lookup"><span data-stu-id="b8296-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="b8296-120">Nasıl yapılır: Visual Basic Kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="b8296-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="b8296-121">Nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8296-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="b8296-122">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="b8296-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
