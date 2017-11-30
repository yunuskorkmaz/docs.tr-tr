---
title: "TableLayoutPanel Denetimi için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802cc501b695f6c5cfe990bf72a4d9d2af68ba2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="c75de-102">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c75de-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="c75de-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim dikkatle Windows formlarında kullanmadan önce dikkate almanız gereken güçlü yerleşim özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75de-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="c75de-104">Önerileri</span><span class="sxs-lookup"><span data-stu-id="c75de-104">Recommendations</span></span>  
 <span data-ttu-id="c75de-105">Aşağıdaki öneriler kullanmanıza yardımcı <xref:System.Windows.Forms.TableLayoutPanel> en iyi kendi yararınıza denetim.</span><span class="sxs-lookup"><span data-stu-id="c75de-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="c75de-106">Hedeflenen kullanın</span><span class="sxs-lookup"><span data-stu-id="c75de-106">Targeted Use</span></span>  
 <span data-ttu-id="c75de-107">Kullanım <xref:System.Windows.Forms.TableLayoutPanel> tutumlu denetim.</span><span class="sxs-lookup"><span data-stu-id="c75de-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="c75de-108">Onu yeniden boyutlandırılabilir düzeni gerektiren tüm durumlarda kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c75de-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="c75de-109">Aşağıdaki listede kullanımı en fazla yararlanır düzenleri açıklanmaktadır <xref:System.Windows.Forms.TableLayoutPanel> denetimi:</span><span class="sxs-lookup"><span data-stu-id="c75de-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="c75de-110">Formun orantılı olarak birbirlerine yeniden boyutlandırmak birden çok bölümleri olan düzenler.</span><span class="sxs-lookup"><span data-stu-id="c75de-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="c75de-111">Değiştirilen veya eklenir veya çıkarılır kullanıcı özelleştirilebilir alanlar veri girişi formları gibi çalışma zamanında dinamik olarak üretilen düzenleri tercihlerinize göre temel.</span><span class="sxs-lookup"><span data-stu-id="c75de-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="c75de-112">Genel sabit boyutta kalacağı düzenler.</span><span class="sxs-lookup"><span data-stu-id="c75de-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="c75de-113">Örneğin, 800 x 600'den küçük kalması gereken bir iletişim kutusu olabilir, ancak yerelleştirilmiş dizeleri desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c75de-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="c75de-114">Aşağıdaki listede kullanımından büyük ölçüde faydalanmaz düzenleri açıklanmaktadır <xref:System.Windows.Forms.TableLayoutPanel> denetimi:</span><span class="sxs-lookup"><span data-stu-id="c75de-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="c75de-115">Basit veri girişi formlarla tek bir sütun etiketleri ve metin girişi alanlarının tek bir sütun.</span><span class="sxs-lookup"><span data-stu-id="c75de-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="c75de-116">Tek bir büyük formlarla bir yeniden boyutlandırma meydana geldiğinde, tüm kullanılabilir alanı dolduracak alanı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c75de-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="c75de-117">Bu, tek bir görüntüleyen bir form örneğidir <xref:System.Windows.Forms.PropertyGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="c75de-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="c75de-118">Bu durumda, formu yeniden boyutlandırıldığında hiçbir şey genişletmeniz gerekir çünkü sabitleme, kullanın.</span><span class="sxs-lookup"><span data-stu-id="c75de-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="c75de-119">Hangi denetimlerin olması gereken seçerken dikkatli bir <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="c75de-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="c75de-120">%30 sabitleme kullanarak tarafından büyümeye metninizi yer varsa, kullanmayı <xref:System.Windows.Forms.Control.Anchor%2A> yalnızca özelliği.</span><span class="sxs-lookup"><span data-stu-id="c75de-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="c75de-121">Düzeninizi tarafından gerekli alanı tahmin edebilirsiniz, kullanımı <xref:System.Windows.Forms.Control.Dock%2A> ve <xref:System.Windows.Forms.Control.Anchor%2A> kalan alanın ayrıntılarını tahmin daha kolaydır ve <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı.</span><span class="sxs-lookup"><span data-stu-id="c75de-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="c75de-122">Genel olarak, düzeniyle tasarlarken, <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, tasarım olabildiğince basit tutun.</span><span class="sxs-lookup"><span data-stu-id="c75de-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="c75de-123">Belge Anahattı penceresi kullanın</span><span class="sxs-lookup"><span data-stu-id="c75de-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="c75de-124">Belge Anahattı penceresi denetimlerinizi z düzeni ve üst-alt ilişkilerini yönetmek için kullanabileceğiniz düzeninizi ağaç görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="c75de-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="c75de-125">Gelen **Görünüm menüsünde**seçin **diğer pencereler**seçeneğini belirleyip **belge anahattı**.</span><span class="sxs-lookup"><span data-stu-id="c75de-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="c75de-126">İç içe geçme kaçının</span><span class="sxs-lookup"><span data-stu-id="c75de-126">Avoid Nesting</span></span>  
 <span data-ttu-id="c75de-127">İç içe geçme diğer kaçının <xref:System.Windows.Forms.TableLayoutPanel> içinde denetleyen bir <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="c75de-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="c75de-128">İç içe geçmiş düzenleri hata ayıklama zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c75de-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="c75de-129">Görsel devralma kaçının</span><span class="sxs-lookup"><span data-stu-id="c75de-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="c75de-130"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi Windows Forms Tasarımcısı'nda görsel devralma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c75de-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="c75de-131">A <xref:System.Windows.Forms.TableLayoutPanel> türetilmiş bir sınıf denetiminde "tasarım zamanında kilitli"olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c75de-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75de-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c75de-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
