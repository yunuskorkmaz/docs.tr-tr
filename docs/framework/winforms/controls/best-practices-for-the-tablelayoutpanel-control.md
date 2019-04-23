---
title: TableLayoutPanel Denetimi için En İyi Yöntemler
ms.date: 03/30/2017
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
ms.openlocfilehash: 57abf3527af146f1ce918bcabbc6a5a34bfb9b34
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773837"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="9e328-102">TableLayoutPanel Denetimi için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e328-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="9e328-103"><xref:System.Windows.Forms.TableLayoutPanel> Denetim dikkatli bir şekilde Windows formlarınızı kullanmadan önce dikkate almanız gereken güçlü düzen özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e328-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="9e328-104">Öneriler</span><span class="sxs-lookup"><span data-stu-id="9e328-104">Recommendations</span></span>  
 <span data-ttu-id="9e328-105">Aşağıdaki öneriler kullanmanıza yardımcı olacak <xref:System.Windows.Forms.TableLayoutPanel> en iyi avantajı denetimi.</span><span class="sxs-lookup"><span data-stu-id="9e328-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="9e328-106">Hedeflenen kullanın</span><span class="sxs-lookup"><span data-stu-id="9e328-106">Targeted Use</span></span>  
 <span data-ttu-id="9e328-107">Kullanım <xref:System.Windows.Forms.TableLayoutPanel> olabildiğince az denetim.</span><span class="sxs-lookup"><span data-stu-id="9e328-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="9e328-108">Bunu yeniden boyutlandırılabilir düzeni gerektiren tüm durumlarda kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9e328-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="9e328-109">Aşağıdaki listede açıklanmıştır kullanımını en iyi yararlanan düzenleri <xref:System.Windows.Forms.TableLayoutPanel> denetimi:</span><span class="sxs-lookup"><span data-stu-id="9e328-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="9e328-110">Birbirleriyle orantılı olarak yeniden boyutlandırmak birden çok form parçası olan düzenler.</span><span class="sxs-lookup"><span data-stu-id="9e328-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="9e328-111">Değiştirildiğinde veya eklendiğinde veya çıkarıldığında kullanıcı tarafından özelleştirilebilir alanlara sahip veri girişi formları gibi çalışma zamanında dinamik olarak oluşturulan düzenleri tercihleri temelinde.</span><span class="sxs-lookup"><span data-stu-id="9e328-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="9e328-112">Genel bir sabit boyutta kalması gereken düzenler.</span><span class="sxs-lookup"><span data-stu-id="9e328-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="9e328-113">Örneğin, 800 x 600 ' küçük kalması gereken bir iletişim kutusu olabilir, ancak yerelleştirilmiş dizeleri desteklemeniz gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="9e328-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="9e328-114">Aşağıdaki liste önemli ölçüde kullanarak avantaj elde değil düzenleri açıklar <xref:System.Windows.Forms.TableLayoutPanel> denetimi:</span><span class="sxs-lookup"><span data-stu-id="9e328-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="9e328-115">Etiket ve metin girişi alanlarının tek bir sütun basit veri girişi formları ile tek bir sütun.</span><span class="sxs-lookup"><span data-stu-id="9e328-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="9e328-116">Bir yeniden boyutlandırma meydana geldiğinde, tüm kullanılabilir alanı dolduracak alan büyük tek bir form görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9e328-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="9e328-117">Bu, tek bir görüntüleyen bir form örneğidir <xref:System.Windows.Forms.PropertyGrid> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9e328-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="9e328-118">Formu yeniden boyutlandırıldığında başka bir şey genişletmeniz gerekir çünkü bu durumda, sabitleme, kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e328-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="9e328-119">Hangi denetimlerin olması gereken seçerken dikkatli bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9e328-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="9e328-120">Bağlama kullanarak 30 oranında büyümesine metni yer varsa kullanmayı <xref:System.Windows.Forms.Control.Anchor%2A> yalnızca özellik.</span><span class="sxs-lookup"><span data-stu-id="9e328-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="9e328-121">Düzeninizi tarafından gerekli alanı tahmin edebilirsiniz, kullanım <xref:System.Windows.Forms.Control.Dock%2A> ve <xref:System.Windows.Forms.Control.Anchor%2A> kalan alanı ayrıntılarını tahmin etmek daha kolaydır ve <xref:System.Windows.Forms.Control.AutoSize%2A> davranışı.</span><span class="sxs-lookup"><span data-stu-id="9e328-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="9e328-122">Genel olarak ile düzeninizi tasarlarken, <xref:System.Windows.Forms.TableLayoutPanel> denetlemek, tasarım, olabildiğince basit tutun.</span><span class="sxs-lookup"><span data-stu-id="9e328-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="9e328-123">Belge Anahattı penceresini kullanma</span><span class="sxs-lookup"><span data-stu-id="9e328-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="9e328-124">Belge Anahattı penceresi denetimlerinizi z düzenini ve üst-alt ilişkilerini yönetmek için kullanabileceğiniz düzeninizi ağaç görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e328-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="9e328-125">Gelen **Görünüm menüsü**seçin **diğer Windows**, ardından **belge anahattı**.</span><span class="sxs-lookup"><span data-stu-id="9e328-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="9e328-126">İç içe geçme kaçının</span><span class="sxs-lookup"><span data-stu-id="9e328-126">Avoid Nesting</span></span>  
 <span data-ttu-id="9e328-127">İç içe diğer önlemek <xref:System.Windows.Forms.TableLayoutPanel> içinde denetleyen bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="9e328-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="9e328-128">İç içe geçmiş düzenleri hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e328-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="9e328-129">Görsel devralmadan kaçının</span><span class="sxs-lookup"><span data-stu-id="9e328-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="9e328-130"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi Windows Form Tasarımcısı'nda görsel devralmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9e328-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="9e328-131">A <xref:System.Windows.Forms.TableLayoutPanel> "tasarım zamanında kilitli gibi" Denetim türetilmiş bir sınıf içinde görünür.</span><span class="sxs-lookup"><span data-stu-id="9e328-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e328-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e328-132">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
