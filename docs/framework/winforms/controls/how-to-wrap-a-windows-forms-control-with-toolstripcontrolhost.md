---
title: Denetimi ToolStripControlHost ile sarın
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: c7dbe042623006ed9501016669d6451ba0667cbc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728184"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="efc8b-102">Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma</span><span class="sxs-lookup"><span data-stu-id="efc8b-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="efc8b-103"><xref:System.Windows.Forms.ToolStripControlHost>, <xref:System.Windows.Forms.ToolStripControlHost> Oluşturucusu kullanılarak veya <xref:System.Windows.Forms.ToolStripControlHost> kendisini genişleterek rastgele Windows Forms denetimlerinin barındırılmasına olanak tanımak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="efc8b-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="efc8b-104"><xref:System.Windows.Forms.ToolStripControlHost> genişleterek ve denetimin sık kullanılan özelliklerini ve yöntemlerini ortaya çıkaran özellikleri ve yöntemleri uygulayarak denetimi sarmayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="efc8b-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="efc8b-105">Ayrıca, denetimin olaylarını <xref:System.Windows.Forms.ToolStripControlHost> düzeyinde kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efc8b-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="efc8b-106">Türeerek bir ToolStripControlHost 'ta denetim barındırmak için</span><span class="sxs-lookup"><span data-stu-id="efc8b-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="efc8b-107"><xref:System.Windows.Forms.ToolStripControlHost>genişletin.</span><span class="sxs-lookup"><span data-stu-id="efc8b-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="efc8b-108">İstenen denetimde geçen temel sınıf oluşturucusunu çağıran parametresiz bir Oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="efc8b-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="efc8b-109">Sarmalanan denetimle aynı türde bir özellik bildirin ve özelliğin erişimcisinde doğru denetim türü olarak `Control` döndürün.</span><span class="sxs-lookup"><span data-stu-id="efc8b-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="efc8b-110">Sarmalanan denetimin diğer sık kullanılan özelliklerini ve yöntemlerini genişletilmiş sınıftaki özellikler ve yöntemlerle kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="efc8b-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="efc8b-111">İsteğe bağlı olarak, <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>ve <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> yöntemlerini geçersiz kılın ve göstermek istediğiniz denetim olaylarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="efc8b-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="efc8b-112">Göstermek istediğiniz olaylar için gereken sarmayı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="efc8b-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="efc8b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="efc8b-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="efc8b-114">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="efc8b-114">Compiling the Code</span></span>  
  
<span data-ttu-id="efc8b-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="efc8b-115">This example requires:</span></span>
  
- <span data-ttu-id="efc8b-116">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="efc8b-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc8b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efc8b-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="efc8b-118">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="efc8b-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="efc8b-119">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="efc8b-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="efc8b-120">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="efc8b-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
