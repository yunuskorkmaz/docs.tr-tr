---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 54176ae6706311b17227c7dc21a5060c9b369753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603038"
---
# <a name="mysettings-object"></a><span data-ttu-id="29963-102">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="29963-102">My.Settings Object</span></span>
<span data-ttu-id="29963-103">Özellikler ve uygulamanın ayarlarına erişmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="29963-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29963-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29963-104">Remarks</span></span>  
 <span data-ttu-id="29963-105">`My.Settings` Nesne uygulamanın ayarlarına erişim sağlar ve dinamik olarak depolamak ve özellik ayarları ve uygulamanız için diğer bilgilerini almak sağlar.</span><span class="sxs-lookup"><span data-stu-id="29963-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="29963-106">Daha fazla bilgi için bkz: [yönetme uygulama ayarları (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="29963-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29963-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="29963-107">Properties</span></span>  
 <span data-ttu-id="29963-108">Özelliklerini `My.Settings` nesne uygulamanızın ayarlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="29963-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="29963-109">Ayarlar eklemek veya kaldırmak için kullanın **ayarları Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="29963-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="29963-110">Her ayarına sahip bir **adı**, **türü**, **kapsam**, ve **değeri**, ve bu ayarlar belirler nasıl her ayar erişmek için özelliğini görünür `My.Settings` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="29963-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="29963-111">**Ad** özelliğinin adını belirler.</span><span class="sxs-lookup"><span data-stu-id="29963-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="29963-112">**Tür** özelliğin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="29963-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="29963-113">**Kapsam** özelliği salt okunur olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29963-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="29963-114">Değer ise **uygulama**, özellik değeri geçerliyse salt okunur; **kullanıcı**, salt okunur bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="29963-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="29963-115">**Değer** özelliğinin varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="29963-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29963-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="29963-116">Methods</span></span>  
  
|<span data-ttu-id="29963-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="29963-117">Method</span></span>|<span data-ttu-id="29963-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29963-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="29963-119">Son kaydedilen değerlerini kullanıcı ayarlarından yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="29963-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="29963-120">Geçerli kullanıcı ayarları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="29963-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="29963-121">`My.Settings` Nesnesi de sağlar Gelişmiş özellikleri ve yöntemleri, devralınan <xref:System.Configuration.ApplicationSettingsBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="29963-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="29963-122">Görevler</span><span class="sxs-lookup"><span data-stu-id="29963-122">Tasks</span></span>  
 <span data-ttu-id="29963-123">Örnekler ilgili görevleri aşağıdaki tabloda listelenmektedir `My.Settings` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="29963-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="29963-124">Bitiş</span><span class="sxs-lookup"><span data-stu-id="29963-124">To</span></span>|<span data-ttu-id="29963-125">Bkz. </span><span class="sxs-lookup"><span data-stu-id="29963-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="29963-126">Bir uygulama ayarı okuma</span><span class="sxs-lookup"><span data-stu-id="29963-126">Read an application setting</span></span>|[<span data-ttu-id="29963-127">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="29963-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="29963-128">Bir kullanıcı ayarı değiştirme</span><span class="sxs-lookup"><span data-stu-id="29963-128">Change a user setting</span></span>|[<span data-ttu-id="29963-129">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="29963-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="29963-130">Kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="29963-130">Persist user settings</span></span>|[<span data-ttu-id="29963-131">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="29963-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="29963-132">Kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="29963-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="29963-133">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="29963-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="29963-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="29963-134">Example</span></span>  
 <span data-ttu-id="29963-135">Bu örnek değerini görüntüler `Nickname` ayarı.</span><span class="sxs-lookup"><span data-stu-id="29963-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 <span data-ttu-id="29963-136">Bu örnekte çalışması, uygulamanızın olmalıdır bir `Nickname` türü ayarı `String`.</span><span class="sxs-lookup"><span data-stu-id="29963-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29963-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29963-137">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [<span data-ttu-id="29963-138">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="29963-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="29963-139">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="29963-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="29963-140">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını sürdürmek</span><span class="sxs-lookup"><span data-stu-id="29963-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="29963-141">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzları oluşturma</span><span class="sxs-lookup"><span data-stu-id="29963-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="29963-142">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="29963-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
