---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: f3348e9eea5bdd7f4fd911150877c9aefdd66bcc
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867291"
---
# <a name="mysettings-object"></a><span data-ttu-id="5c6db-102">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="5c6db-102">My.Settings Object</span></span>

<span data-ttu-id="5c6db-103">Uygulamanın ayarlarına erişmek için özellikleri ve yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c6db-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c6db-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c6db-104">Remarks</span></span>  

 <span data-ttu-id="5c6db-105">`My.Settings`Nesnesi, uygulama ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c6db-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="5c6db-106">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5c6db-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c6db-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c6db-107">Properties</span></span>  

 <span data-ttu-id="5c6db-108">`My.Settings`Nesnesinin özellikleri uygulamanızın ayarlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c6db-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="5c6db-109">Ayarları eklemek veya kaldırmak için, **Ayarlar tasarımcısını**kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c6db-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="5c6db-110">Her ayarın bir **adı**, **türü**, **kapsamı**ve **değeri**vardır ve bu ayarlar, her bir ayara erişme özelliğinin nesnede nasıl göründüğünü belirlenir `My.Settings` :</span><span class="sxs-lookup"><span data-stu-id="5c6db-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="5c6db-111">**Ad** , özelliğin adını belirler.</span><span class="sxs-lookup"><span data-stu-id="5c6db-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="5c6db-112">**Tür** , özelliğin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="5c6db-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="5c6db-113">**Kapsam** , özelliğin salt okunurdur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c6db-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="5c6db-114">Değer **uygulama**ise, özellik salt okunurdur; değer **Kullanıcı**ise, özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="5c6db-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="5c6db-115">**Değer** , özelliğin varsayılan değeridir.</span><span class="sxs-lookup"><span data-stu-id="5c6db-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c6db-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c6db-116">Methods</span></span>  
  
|<span data-ttu-id="5c6db-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c6db-117">Method</span></span>|<span data-ttu-id="5c6db-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c6db-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="5c6db-119">Son kaydedilen değerlerden Kullanıcı ayarlarını yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="5c6db-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="5c6db-120">Geçerli Kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5c6db-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="5c6db-121">`My.Settings`Nesnesi ayrıca sınıfından devralınan gelişmiş özellikler ve yöntemler de sağlar <xref:System.Configuration.ApplicationSettingsBase> .</span><span class="sxs-lookup"><span data-stu-id="5c6db-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="5c6db-122">Görevler</span><span class="sxs-lookup"><span data-stu-id="5c6db-122">Tasks</span></span>  

 <span data-ttu-id="5c6db-123">Aşağıdaki tabloda, nesnesiyle ilgili görevlerin örnekleri listelenmektedir `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="5c6db-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="5c6db-124">Amaç</span><span class="sxs-lookup"><span data-stu-id="5c6db-124">To</span></span>|<span data-ttu-id="5c6db-125">Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c6db-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="5c6db-126">Uygulama ayarını oku</span><span class="sxs-lookup"><span data-stu-id="5c6db-126">Read an application setting</span></span>|[<span data-ttu-id="5c6db-127">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="5c6db-127">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="5c6db-128">Kullanıcı ayarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="5c6db-128">Change a user setting</span></span>|[<span data-ttu-id="5c6db-129">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5c6db-129">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="5c6db-130">Kullanıcı ayarlarını kalıcı yap</span><span class="sxs-lookup"><span data-stu-id="5c6db-130">Persist user settings</span></span>|[<span data-ttu-id="5c6db-131">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="5c6db-131">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="5c6db-132">Kullanıcı ayarları için özellik Kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="5c6db-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="5c6db-133">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5c6db-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="5c6db-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c6db-134">Example</span></span>  

 <span data-ttu-id="5c6db-135">Bu örnek, ayarın değerini gösterir `Nickname` .</span><span class="sxs-lookup"><span data-stu-id="5c6db-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="5c6db-136">Bu örneğin çalışması için, uygulamanızın türünde bir ayarı olması gerekir `Nickname` `String` .</span><span class="sxs-lookup"><span data-stu-id="5c6db-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6db-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c6db-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="5c6db-138">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="5c6db-138">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="5c6db-139">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5c6db-139">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="5c6db-140">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="5c6db-140">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="5c6db-141">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5c6db-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5c6db-142">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="5c6db-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
