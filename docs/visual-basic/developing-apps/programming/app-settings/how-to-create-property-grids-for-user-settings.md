---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Visual Basic Kullanıcı ayarları için özellik kılavuzları oluşturma'
title: 'Nasıl yapılır: Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 19523f712207cac225ccf68e02e338a9e76fe358
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797854"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="d467f-103">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d467f-103">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="d467f-104"><xref:System.Windows.Forms.PropertyGrid>Nesnenin Kullanıcı ayarı özellikleriyle bir denetim doldurarak Kullanıcı ayarları için özellik Kılavuzu oluşturabilirsiniz `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="d467f-104">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d467f-105">Bu örneğin çalışması için, uygulamanız kullanıcı ayarlarının yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d467f-105">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="d467f-106">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d467f-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="d467f-107">`My.Settings`Nesnesi her ayarı bir özellik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d467f-107">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="d467f-108">Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d467f-108">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="d467f-109">Ayarın **kapsamı** , özelliğin salt okunurdur belirler; bir **uygulama** kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı** kapsamı ayarının özelliği okuma-yazma olur.</span><span class="sxs-lookup"><span data-stu-id="d467f-109">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="d467f-110">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="d467f-110">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d467f-111">Çalışma zamanında uygulama kapsamı ayarlarının değerlerini değiştiremez veya kaydedemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d467f-111">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="d467f-112">Uygulama kapsamı ayarları yalnızca uygulama oluşturulurken ( **Proje Tasarımcısı** aracılığıyla) veya uygulamanın yapılandırma dosyası düzenlenerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d467f-112">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="d467f-113">Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d467f-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="d467f-114">Bu örnek, <xref:System.Windows.Forms.PropertyGrid> nesnenin Kullanıcı ayarı özelliklerine erişmek için bir denetim kullanır `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="d467f-114">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="d467f-115">Varsayılan olarak, <xref:System.Windows.Forms.PropertyGrid> nesnesinin tüm özelliklerini gösterir `My.Settings` .</span><span class="sxs-lookup"><span data-stu-id="d467f-115">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="d467f-116">Ancak, Kullanıcı ayarı özelliklerinin <xref:System.Configuration.UserScopedSettingAttribute> özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="d467f-116">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="d467f-117">Bu örnek <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> , öğesinin özelliğini <xref:System.Windows.Forms.PropertyGrid> <xref:System.Configuration.UserScopedSettingAttribute> yalnızca Kullanıcı ayarı özelliklerini görüntüleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d467f-117">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="d467f-118">Kullanıcı ayarı Özellik Kılavuzu eklemek için</span><span class="sxs-lookup"><span data-stu-id="d467f-118">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="d467f-119">**Araç kutusundan** **PropertyGrid** denetimini uygulamanızın tasarım yüzeyine ekleyin, burada kabul edilir `Form1` .</span><span class="sxs-lookup"><span data-stu-id="d467f-119">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="d467f-120">Özellik Kılavuzu denetiminin varsayılan adı `PropertyGrid1` .</span><span class="sxs-lookup"><span data-stu-id="d467f-120">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="d467f-121">`Form1`Form yükleme olay işleyicisi için kodu açmak üzere tasarım yüzeyine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d467f-121">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="d467f-122">Nesne, `My.Settings` Özellik kılavuzu için seçilen nesne olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d467f-122">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="d467f-123">Özellik kılavuzunu yalnızca Kullanıcı ayarlarını gösterecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d467f-123">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="d467f-124">Yalnızca uygulama kapsamı ayarlarını göstermek için <xref:System.Configuration.ApplicationScopedSettingAttribute> yerine özniteliğini kullanın  <xref:System.Configuration.UserScopedSettingAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d467f-124">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d467f-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d467f-125">Robust Programming</span></span>  

 <span data-ttu-id="d467f-126">Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d467f-126">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="d467f-127">Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d467f-127">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="d467f-128">Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](how-to-persist-user-settings.md)getirme.</span><span class="sxs-lookup"><span data-stu-id="d467f-128">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d467f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d467f-129">See also</span></span>

- [<span data-ttu-id="d467f-130">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d467f-130">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="d467f-131">Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma</span><span class="sxs-lookup"><span data-stu-id="d467f-131">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="d467f-132">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d467f-132">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="d467f-133">Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma</span><span class="sxs-lookup"><span data-stu-id="d467f-133">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="d467f-134">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="d467f-134">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
