---
title: 'Nasıl yapılır: Numaralandırmaya Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454444"
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="ab3f8-102">Nasıl yapılır: Numaralandırmaya Bağlama</span><span class="sxs-lookup"><span data-stu-id="ab3f8-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="ab3f8-103">Bu örnek, numaralandırmanın GetValues yöntemine bağlama yoluyla bir numaralandırmaya nasıl bağlanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab3f8-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab3f8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab3f8-104">Example</span></span>  
 <span data-ttu-id="ab3f8-105">Aşağıdaki örnekte <xref:System.Windows.Controls.ListBox>, veri bağlama aracılığıyla <xref:System.Windows.HorizontalAlignment> numaralandırma değerlerinin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ab3f8-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="ab3f8-106"><xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.ListBox>bir değer seçerek <xref:System.Windows.Controls.Button> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özellik değerini değiştirebilmeniz için bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ab3f8-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="ab3f8-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab3f8-107">See also</span></span>

- [<span data-ttu-id="ab3f8-108">Bir Yönteme Bağlama</span><span class="sxs-lookup"><span data-stu-id="ab3f8-108">Bind to a Method</span></span>](how-to-bind-to-a-method.md)
- [<span data-ttu-id="ab3f8-109">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab3f8-109">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ab3f8-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ab3f8-110">How-to Topics</span></span>](data-binding-how-to-topics.md)
