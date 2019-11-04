---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459580"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a><span data-ttu-id="64fae-102">İzlenecek yol: akıllı etiketleri kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="64fae-102">Walkthrough: Perform Common Tasks Using Smart Tags</span></span>

<span data-ttu-id="64fae-103">Windows Forms uygulamanız için form ve denetimler oluştururken, defalarca gerçekleştireceğiniz birçok görev vardır.</span><span class="sxs-lookup"><span data-stu-id="64fae-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="64fae-104">Bunlar, karşılaştığınız yaygın olarak gerçekleştirilen görevlerden bazılarıdır:</span><span class="sxs-lookup"><span data-stu-id="64fae-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="64fae-105"><xref:System.Windows.Forms.TabControl>sekme ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="64fae-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="64fae-106">Bir denetimi üst öğesine yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="64fae-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="64fae-107"><xref:System.Windows.Forms.SplitContainer> denetiminin yönünü değiştirme.</span><span class="sxs-lookup"><span data-stu-id="64fae-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="64fae-108">Geliştirme hızını artırmak için, birçok denetim, tasarım zamanında tek bir hareket halinde gibi genel görevleri gerçekleştirmenize imkan tanıyan, içeriğe duyarlı menüler sunan akıllı etiketler sunar.</span><span class="sxs-lookup"><span data-stu-id="64fae-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="64fae-109">Bu görevlere *akıllı etiket fiilleri*denir.</span><span class="sxs-lookup"><span data-stu-id="64fae-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="64fae-110">Akıllı Etiketler, tasarımcıda ömrü boyunca bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64fae-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="64fae-111">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="64fae-111">Create the project</span></span>

<span data-ttu-id="64fae-112">İlk adım projeyi oluşturmak ve formu kurmak olur.</span><span class="sxs-lookup"><span data-stu-id="64fae-112">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="64fae-113">Visual Studio 'da, **Smarttagsexörnek**adlı bir Windows tabanlı uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64fae-113">In Visual Studio, create a Windows-based application project called **SmartTagsExample**.</span></span>

2. <span data-ttu-id="64fae-114">**Windows Form Tasarımcısı**formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="64fae-114">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="64fae-115">Akıllı etiketleri kullanma</span><span class="sxs-lookup"><span data-stu-id="64fae-115">Use smart tags</span></span>

<span data-ttu-id="64fae-116">Akıllı Etiketler, bunları sunan denetimlerde her zaman tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64fae-116">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="64fae-117">**Araç kutusundan** bir <xref:System.Windows.Forms.TabControl> form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-117">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="64fae-118"><xref:System.Windows.Forms.TabControl>tarafında görüntülenen akıllı etiket kabartmasını (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif)) unutmayın.</span><span class="sxs-lookup"><span data-stu-id="64fae-118">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif)) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="64fae-119">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="64fae-119">Click the smart-tag glyph.</span></span> <span data-ttu-id="64fae-120">Glifin yanında görünen kısayol menüsünde **sekme öğesi Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="64fae-120">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="64fae-121"><xref:System.Windows.Forms.TabControl>yeni bir sekme sayfasının eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-121">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="64fae-122">**Araç kutusundan** bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-122">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="64fae-123">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="64fae-123">Click the smart-tag glyph.</span></span> <span data-ttu-id="64fae-124">Glifin yanında görünen kısayol menüsünde, **sütun Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="64fae-124">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="64fae-125"><xref:System.Windows.Forms.TableLayoutPanel> denetimine yeni bir sütun eklendiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-125">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="64fae-126">**Araç kutusundan** bir <xref:System.Windows.Forms.SplitContainer> denetimini formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-126">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="64fae-127">Akıllı etiket glifi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="64fae-127">Click the smart-tag glyph.</span></span> <span data-ttu-id="64fae-128">Glifin yanında görünen kısayol menüsünde **yatay Bölümlendirici yön** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="64fae-128">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="64fae-129"><xref:System.Windows.Forms.SplitContainer> denetiminin Bölümlendirici çubuğunun artık yatay olarak yönlendirildiğini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="64fae-129">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="64fae-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64fae-130">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
