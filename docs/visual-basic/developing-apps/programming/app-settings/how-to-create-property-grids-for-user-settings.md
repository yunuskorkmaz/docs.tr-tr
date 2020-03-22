---
title: 'Nasıl Yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329607"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="6876e-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6876e-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="6876e-103">Nesnenin kullanıcı ayar özellikleri ile bir <xref:System.Windows.Forms.PropertyGrid> denetim doldurma tarafından kullanıcı ayarları için bir özellik ızgarası oluşturabilirsiniz. `My.Settings`</span><span class="sxs-lookup"><span data-stu-id="6876e-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6876e-104">Bu örneğin çalışabilmesi için uygulamanızın kullanıcı ayarlarını yapılandırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6876e-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="6876e-105">Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6876e-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="6876e-106">Nesne `My.Settings` her ayarı bir özellik olarak ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6876e-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="6876e-107">Özellik adı ayar adı ile aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6876e-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="6876e-108">Ayarın **Kapsamı** özelliğin salt okunup okunmayalı olduğunu belirler; **Bir Uygulama**-kapsam ayarı için özellik salt okunurken, **Kullanıcı-kapsam**ayarı özelliği okuma-yazma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="6876e-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="6876e-109">Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.</span><span class="sxs-lookup"><span data-stu-id="6876e-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6876e-110">Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6876e-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="6876e-111">Uygulama kapsamı ayarları yalnızca uygulamayı oluştururken **(Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyasını düzenleyerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6876e-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="6876e-112">Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6876e-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="6876e-113">Bu örnek, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnenin kullanıcı ayar özelliklerine erişmek için bir denetim kullanır.</span><span class="sxs-lookup"><span data-stu-id="6876e-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="6876e-114">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnenin tüm özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6876e-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="6876e-115">Ancak, kullanıcı ayar özellikleri <xref:System.Configuration.UserScopedSettingAttribute> özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6876e-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="6876e-116">Bu örnek, <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> yalnızca <xref:System.Windows.Forms.PropertyGrid> kullanıcı <xref:System.Configuration.UserScopedSettingAttribute> ayar özelliklerini görüntülemek için özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6876e-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="6876e-117">Kullanıcı ayar özelliği ızgarası eklemek için</span><span class="sxs-lookup"><span data-stu-id="6876e-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="6876e-118">**Toolbox'tan** **PropertyGrid** denetimini uygulamanız için tasarım yüzeyine `Form1`ekleyin, burada olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="6876e-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="6876e-119">Özellik-ızgara denetiminin varsayılan `PropertyGrid1`adı.</span><span class="sxs-lookup"><span data-stu-id="6876e-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="6876e-120">Form yükleme olay işleyicisinin kodunu açmak için `Form1` tasarım yüzeyini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="6876e-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="6876e-121">Nesneyi `My.Settings` özellik ızgarası için seçili nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6876e-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="6876e-122">Özellik ızgarasını yalnızca kullanıcı ayarlarını gösterecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="6876e-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="6876e-123">Yalnızca uygulama kapsamı ayarlarını göstermek <xref:System.Configuration.ApplicationScopedSettingAttribute> için, <xref:System.Configuration.UserScopedSettingAttribute>özniteliği yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="6876e-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6876e-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6876e-124">Robust Programming</span></span>  

 <span data-ttu-id="6876e-125">Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6876e-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="6876e-126">Ayarları hemen kaydetmek için `My.Settings.Save` yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="6876e-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="6876e-127">Daha fazla bilgi için [bkz: Visual Basic'te Kullanıcı Ayarlarını Devam](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)Edin.</span><span class="sxs-lookup"><span data-stu-id="6876e-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6876e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6876e-128">See also</span></span>

- [<span data-ttu-id="6876e-129">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="6876e-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="6876e-130">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="6876e-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="6876e-131">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6876e-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="6876e-132">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="6876e-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="6876e-133">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="6876e-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
