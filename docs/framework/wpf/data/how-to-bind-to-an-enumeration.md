---
title: 'Nasıl yapılır: Numaralandırmaya Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: df26d2bd08e4691837f739a4e71d3bb1a25bdd00
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377800"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="93b8f-102">Nasıl yapılır: Numaralandırmaya Bağlama</span><span class="sxs-lookup"><span data-stu-id="93b8f-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="93b8f-103">Bu örnek, bir numaralandırma sabit listesinin GetValues yöntemi bağlanarak bağlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93b8f-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93b8f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="93b8f-104">Example</span></span>  
 <span data-ttu-id="93b8f-105">Aşağıdaki örnekte, <xref:System.Windows.Controls.ListBox> listesini görüntüler <xref:System.Windows.HorizontalAlignment> sabit listesi değerleri veri bağlama aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="93b8f-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="93b8f-106"><xref:System.Windows.Controls.ListBox> Ve <xref:System.Windows.Controls.Button> değiştirebileceğiniz şekilde bağlı <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği değerinin <xref:System.Windows.Controls.Button> bir değer seçerek <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="93b8f-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="93b8f-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93b8f-107">See also</span></span>
- [<span data-ttu-id="93b8f-108">Bir Yönteme Bağlama</span><span class="sxs-lookup"><span data-stu-id="93b8f-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="93b8f-109">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="93b8f-109">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="93b8f-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="93b8f-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
