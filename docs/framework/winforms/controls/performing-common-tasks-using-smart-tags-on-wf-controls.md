---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015759"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="e90be-102">İzlenecek yol: Akıllı etiketleri kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e90be-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="e90be-103">Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır.</span><span class="sxs-lookup"><span data-stu-id="e90be-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="e90be-104">Bunlar, karşılaştığınız yaygın olarak gerçekleştirilen görevlerden bazılarıdır:</span><span class="sxs-lookup"><span data-stu-id="e90be-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="e90be-105">Bir <xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="e90be-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="e90be-106">Bir denetimi üst öğesine yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="e90be-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="e90be-107">Bir <xref:System.Windows.Forms.SplitContainer> denetimin yönünü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e90be-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="e90be-108">Geliştirme hızını artırmak için, birçok denetim, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize imkan tanıyan, içeriğe duyarlı menüler sunan akıllı etiketler sunar.</span><span class="sxs-lookup"><span data-stu-id="e90be-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="e90be-109">Bu görevlere *akıllı etiket fiilleri*denir.</span><span class="sxs-lookup"><span data-stu-id="e90be-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="e90be-110">Akıllı Etiketler, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e90be-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="e90be-111">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e90be-111">Create the project</span></span>

<span data-ttu-id="e90be-112">İlk adım projeyi oluşturmak ve formu kurmak olur.</span><span class="sxs-lookup"><span data-stu-id="e90be-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="e90be-113">Visual Studio 'da, **Smarttagsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e90be-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="e90be-114">**Windows Form Tasarımcısı**formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e90be-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="e90be-115">Akıllı etiketleri kullanma</span><span class="sxs-lookup"><span data-stu-id="e90be-115">Use smart tags</span></span>

<span data-ttu-id="e90be-116">Akıllı Etiketler, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e90be-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="e90be-117"><xref:System.Windows.Forms.TabControl> **Araç kutusundan** bir öğesini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="e90be-118">Öğesinin![tarafındagörüntülenen](./media/vs-winformsmttagglyph.gif)akıllı etiket karakterini (akıllı etiket karakter) unutmayın. <xref:System.Windows.Forms.TabControl></span><span class="sxs-lookup"><span data-stu-id="e90be-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="e90be-119">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e90be-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="e90be-120">Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e90be-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="e90be-121">Yeni bir sekme sayfasının öğesine <xref:System.Windows.Forms.TabControl>eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="e90be-122"><xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="e90be-123">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e90be-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="e90be-124">Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e90be-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="e90be-125"><xref:System.Windows.Forms.TableLayoutPanel> Denetime yeni bir sütun eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="e90be-126"><xref:System.Windows.Forms.SplitContainer> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="e90be-127">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e90be-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="e90be-128">Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e90be-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="e90be-129"><xref:System.Windows.Forms.SplitContainer> Denetimin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="e90be-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="e90be-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e90be-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
