---
title: 'Nasıl yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
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
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="02dc2-102">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02dc2-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="02dc2-103">`My.Settings` Nesnenin Kullanıcı ayarı özellikleriyle bir <xref:System.Windows.Forms.PropertyGrid> denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02dc2-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02dc2-104">Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02dc2-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="02dc2-105">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="02dc2-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="02dc2-106">`My.Settings` Nesnesi her ayarı bir özellik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="02dc2-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="02dc2-107">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="02dc2-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="02dc2-108">Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama**kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı**kapsamı ayarının özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="02dc2-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="02dc2-109">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="02dc2-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02dc2-110">Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="02dc2-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="02dc2-111">Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı**aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="02dc2-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="02dc2-112">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="02dc2-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="02dc2-113">Bu örnek, `My.Settings` nesnenin <xref:System.Windows.Forms.PropertyGrid> Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır.</span><span class="sxs-lookup"><span data-stu-id="02dc2-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="02dc2-114">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> `My.Settings` nesnesinin tüm özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="02dc2-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="02dc2-115">Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="02dc2-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="02dc2-116">Bu örnek, <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid> öğesinin özelliğini yalnızca Kullanıcı ayarı <xref:System.Configuration.UserScopedSettingAttribute> özelliklerini görüntüleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="02dc2-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="02dc2-117">Kullanıcı ayarı Özellik Kılavuzu eklemek için</span><span class="sxs-lookup"><span data-stu-id="02dc2-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="02dc2-118">Araç kutusundan **PropertyGrid** denetimini uygulamanızın tasarım **Toolbox** yüzeyine ekleyin, burada kabul edilir `Form1`.</span><span class="sxs-lookup"><span data-stu-id="02dc2-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="02dc2-119">Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="02dc2-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="02dc2-120">Form yükleme olay işleyicisi için kodu açmak `Form1` üzere tasarım yüzeyine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="02dc2-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="02dc2-121">`My.Settings` Nesne, Özellik kılavuzu için seçilen nesne olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="02dc2-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="02dc2-122">Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="02dc2-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="02dc2-123">Yalnızca uygulama kapsamı ayarlarını göstermek için yerine <xref:System.Configuration.ApplicationScopedSettingAttribute> özniteliğini kullanın. <xref:System.Configuration.UserScopedSettingAttribute></span><span class="sxs-lookup"><span data-stu-id="02dc2-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="02dc2-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="02dc2-124">Robust Programming</span></span>  

 <span data-ttu-id="02dc2-125">Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="02dc2-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="02dc2-126">Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="02dc2-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="02dc2-127">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)getirme.</span><span class="sxs-lookup"><span data-stu-id="02dc2-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02dc2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02dc2-128">See also</span></span>

- [<span data-ttu-id="02dc2-129">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="02dc2-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="02dc2-130">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="02dc2-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="02dc2-131">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="02dc2-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="02dc2-132">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="02dc2-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="02dc2-133">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="02dc2-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
