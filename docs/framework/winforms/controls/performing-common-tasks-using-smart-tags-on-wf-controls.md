---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: 1cc854d735ba88a301d6e2f6a83fe5c8bf881380
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211414"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="9fb83-102">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="9fb83-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>

<span data-ttu-id="9fb83-103">Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirir çok sayıda görev vardır.</span><span class="sxs-lookup"><span data-stu-id="9fb83-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="9fb83-104">Karşınıza çıkacak sık gerçekleştirilen görevlerin bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9fb83-104">These are some of the commonly performed tasks you will encounter:</span></span>

- <span data-ttu-id="9fb83-105">Ekleyerek veya bir sekme üzerindeki kaldırarak bir <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="9fb83-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>

- <span data-ttu-id="9fb83-106">Bir denetim için üst yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="9fb83-106">Docking a control to its parent.</span></span>

- <span data-ttu-id="9fb83-107">Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9fb83-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>

<span data-ttu-id="9fb83-108">Geliştirme hızlandırmak için pek çok denetimi tasarım zamanında bu tek gibi genel görevleri gerçekleştirmenize olanak tanıyan bağlama duyarlı menüler şunlardır akıllı etiketler sunar.</span><span class="sxs-lookup"><span data-stu-id="9fb83-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="9fb83-109">Bu görevleri adlı *akıllı etiket fiilleri*.</span><span class="sxs-lookup"><span data-stu-id="9fb83-109">These tasks are called *smart-tag verbs*.</span></span>

<span data-ttu-id="9fb83-110">Akıllı etiketler Tasarımcısı'nda yaşam süresi'için bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb83-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>

<span data-ttu-id="9fb83-111">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="9fb83-111">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="9fb83-112">Bir Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fb83-112">Creating a Windows Forms project</span></span>

- <span data-ttu-id="9fb83-113">Akıllı etiketleri kullanarak</span><span class="sxs-lookup"><span data-stu-id="9fb83-113">Using smart tags</span></span>

- <span data-ttu-id="9fb83-114">Akıllı etiketler devre dışı bırakma ve etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9fb83-114">Enabling and Disabling Smart Tags</span></span>

<span data-ttu-id="9fb83-115">İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="9fb83-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="9fb83-116">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fb83-116">Create the project</span></span>

<span data-ttu-id="9fb83-117">İlk adım projeyi oluşturmak ve formu ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9fb83-117">The first step is to create the project and set up the form.</span></span>

1. <span data-ttu-id="9fb83-118">Visual Studio'da "SmartTagsExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).</span><span class="sxs-lookup"><span data-stu-id="9fb83-118">In Visual Studio, create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="9fb83-119">Formda seçin **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="9fb83-119">Select the form in the **Windows Forms Designer**.</span></span>

## <a name="use-smart-tags"></a><span data-ttu-id="9fb83-120">Akıllı etiketler kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fb83-120">Use smart tags</span></span>

<span data-ttu-id="9fb83-121">Akıllı etiketler her zaman bunları teklif denetimleri tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb83-121">Smart tags are always available at design time on controls that offer them.</span></span>

1. <span data-ttu-id="9fb83-122">Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="9fb83-122">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="9fb83-123">Akıllı etiket karakterini unutmayın (![akıllı etiket karakterini](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) üzerinde yan, görüntülenen <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="9fb83-123">Note the smart-tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>

2. <span data-ttu-id="9fb83-124">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fb83-124">Click the smart-tag glyph.</span></span> <span data-ttu-id="9fb83-125">Glif yanında görüntülenen kısayol menüsünden seçin **Sekme Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fb83-125">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="9fb83-126">Yeni bir sekme sayfası eklenir gözlemleyin <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="9fb83-126">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>

3. <span data-ttu-id="9fb83-127">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="9fb83-127">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

4. <span data-ttu-id="9fb83-128">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fb83-128">Click the smart-tag glyph.</span></span> <span data-ttu-id="9fb83-129">Glif yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fb83-129">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="9fb83-130">Yeni bir sütun eklenir gözlemleyin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9fb83-130">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

5. <span data-ttu-id="9fb83-131">Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="9fb83-131">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>

6. <span data-ttu-id="9fb83-132">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9fb83-132">Click the smart-tag glyph.</span></span> <span data-ttu-id="9fb83-133">Glif yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi.</span><span class="sxs-lookup"><span data-stu-id="9fb83-133">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="9fb83-134">Mesajının görüntülendiğini görün <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı, artık yatay odaklıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb83-134">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fb83-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fb83-135">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
- <span data-ttu-id="9fb83-136">[İzlenecek yol: Bir Windows Formları bileşenine akıllı etiket ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9fb83-136">[Walkthrough: Adding Smart Tags to a Windows Forms Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171829(v=vs.120))</span></span>
