---
title: "DomainUpDown Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5a86dc6c56c3afff8d8a3a4ca2c5d5efa8eac1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="95660-102">DomainUpDown Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="95660-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="95660-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimidir aslında bir metin kutusu bileşimini ve listesini yukarı veya aşağı taşıma için düğmeler çifti.</span><span class="sxs-lookup"><span data-stu-id="95660-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="95660-104">Denetim görüntüler ve seçenekler listesinden bir metin dizesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="95660-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="95660-105">Kullanıcı düğmeleri listesini taşımak için yukarı ve aşağı tıklatarak yukarı ve aşağı ok tuşlarına basarak veya listeden bir öğe eşleşen bir dize yazarak dize seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95660-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="95660-106">Öğe adları alfabetik olarak sıralanan bir listesinden seçmek için bu denetim için bir olası kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="95660-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95660-107">Sıralamak için ayarlanmış <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="95660-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="95660-108">Bu denetim işlevi liste kutusu veya birleşik giriş kutusu çok benzer, ancak çok az alanı kaplar.</span><span class="sxs-lookup"><span data-stu-id="95660-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="95660-109">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="95660-109">Key Properties</span></span>  
 <span data-ttu-id="95660-110">Anahtar özellikler denetiminin <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="95660-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="95660-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Özellik metin değerleri denetiminde görüntülenen nesnelerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="95660-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="95660-112">Varsa <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> ayarlanır `false`, kullanıcı türleri ve listesindeki bir değeri ile eşleşen metin denetimi otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="95660-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="95660-113">Varsa <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> ayarlanır `true`, son öğenin kaydırma yönlendirilirsiniz ilk öğeye listesinde ve tersi.</span><span class="sxs-lookup"><span data-stu-id="95660-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="95660-114">Denetimin anahtar yöntemleri <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> ve <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="95660-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="95660-115">Bu denetim yalnızca metin dizelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="95660-115">This control displays only text strings.</span></span> <span data-ttu-id="95660-116">Sayısal değerler görüntüleyen bir denetim istiyorsanız kullanın <xref:System.Windows.Forms.NumericUpDown> denetim.</span><span class="sxs-lookup"><span data-stu-id="95660-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="95660-117">Daha fazla bilgi için bkz: [NumericUpDown denetimine genel bakış](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="95660-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95660-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95660-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="95660-119">DomainUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="95660-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
