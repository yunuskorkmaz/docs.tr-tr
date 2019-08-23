---
title: 'Nasıl yapılır: Windows Forms’da Nesneleri Katmanlara Ayırma'
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
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966533"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="0c5bc-102">Nasıl yapılır: Windows Forms’da Nesneleri Katmanlara Ayırma</span><span class="sxs-lookup"><span data-stu-id="0c5bc-102">How to: Layer Objects on Windows Forms</span></span>
<span data-ttu-id="0c5bc-103">Karmaşık bir kullanıcı arabirimi oluşturduğunuzda veya birden çok belge arabirimi (MDI) formuyla çalışıyorsanız, genellikle daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için hem denetimleri hem de alt formları katman halinde katman yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="0c5bc-104">Bir grup bağlamı içinde denetimleri ve pencereleri taşımak ve izlemek için z sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-104">To move and keep track of controls and windows within the context of a group, you manipulate their z-order.</span></span> <span data-ttu-id="0c5bc-105">*Z düzeni* , formun Z ekseni (derinlik) üzerinde bir formdaki denetimlerin görsel katmandır.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-105">*Z-order* is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="0c5bc-106">Z düzeninin en üstündeki pencere diğer tüm pencereler ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="0c5bc-107">Diğer tüm pencereler, z düzeninin alt kısmındaki pencereyle çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="0c5bc-108">Tasarım zamanında katman denetimlerine</span><span class="sxs-lookup"><span data-stu-id="0c5bc-108">To layer controls at design time</span></span>

1. <span data-ttu-id="0c5bc-109">Katman yapmak istediğiniz bir denetim seçin.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-109">Select a control that you want to layer.</span></span>

2. <span data-ttu-id="0c5bc-110">**Biçim** menüsünde, **Düzen**' in üzerine gelin ve ardından **öne getir** veya **geri gönder**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-110">On the **Format** menu, point to **Order**, and then click **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="0c5bc-111">Denetimleri programlı olarak katman halinde</span><span class="sxs-lookup"><span data-stu-id="0c5bc-111">To layer controls programmatically</span></span>

- <span data-ttu-id="0c5bc-112">Denetimlerin z düzenini <xref:System.Windows.Forms.Control.SendToBack%2A> değiştirmek için veyöntemlerinikullanın.<xref:System.Windows.Forms.Control.BringToFront%2A></span><span class="sxs-lookup"><span data-stu-id="0c5bc-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

     <span data-ttu-id="0c5bc-113">Örneğin, bir <xref:System.Windows.Forms.TextBox> `txtFirstName`denetim başka bir denetimin altında ise ve en üstte olmasını istiyorsanız aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0c5bc-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

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
> <span data-ttu-id="0c5bc-114">Windows Forms *Denetim kapsamayı*destekler.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="0c5bc-115">Denetim kapsama, bir <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.GroupBox> denetim içindeki denetim sayısı gibi, kapsayan bir denetim içinde çok sayıda denetim yerleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="0c5bc-116">Daha sonra, içeren denetim içindeki denetimleri katmandan yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="0c5bc-117">Grup kutusunun taşınması, içinde olduklarından, denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c5bc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c5bc-118">See also</span></span>

- [<span data-ttu-id="0c5bc-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0c5bc-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0c5bc-120">Windows Forms’da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0c5bc-120">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="0c5bc-121">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="0c5bc-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="0c5bc-122">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="0c5bc-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="0c5bc-123">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="0c5bc-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
