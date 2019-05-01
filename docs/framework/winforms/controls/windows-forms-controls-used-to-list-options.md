---
title: Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, listing options
- option lists in Windows Forms
ms.assetid: 5bc064c7-bc1f-4b62-8f4b-252f864b118e
ms.openlocfilehash: 92d5f330fbd5269e15bf52dc11ad998939aa18e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009077"
---
# <a name="windows-forms-controls-used-to-list-options"></a><span data-ttu-id="e7600-102">Seçenekleri Listelemede Kullanılan Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="e7600-102">Windows Forms Controls Used to List Options</span></span>
<span data-ttu-id="e7600-103">Kullanıcılara bir seçenek yelpazesinden listesi sağlamak istiyorsanız Windows Form çeşitli denetimlere ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7600-103">You can add a variety of controls to a Windows Form if you want to provide users with a list of options to choose from.</span></span> <span data-ttu-id="e7600-104">Bağlı olarak ne kadar istediğiniz kullanıcılarınızın kısıtlamak input, ekleyebileceğiniz bir <xref:System.Windows.Forms.ListBox> denetimi, bir <xref:System.Windows.Forms.ComboBox> denetimi veya <xref:System.Windows.Forms.CheckedListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e7600-104">Depending on how much you want to restrict your users' input, you can add a <xref:System.Windows.Forms.ListBox> control, a <xref:System.Windows.Forms.ComboBox> control, or a <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="e7600-105">En iyi hangi denetimin gereksinimlerinize uyan belirlemek için aşağıdaki bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7600-105">Use the following links to determine which control best suits your needs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7600-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e7600-106">In This Section</span></span>  
 [<span data-ttu-id="e7600-107">ListBox Yerine Ne Zaman Windows Forms ComboBox Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="e7600-107">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 <span data-ttu-id="e7600-108">Gereksinimleri ve kısıtlamaları, Windows formunun bağlı olarak, uygun bir liste tabanlı denetim önerir.</span><span class="sxs-lookup"><span data-stu-id="e7600-108">Recommends an appropriate list-based control depending on the needs and restrictions of your Windows Form.</span></span>  
  
 [<span data-ttu-id="e7600-109">Nasıl yapılır: Özel erişim öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="e7600-109">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 <span data-ttu-id="e7600-110">Program aracılığıyla belirli bir konumda listesindeki hangi öğe görünür belirlemek için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7600-110">Gives instructions for programmatically determining which item in a list appears in a given position.</span></span>  
  
 [<span data-ttu-id="e7600-111">Nasıl yapılır: Ekleme ve kaldırma öğeleri bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="e7600-111">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)  
 <span data-ttu-id="e7600-112">Öğe ekleme veya bir denetimin öğeleri listeden kaldırma için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7600-112">Gives instructions for adding or removing items from a control's list of items.</span></span>  
  
 [<span data-ttu-id="e7600-113">Nasıl yapılır: ComboBox, ListBox veya CheckedListBox denetiminde bir Windows Forms için arama tablosu oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7600-113">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](create-a-lookup-table-for-a-wf-combobox-listbox.md)  
 <span data-ttu-id="e7600-114">Görüntüleme ve kullanışlı biçimlerde form verilerini depolamak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7600-114">Gives directions for displaying and storing form data in useful formats.</span></span>  
  
 [<span data-ttu-id="e7600-115">Nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama</span><span class="sxs-lookup"><span data-stu-id="e7600-115">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 <span data-ttu-id="e7600-116">Bir liste tabanlı denetim bir veri kaynağına bağlama için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7600-116">Gives directions for binding a list-based control to a data source.</span></span>  
  
 [<span data-ttu-id="e7600-117">Nasıl yapılır: Sıralama içeriği bir Windows Forms ComboBox, ListBox veya CheckedListBox denetimi</span><span class="sxs-lookup"><span data-stu-id="e7600-117">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 <span data-ttu-id="e7600-118">Veri kaynağında listesi verileri sıralamak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7600-118">Explains how to sort list data at its data source.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e7600-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e7600-119">Reference</span></span>  
 <xref:System.Windows.Forms.CheckedListBox>  
 <span data-ttu-id="e7600-120">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e7600-120">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.ComboBox>  
 <span data-ttu-id="e7600-121">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e7600-121">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.ListBox>  
 <span data-ttu-id="e7600-122">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e7600-122">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7600-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e7600-123">Related Sections</span></span>  
 [<span data-ttu-id="e7600-124">CheckedListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e7600-124">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)  
 <span data-ttu-id="e7600-125">Bu denetimi nedir ve önemli özellikler ve özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7600-125">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e7600-126">ComboBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e7600-126">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)  
 <span data-ttu-id="e7600-127">Bu denetimi nedir ve önemli özellikler ve özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7600-127">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e7600-128">ListBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e7600-128">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)  
 <span data-ttu-id="e7600-129">Bu denetimi nedir ve önemli özellikler ve özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7600-129">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e7600-130">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="e7600-130">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="e7600-131">Windows Forms denetimlerini, tam bir listesi, kullanımları hakkında bilgi için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7600-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
