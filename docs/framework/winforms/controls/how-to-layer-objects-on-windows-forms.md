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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e4c6a3236b3a2a2afaad73fee21c3cf59b992b8
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987560"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="19f20-102">Nasıl yapılır: Windows Forms katman nesneleri</span><span class="sxs-lookup"><span data-stu-id="19f20-102">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="19f20-103">Karmaşık bir kullanıcı arabirimi oluşturduğunuzda veya birden çok belge arabirimi (MDI) formuyla çalışıyorsanız, genellikle daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için hem denetimleri hem de alt formları katman halinde katman yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="19f20-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="19f20-104">Bir grup bağlamı içinde denetimleri ve pencereleri taşımak ve izlemek için *z sırasını*değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19f20-104">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="19f20-105">Z düzeni, formun z ekseni (derinlik) üzerinde bir formdaki denetimlerin görsel katmandır.</span><span class="sxs-lookup"><span data-stu-id="19f20-105">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="19f20-106">Z düzeninin en üstündeki pencere diğer tüm pencereler ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="19f20-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="19f20-107">Diğer tüm pencereler, z düzeninin alt kısmındaki pencereyle çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="19f20-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="19f20-108">Tasarım zamanında katman denetimlerine</span><span class="sxs-lookup"><span data-stu-id="19f20-108">To layer controls at design time</span></span>

1. <span data-ttu-id="19f20-109">Visual Studio 'da, katman yapmak istediğiniz bir denetim seçin.</span><span class="sxs-lookup"><span data-stu-id="19f20-109">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="19f20-110">**Biçim** menüsünde, **sipariş**' i seçin ve ardından **öne getir** veya **geri gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="19f20-110">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="19f20-111">Denetimleri programlı olarak katman halinde</span><span class="sxs-lookup"><span data-stu-id="19f20-111">To layer controls programmatically</span></span>

<span data-ttu-id="19f20-112">Denetimlerin z düzenini <xref:System.Windows.Forms.Control.SendToBack%2A> değiştirmek için veyöntemlerinikullanın.<xref:System.Windows.Forms.Control.BringToFront%2A></span><span class="sxs-lookup"><span data-stu-id="19f20-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="19f20-113">Örneğin, bir <xref:System.Windows.Forms.TextBox> `txtFirstName`denetim başka bir denetimin altında ise ve en üstte olmasını istiyorsanız aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="19f20-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

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
> <span data-ttu-id="19f20-114">Windows Forms *Denetim kapsamayı*destekler.</span><span class="sxs-lookup"><span data-stu-id="19f20-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="19f20-115">Denetim kapsama, bir <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.GroupBox> denetim içindeki denetim sayısı gibi, kapsayan bir denetim içinde çok sayıda denetim yerleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="19f20-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="19f20-116">Daha sonra, içeren denetim içindeki denetimleri katmandan yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19f20-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="19f20-117">Grup kutusunun taşınması, içinde olduklarından, denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="19f20-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="19f20-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19f20-118">See also</span></span>

- [<span data-ttu-id="19f20-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="19f20-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="19f20-120">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="19f20-120">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="19f20-121">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="19f20-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="19f20-122">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="19f20-122">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
