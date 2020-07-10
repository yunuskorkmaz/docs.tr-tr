---
title: Nesneleri Katmanlama
description: Daha karmaşık kullanıcı arabirimleri oluşturmak için Windows Forms Denetimlerinde ve alt formlarda nesneleri nasıl katmanleyeceğinizi öğrenin.
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
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174516"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="6fbe1-103">Nasıl yapılır: Windows Forms üzerinde katman nesneleri</span><span class="sxs-lookup"><span data-stu-id="6fbe1-103">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="6fbe1-104">Karmaşık bir kullanıcı arabirimi oluşturduğunuzda veya birden çok belge arabirimi (MDI) formuyla çalışıyorsanız, genellikle daha karmaşık kullanıcı arabirimleri (UI) oluşturmak için hem denetimleri hem de alt formları katman halinde katman yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-104">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="6fbe1-105">Bir grup bağlamı içinde denetimleri ve pencereleri taşımak ve izlemek için *z sırasını*değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-105">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="6fbe1-106">Z düzeni, formun z ekseni (derinlik) üzerinde bir formdaki denetimlerin görsel katmandır.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-106">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="6fbe1-107">Z düzeninin en üstündeki pencere diğer tüm pencereler ile çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-107">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="6fbe1-108">Diğer tüm pencereler, z düzeninin alt kısmındaki pencereyle çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-108">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="6fbe1-109">Tasarım zamanında katman denetimlerine</span><span class="sxs-lookup"><span data-stu-id="6fbe1-109">To layer controls at design time</span></span>

1. <span data-ttu-id="6fbe1-110">Visual Studio 'da, katman yapmak istediğiniz bir denetim seçin.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-110">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="6fbe1-111">**Biçim** menüsünde, **sipariş**' i seçin ve ardından **öne getir** veya **geri gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-111">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="6fbe1-112">Denetimleri programlı olarak katman halinde</span><span class="sxs-lookup"><span data-stu-id="6fbe1-112">To layer controls programmatically</span></span>

<span data-ttu-id="6fbe1-113"><xref:System.Windows.Forms.Control.BringToFront%2A> <xref:System.Windows.Forms.Control.SendToBack%2A> Denetimlerin z düzenini değiştirmek için ve yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-113">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="6fbe1-114">Örneğin, bir <xref:System.Windows.Forms.TextBox> Denetim `txtFirstName` başka bir denetimin altında ise ve en üstte olmasını istiyorsanız aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="6fbe1-114">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

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
> <span data-ttu-id="6fbe1-115">Windows Forms *Denetim kapsamayı*destekler.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-115">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="6fbe1-116">Denetim kapsama, bir denetim içindeki denetim sayısı gibi, kapsayan bir denetim içinde çok sayıda denetim yerleştirmeyi içerir <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.GroupBox> .</span><span class="sxs-lookup"><span data-stu-id="6fbe1-116">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="6fbe1-117">Daha sonra, içeren denetim içindeki denetimleri katmandan yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-117">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="6fbe1-118">Grup kutusunun taşınması, içinde olduklarından, denetimleri de taşır.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-118">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbe1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fbe1-119">See also</span></span>

- [<span data-ttu-id="6fbe1-120">Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="6fbe1-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="6fbe1-121">Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma</span><span class="sxs-lookup"><span data-stu-id="6fbe1-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="6fbe1-122">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="6fbe1-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="6fbe1-123">İşleve Göre Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="6fbe1-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
