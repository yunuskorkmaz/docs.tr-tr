---
description: ': My. Settings nesnesi hakkında daha fazla bilgi edinin'
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 92323c5379d0c5a4dbf96cfdbe0becccc2bad7cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640608"
---
# <a name="mysettings-object"></a><span data-ttu-id="81327-103">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="81327-103">My.Settings Object</span></span>

<span data-ttu-id="81327-104">Uygulamanın ayarlarına erişmek için özellikleri ve yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="81327-104">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81327-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81327-105">Remarks</span></span>  

 <span data-ttu-id="81327-106">`My.Settings`Nesnesi, uygulama ayarlarına erişim sağlar ve uygulamanızın özellik ayarlarını ve diğer bilgilerini dinamik olarak depolamanızı ve almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="81327-106">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="81327-107">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="81327-107">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81327-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="81327-108">Properties</span></span>  

 <span data-ttu-id="81327-109">`My.Settings`Nesnesinin özellikleri uygulamanızın ayarlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="81327-109">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="81327-110">Ayarları eklemek veya kaldırmak için, **Ayarlar tasarımcısını** kullanın.</span><span class="sxs-lookup"><span data-stu-id="81327-110">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="81327-111">Her ayarın bir **adı**, **türü**, **kapsamı** ve **değeri** vardır ve bu ayarlar, her bir ayara erişme özelliğinin nesnede nasıl göründüğünü belirlenir `My.Settings` :</span><span class="sxs-lookup"><span data-stu-id="81327-111">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="81327-112">**Ad** , özelliğin adını belirler.</span><span class="sxs-lookup"><span data-stu-id="81327-112">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="81327-113">**Tür** , özelliğin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="81327-113">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="81327-114">**Kapsam** , özelliğin salt okunurdur olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="81327-114">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="81327-115">Değer **uygulama** ise, özellik salt okunurdur; değer **Kullanıcı** ise, özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="81327-115">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="81327-116">**Değer** , özelliğin varsayılan değeridir.</span><span class="sxs-lookup"><span data-stu-id="81327-116">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81327-117">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="81327-117">Methods</span></span>  
  
|<span data-ttu-id="81327-118">Yöntem</span><span class="sxs-lookup"><span data-stu-id="81327-118">Method</span></span>|<span data-ttu-id="81327-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81327-119">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="81327-120">Son kaydedilen değerlerden Kullanıcı ayarlarını yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="81327-120">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="81327-121">Geçerli Kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="81327-121">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="81327-122">`My.Settings`Nesnesi ayrıca sınıfından devralınan gelişmiş özellikler ve yöntemler de sağlar <xref:System.Configuration.ApplicationSettingsBase> .</span><span class="sxs-lookup"><span data-stu-id="81327-122">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="81327-123">Görevler</span><span class="sxs-lookup"><span data-stu-id="81327-123">Tasks</span></span>  

 <span data-ttu-id="81327-124">Aşağıdaki tabloda, nesnesiyle ilgili görevlerin örnekleri listelenmektedir `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="81327-124">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="81327-125">Amaç</span><span class="sxs-lookup"><span data-stu-id="81327-125">To</span></span>|<span data-ttu-id="81327-126">Bkz.</span><span class="sxs-lookup"><span data-stu-id="81327-126">See</span></span>|  
|---|---|  
|<span data-ttu-id="81327-127">Uygulama ayarını oku</span><span class="sxs-lookup"><span data-stu-id="81327-127">Read an application setting</span></span>|[<span data-ttu-id="81327-128">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="81327-128">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="81327-129">Kullanıcı ayarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="81327-129">Change a user setting</span></span>|[<span data-ttu-id="81327-130">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="81327-130">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="81327-131">Kullanıcı ayarlarını kalıcı yap</span><span class="sxs-lookup"><span data-stu-id="81327-131">Persist user settings</span></span>|[<span data-ttu-id="81327-132">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="81327-132">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="81327-133">Kullanıcı ayarları için özellik Kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="81327-133">Create a property grid for user settings</span></span>|[<span data-ttu-id="81327-134">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81327-134">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="81327-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="81327-135">Example</span></span>  

 <span data-ttu-id="81327-136">Bu örnek, ayarın değerini gösterir `Nickname` .</span><span class="sxs-lookup"><span data-stu-id="81327-136">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="81327-137">Bu örneğin çalışması için, uygulamanızın türünde bir ayarı olması gerekir `Nickname` `String` .</span><span class="sxs-lookup"><span data-stu-id="81327-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81327-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81327-138">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="81327-139">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="81327-139">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="81327-140">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="81327-140">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="81327-141">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="81327-141">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="81327-142">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81327-142">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="81327-143">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="81327-143">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
