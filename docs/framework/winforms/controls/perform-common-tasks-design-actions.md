---
title: Denetimlerde tasarımcı eylemlerini kullanarak ortak görevleri gerçekleştirme
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634885"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a><span data-ttu-id="0e597-102">İzlenecek yol: tasarımcı eylemlerini kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0e597-102">Walkthrough: Perform common tasks using designer actions</span></span>

<span data-ttu-id="0e597-103">Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır.</span><span class="sxs-lookup"><span data-stu-id="0e597-103">As you construct forms and controls for your Windows Forms application, there are many tasks you'll perform repeatedly.</span></span> <span data-ttu-id="0e597-104">Aşağıdaki listede, tüm sık gerçekleştirilen görevlerden bazıları gösterilir:</span><span class="sxs-lookup"><span data-stu-id="0e597-104">The following list shows some of the commonly performed tasks you'll come across:</span></span>

- <span data-ttu-id="0e597-105"><xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="0e597-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>
- <span data-ttu-id="0e597-106">Bir denetimi üst öğesine yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="0e597-106">Docking a control to its parent.</span></span>
- <span data-ttu-id="0e597-107"><xref:System.Windows.Forms.SplitContainer> denetiminin yönünü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="0e597-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="0e597-108">Geliştirme hızını artırmak için birçok denetim Tasarımcı eylemleri sunar; bu, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize olanak tanıyan içeriğe duyarlı menüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e597-108">To speed development, many controls offer designer actions, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="0e597-109">Bu görevlere *Tasarımcı eylemleri fiilleri*denir.</span><span class="sxs-lookup"><span data-stu-id="0e597-109">These tasks are called *designer actions verbs*.</span></span>

<span data-ttu-id="0e597-110">Tasarımcı eylemleri, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e597-110">Designer actions remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0e597-111">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e597-111">Create the project</span></span>

<span data-ttu-id="0e597-112">İlk adım projeyi oluşturmak ve formu kurmak olur.</span><span class="sxs-lookup"><span data-stu-id="0e597-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="0e597-113">Visual Studio 'da **Designeractionsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0e597-113">In Visual Studio, create a Windows-based application project called **DesignerActionsExample**.</span></span>

2. <span data-ttu-id="0e597-114">**Windows Form Tasarımcısı**formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="0e597-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-designer-actions"></a><span data-ttu-id="0e597-115">Tasarımcı eylemlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0e597-115">Use designer actions</span></span>

<span data-ttu-id="0e597-116">Tasarımcı eylemleri, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e597-116">Designer actions are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="0e597-117">**Araç kutusundan** bir <xref:System.Windows.Forms.TabControl> form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="0e597-118"><xref:System.Windows.Forms.TabControl>tarafında görüntülenen tasarımcı eylemleri glifin (![küçük siyah ok](./media/designer-actions-glyph.gif)) not edin.</span><span class="sxs-lookup"><span data-stu-id="0e597-118">Note the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="0e597-119">Tasarımcı eylemleri glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0e597-119">Click the designer actions glyph.</span></span> <span data-ttu-id="0e597-120">Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0e597-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="0e597-121"><xref:System.Windows.Forms.TabControl>yeni bir sekme sayfasının eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="0e597-122">**Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="0e597-123">Tasarımcı eylemleri glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0e597-123">Click the designer actions glyph.</span></span> <span data-ttu-id="0e597-124">Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0e597-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="0e597-125"><xref:System.Windows.Forms.TableLayoutPanel> denetimine yeni bir sütun eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="0e597-126">**Araç kutusundan** bir <xref:System.Windows.Forms.SplitContainer> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="0e597-127">Tasarımcı eylemleri glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0e597-127">Click the designer actions glyph.</span></span> <span data-ttu-id="0e597-128">Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="0e597-128">In the shortcut menu that appears next to the glyph, select the **Horizontal Splitter Orientation** item.</span></span> <span data-ttu-id="0e597-129"><xref:System.Windows.Forms.SplitContainer> denetiminin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="0e597-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e597-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e597-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
