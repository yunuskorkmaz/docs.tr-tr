---
title: My.Settings nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9533e8e1ccc51078fefcf6bf73feb2683ae8febb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625277"
---
# <a name="mysettings-object"></a><span data-ttu-id="181aa-102">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="181aa-102">My.Settings Object</span></span>
<span data-ttu-id="181aa-103">Özellikler ve uygulama ayarlarının erişmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="181aa-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="181aa-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="181aa-104">Remarks</span></span>  
 <span data-ttu-id="181aa-105">`My.Settings` Nesne uygulamanın ayarlarına erişim sağlar ve dinamik olarak depolamak ve özellik ayarlarını ve uygulamanızın diğer bilgilerini almak sağlar.</span><span class="sxs-lookup"><span data-stu-id="181aa-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="181aa-106">Daha fazla bilgi için [uygulama ayarlarını yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="181aa-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="181aa-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="181aa-107">Properties</span></span>  
 <span data-ttu-id="181aa-108">Özelliklerini `My.Settings` nesne, uygulamanızın ayarlarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="181aa-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="181aa-109">Ayarlar eklemek veya kaldırmak için kullanın **ayarlar Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="181aa-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="181aa-110">Her ayarının bir **adı**, **türü**, **kapsam**, ve **değer**, ve bu ayarlar belirler nasıl her ayar erişmek için özelliği görünür `My.Settings` nesnesi:</span><span class="sxs-lookup"><span data-stu-id="181aa-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="181aa-111">**Adı** özelliğin adını belirler.</span><span class="sxs-lookup"><span data-stu-id="181aa-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="181aa-112">**Tür** özelliğin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="181aa-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="181aa-113">**Kapsam** özelliği salt okunur olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="181aa-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="181aa-114">Değer ise **uygulama**, özelliği değer ise salt okunur; **kullanıcı**, okuma-yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="181aa-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="181aa-115">**Değer** özelliğinin varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="181aa-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="181aa-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="181aa-116">Methods</span></span>  
  
|<span data-ttu-id="181aa-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="181aa-117">Method</span></span>|<span data-ttu-id="181aa-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="181aa-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="181aa-119">Son kaydedilen değerler kullanıcı ayarlarının yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="181aa-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="181aa-120">Geçerli kullanıcı ayarları kaydeder.</span><span class="sxs-lookup"><span data-stu-id="181aa-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="181aa-121">`My.Settings` Nesnesi de sağlar Gelişmiş özellikleri ve yöntemleri, devralınan <xref:System.Configuration.ApplicationSettingsBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="181aa-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="181aa-122">Görevler</span><span class="sxs-lookup"><span data-stu-id="181aa-122">Tasks</span></span>  
 <span data-ttu-id="181aa-123">Aşağıdaki tabloda, ilgili görev örnekleri listelenir `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="181aa-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="181aa-124">Bitiş</span><span class="sxs-lookup"><span data-stu-id="181aa-124">To</span></span>|<span data-ttu-id="181aa-125">Bkz. </span><span class="sxs-lookup"><span data-stu-id="181aa-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="181aa-126">Uygulama ayarını oku</span><span class="sxs-lookup"><span data-stu-id="181aa-126">Read an application setting</span></span>|[<span data-ttu-id="181aa-127">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="181aa-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="181aa-128">Bir kullanıcı ayarı</span><span class="sxs-lookup"><span data-stu-id="181aa-128">Change a user setting</span></span>|[<span data-ttu-id="181aa-129">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="181aa-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="181aa-130">Kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="181aa-130">Persist user settings</span></span>|[<span data-ttu-id="181aa-131">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="181aa-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="181aa-132">Kullanıcı ayarları için bir özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="181aa-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="181aa-133">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="181aa-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="181aa-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="181aa-134">Example</span></span>  
 <span data-ttu-id="181aa-135">Bu örnek değeri görüntüler `Nickname` ayarı.</span><span class="sxs-lookup"><span data-stu-id="181aa-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="181aa-136">Bu örneğin çalışması, uygulamanız olmalıdır bir `Nickname` biriminin türü `String`.</span><span class="sxs-lookup"><span data-stu-id="181aa-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181aa-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="181aa-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="181aa-138">Nasıl yapılır: Visual Basic'te uygulama ayarlarını okuma</span><span class="sxs-lookup"><span data-stu-id="181aa-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="181aa-139">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="181aa-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="181aa-140">Nasıl yapılır: Visual Basic'te kullanıcı ayarlarını kalıcı yapma</span><span class="sxs-lookup"><span data-stu-id="181aa-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="181aa-141">Nasıl yapılır: Visual Basic'te kullanıcı ayarları için özellik kılavuzu oluşturma</span><span class="sxs-lookup"><span data-stu-id="181aa-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="181aa-142">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="181aa-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
