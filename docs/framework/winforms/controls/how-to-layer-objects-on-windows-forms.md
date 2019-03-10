---
title: "Nasıl yapılır: Windows Forms'ta katman nesneleri"
ms.date: 03/30/2017
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
ms.openlocfilehash: ea97e26d31d2cdda353b6ada554cac27c5b56c62
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719110"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="1822b-102">Nasıl yapılır: Windows Forms'ta katman nesneleri</span><span class="sxs-lookup"><span data-stu-id="1822b-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="1822b-103">Karmaşık kullanıcı arabirimi oluşturmak veya birden çok belge arabirimi (MDI) formla çalışmak, genellikle denetimleri hem daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için alt formları katman isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1822b-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="1822b-104">Taşıma ve denetimleri ve windows Grup bağlamında izlemek için z düzenini yönetmek.</span><span class="sxs-lookup"><span data-stu-id="1822b-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="1822b-105">*Z düzenini* formun z ekseni (ayrıntılı) boyunca bir form üzerinde denetimleri visual katmanlarını olduğu.</span><span class="sxs-lookup"><span data-stu-id="1822b-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="1822b-106">Pencerenin üst kısmında z düzenini, diğer tüm windows ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="1822b-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="1822b-107">Diğer tüm windows pencerenin alt kısmındaki z düzenini çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="1822b-107">All other windows overlap the window at the bottom of the z-order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1822b-108">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="1822b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1822b-109">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1822b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1822b-110">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1822b-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="1822b-111">Tasarım zamanında katman denetimleri</span><span class="sxs-lookup"><span data-stu-id="1822b-111">To layer controls at design time</span></span>  
  
1.  <span data-ttu-id="1822b-112">Katman istediğiniz denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="1822b-112">Select a control that you want to layer.</span></span>  
  
2.  <span data-ttu-id="1822b-113">Üzerinde **biçimi** menüsünde **sipariş**ve ardından **öne** veya **geri gönderme**.</span><span class="sxs-lookup"><span data-stu-id="1822b-113">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>  
  
### <a name="to-layer-controls-programmatically"></a><span data-ttu-id="1822b-114">Katman için programlı denetimler</span><span class="sxs-lookup"><span data-stu-id="1822b-114">To layer controls programmatically</span></span>  
  
-   <span data-ttu-id="1822b-115">Kullanım <xref:System.Windows.Forms.Control.BringToFront%2A> ve <xref:System.Windows.Forms.Control.SendToBack%2A> denetimlerinin z düzenini yönetmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="1822b-115">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>  
  
     <span data-ttu-id="1822b-116">Örneğin, bir <xref:System.Windows.Forms.TextBox> denetimi `txtFirstName`, olan altındaki başka bir denetim istiyorsanız üstte olması aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1822b-116">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>  
  
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
>  <span data-ttu-id="1822b-117">Windows Forms destekler *denetim kapsama*.</span><span class="sxs-lookup"><span data-stu-id="1822b-117">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="1822b-118">Denetim kapsamı içeren bir dizi gibi bir dizi içeren bir denetimi içindeki denetimler yerleştirme <xref:System.Windows.Forms.RadioButton> içinde denetleyen bir <xref:System.Windows.Forms.GroupBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="1822b-118">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="1822b-119">Ardından, içeren denetimi içindeki denetimler katmanlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1822b-119">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="1822b-120">Grup kutusu taşıma, bunlar içinde yer aldığından, denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="1822b-120">Moving the group box moves the controls as well, because they are contained inside it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1822b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1822b-121">See also</span></span>
- [<span data-ttu-id="1822b-122">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="1822b-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="1822b-123">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1822b-123">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="1822b-124">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="1822b-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="1822b-125">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="1822b-125">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="1822b-126">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="1822b-126">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
