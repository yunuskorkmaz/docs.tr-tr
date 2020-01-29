---
title: Nesneleri Katmanlama
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1615b9c4df222edd95cda9bceae622ba6f1d8d78
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736343"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="90051-102">Nasıl yapılır: Windows Forms üzerinde katman nesneleri</span><span class="sxs-lookup"><span data-stu-id="90051-102">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="90051-103">Karmaşık bir kullanıcı arabirimi oluşturduğunuzda veya birden çok belge arabirimi (MDI) formuyla çalışıyorsanız, genellikle daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için hem denetimleri hem de alt formları katman halinde katman yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="90051-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="90051-104">Bir grup bağlamı içinde denetimleri ve pencereleri taşımak ve izlemek için *z sırasını*değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90051-104">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="90051-105">Z düzeni, formun z ekseni (derinlik) üzerinde bir formdaki denetimlerin görsel katmandır.</span><span class="sxs-lookup"><span data-stu-id="90051-105">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="90051-106">Z düzeninin en üstündeki pencere diğer tüm pencereler ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="90051-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="90051-107">Diğer tüm pencereler, z düzeninin alt kısmındaki pencereyle çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="90051-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="90051-108">Tasarım zamanında katman denetimlerine</span><span class="sxs-lookup"><span data-stu-id="90051-108">To layer controls at design time</span></span>

1. <span data-ttu-id="90051-109">Visual Studio 'da, katman yapmak istediğiniz bir denetim seçin.</span><span class="sxs-lookup"><span data-stu-id="90051-109">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="90051-110">**Biçim** menüsünde, **sipariş**' i seçin ve ardından **öne getir** veya **geri gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="90051-110">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="90051-111">Denetimleri programlı olarak katman halinde</span><span class="sxs-lookup"><span data-stu-id="90051-111">To layer controls programmatically</span></span>

<span data-ttu-id="90051-112">Denetimlerin z düzenini değiştirmek için <xref:System.Windows.Forms.Control.BringToFront%2A> ve <xref:System.Windows.Forms.Control.SendToBack%2A> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="90051-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="90051-113">Örneğin, `txtFirstName`bir <xref:System.Windows.Forms.TextBox> denetimi başka bir denetimin altında ve en üstte olmasını istiyorsanız aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="90051-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

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
> <span data-ttu-id="90051-114">Windows Forms *Denetim kapsamayı*destekler.</span><span class="sxs-lookup"><span data-stu-id="90051-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="90051-115">Denetim kapsama, bir <xref:System.Windows.Forms.GroupBox> denetimindeki birçok <xref:System.Windows.Forms.RadioButton> denetimi gibi, kapsayan bir denetim içinde çok sayıda denetim yerleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="90051-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="90051-116">Daha sonra, içeren denetim içindeki denetimleri katmandan yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90051-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="90051-117">Grup kutusunun taşınması, içinde olduklarından, denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="90051-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="90051-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90051-118">See also</span></span>

- [<span data-ttu-id="90051-119">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="90051-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="90051-120">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="90051-120">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="90051-121">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="90051-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="90051-122">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="90051-122">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
