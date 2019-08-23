---
title: DomainUpDown Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965308"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="f9888-102">DomainUpDown Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f9888-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="f9888-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimi aslında bir metin kutusu ve bir liste üzerinde yukarı veya aşağı taşımak için bir çift düğme birleşimidir.</span><span class="sxs-lookup"><span data-stu-id="f9888-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="f9888-104">Denetim, bir seçenek listesinden bir metin dizesi görüntüler ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f9888-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="f9888-105">Kullanıcı, yukarı ve aşağı ok tuşlarına basarak veya listedeki bir öğeyle eşleşen bir dize yazarak bir listede gezinmek için yukarı ve aşağı düğmelere tıklayarak dizeyi seçebilir.</span><span class="sxs-lookup"><span data-stu-id="f9888-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="f9888-106">Bu denetim için olası bir kullanım, alfabetik olarak sıralanan bir ad listesinden öğe seçmek içindir.</span><span class="sxs-lookup"><span data-stu-id="f9888-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9888-107">Listeyi sıralamak için <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f9888-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="f9888-108">Bu denetimin işlevi, liste kutusu veya Birleşik giriş kutusuna çok benzer, ancak çok az alan kaplar.</span><span class="sxs-lookup"><span data-stu-id="f9888-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="f9888-109">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="f9888-109">Key Properties</span></span>  
 <span data-ttu-id="f9888-110">Denetimin anahtar özellikleri, <xref:System.Windows.Forms.DomainUpDown.Items%2A> <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>ve <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>' dir.</span><span class="sxs-lookup"><span data-stu-id="f9888-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="f9888-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Özelliği, metin değerleri denetimde görüntülenen nesnelerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f9888-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="f9888-112"><xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> , Olarak`false`ayarlanırsa, denetim otomatik olarak kullanıcının oluşturduğu metni tamamlar ve listedeki bir değerle eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="f9888-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="f9888-113"><xref:System.Windows.Forms.DomainUpDown.Wrap%2A> Olarak`true`ayarlanırsa, son öğeyi geçen öğe, sizi listedeki ilk öğeye götürür ve tam tersi olur.</span><span class="sxs-lookup"><span data-stu-id="f9888-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="f9888-114">Denetimin anahtar yöntemleri ve ' <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>dir.</span><span class="sxs-lookup"><span data-stu-id="f9888-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="f9888-115">Bu denetim yalnızca metin dizelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f9888-115">This control displays only text strings.</span></span> <span data-ttu-id="f9888-116">Sayısal değerleri görüntüleyen bir denetim istiyorsanız, <xref:System.Windows.Forms.NumericUpDown> denetimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9888-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="f9888-117">Daha fazla bilgi için bkz. [NumericUpDown denetimine genel bakış](numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f9888-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9888-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9888-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="f9888-119">DomainUpDown Denetimi</span><span class="sxs-lookup"><span data-stu-id="f9888-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
