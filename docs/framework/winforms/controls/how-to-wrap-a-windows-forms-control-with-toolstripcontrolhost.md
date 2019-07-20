---
title: 'Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma'
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
ms.openlocfilehash: 6335d09a89225ae1e202a781a73bfd149608f5fc
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364194"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="683ab-102">Nasıl yapılır: ToolStripControlHost ile Bir Windows Forms Denetimini Kaydırma</span><span class="sxs-lookup"><span data-stu-id="683ab-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<span data-ttu-id="683ab-103"><xref:System.Windows.Forms.ToolStripControlHost>, <xref:System.Windows.Forms.ToolStripControlHost> oluşturucuyu kullanarak veya kendisini genişleterek <xref:System.Windows.Forms.ToolStripControlHost> rastgele Windows Forms denetimlerinin barındırılmasına olanak tanımak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="683ab-103"><xref:System.Windows.Forms.ToolStripControlHost> is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="683ab-104">Denetimin sık kullanılan özelliklerini ve yöntemlerini sunan özellikleri ve <xref:System.Windows.Forms.ToolStripControlHost> yöntemleri genişleterek ve uygulayarak denetimi sarmayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="683ab-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="683ab-105">Ayrıca, denetimin <xref:System.Windows.Forms.ToolStripControlHost> olaylarını düzeyinde kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="683ab-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="683ab-106">Türeerek bir ToolStripControlHost 'ta denetim barındırmak için</span><span class="sxs-lookup"><span data-stu-id="683ab-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="683ab-107">Genişletin <xref:System.Windows.Forms.ToolStripControlHost>.</span><span class="sxs-lookup"><span data-stu-id="683ab-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="683ab-108">İstenen denetimde geçen temel sınıf oluşturucusunu çağıran parametresiz bir Oluşturucu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="683ab-108">Implement a parameterless constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="683ab-109">Sarmalanan denetimle aynı türde bir özellik bildirin ve özelliğin erişimcisinde doğru `Control` denetim türü olarak döndürün.</span><span class="sxs-lookup"><span data-stu-id="683ab-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="683ab-110">Sarmalanan denetimin diğer sık kullanılan özelliklerini ve yöntemlerini genişletilmiş sınıftaki özellikler ve yöntemlerle kullanıma sunun.</span><span class="sxs-lookup"><span data-stu-id="683ab-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="683ab-111">İsteğe bağlı olarak, <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>ve <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> yöntemlerini geçersiz kılın ve göstermek istediğiniz denetim olaylarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="683ab-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="683ab-112">Göstermek istediğiniz olaylar için gereken sarmayı sağlayın.</span><span class="sxs-lookup"><span data-stu-id="683ab-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="683ab-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="683ab-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="683ab-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="683ab-114">Compiling the Code</span></span>  
  
<span data-ttu-id="683ab-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="683ab-115">This example requires:</span></span>
  
- <span data-ttu-id="683ab-116">System ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="683ab-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683ab-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="683ab-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="683ab-118">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="683ab-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="683ab-119">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="683ab-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="683ab-120">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="683ab-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
