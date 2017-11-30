---
title: "Nasıl yapılır: Windows Formlarında Nesneleri Katmanlara Ayırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda4cb3641ff890646614af35d38ff13621cc16b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="ec654-102">Nasıl yapılır: Windows Formlarında Nesneleri Katmanlara Ayırma</span><span class="sxs-lookup"><span data-stu-id="ec654-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="ec654-103">Karmaşık kullanıcı arabirimi oluşturma ya da birden çok belge arabirimi (MDI) formla çalışmak genellikle denetimleri ve daha karmaşık kullanıcı arabirimi (UI) oluşturmak için alt formları katman isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ec654-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="ec654-104">Taşıma ve denetimleri ve windows Grup bağlamında izlemek için bunların z düzenini yönetme.</span><span class="sxs-lookup"><span data-stu-id="ec654-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="ec654-105">*Z düzeni* formun z ekseni (derinlik) boyunca bir form üzerinde denetimleri görsel katmanlarını değil.</span><span class="sxs-lookup"><span data-stu-id="ec654-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="ec654-106">Pencerenin üst kısmındaki z düzenini diğer tüm windows çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="ec654-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="ec654-107">Diğer tüm windows pencerenin alt kısmındaki z düzenini çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="ec654-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec654-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ec654-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ec654-109">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ec654-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ec654-110">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ec654-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="ec654-111">Tasarım zamanında katman denetimleri için</span><span class="sxs-lookup"><span data-stu-id="ec654-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="ec654-112">Katman istediğiniz bir denetim seçin.</span><span class="sxs-lookup"><span data-stu-id="ec654-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="ec654-113">Üzerinde **biçimi** menüsündeki **sipariş**ve ardından **öne** veya **geri göndermek**.</span><span class="sxs-lookup"><span data-stu-id="ec654-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="ec654-114">Katman için program aracılığıyla denetler</span><span class="sxs-lookup"><span data-stu-id="ec654-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="ec654-115">Kullanım <xref:System.Windows.Forms.Control.BringToFront%2A> ve <xref:System.Windows.Forms.Control.SendToBack%2A> denetimlerinin z sıralamasını değiştirmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ec654-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="ec654-116">Örneğin, bir <xref:System.Windows.Forms.TextBox> denetimi `txtFirstName`, olan altındaki başka bir denetim ve istediğinizde üstte yoksa, aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec654-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="ec654-117">Windows Forms destekleyen *kontrol kapsama*.</span><span class="sxs-lookup"><span data-stu-id="ec654-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="ec654-118">Denetimi kapsamasını içeren bir dizi bir dizi gibi içeren bir denetim içinde denetimleri yerleştirme <xref:System.Windows.Forms.RadioButton> içinde denetleyen bir <xref:System.Windows.Forms.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="ec654-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="ec654-119">Ardından içeren denetim içindeki denetimler katman.</span><span class="sxs-lookup"><span data-stu-id="ec654-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="ec654-120">İçinde bulunan olduğundan grup kutusu taşıma denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="ec654-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec654-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec654-121">See Also</span></span>  
 [<span data-ttu-id="ec654-122">Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="ec654-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="ec654-123">Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="ec654-123">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="ec654-124">Ayrı Windows Forms denetimlerini etiketleme ve kısayollarını sunma</span><span class="sxs-lookup"><span data-stu-id="ec654-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="ec654-125">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="ec654-125">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="ec654-126">Windows Forms denetimleri işlevi</span><span class="sxs-lookup"><span data-stu-id="ec654-126">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
