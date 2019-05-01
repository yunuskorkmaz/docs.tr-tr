---
title: 'Nasıl yapılır: Sabit Listesine Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021017"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="a6d2b-102">Nasıl yapılır: Sabit Listesine Bağlama</span><span class="sxs-lookup"><span data-stu-id="a6d2b-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="a6d2b-103">Bu örnek, bir numaralandırma sabit listesinin GetValues yöntemi bağlanarak bağlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6d2b-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6d2b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6d2b-104">Example</span></span>  
 <span data-ttu-id="a6d2b-105">Aşağıdaki örnekte, <xref:System.Windows.Controls.ListBox> listesini görüntüler <xref:System.Windows.HorizontalAlignment> sabit listesi değerleri veri bağlama aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="a6d2b-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="a6d2b-106"><xref:System.Windows.Controls.ListBox> Ve <xref:System.Windows.Controls.Button> değiştirebileceğiniz şekilde bağlı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği değerinin <xref:System.Windows.Controls.Button> bir değer seçerek <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a6d2b-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="a6d2b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d2b-107">See also</span></span>

- [<span data-ttu-id="a6d2b-108">Bir Yönteme Bağlama</span><span class="sxs-lookup"><span data-stu-id="a6d2b-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="a6d2b-109">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6d2b-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a6d2b-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a6d2b-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
