---
title: "Nasıl yapılır: StackPanel Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ba089c671fe54afe1c97da0a7bd786949cb5c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="7266b-102">Nasıl yapılır: StackPanel Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7266b-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="7266b-103">Bu örnek nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="7266b-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7266b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7266b-104">Example</span></span>  
 <span data-ttu-id="7266b-105">A <xref:System.Windows.Controls.StackPanel> , belirtilen yönde öğeleri yığın olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7266b-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="7266b-106">Üzerinde tanımlanan özellikleri kullanarak <xref:System.Windows.Controls.StackPanel>, içerik akış her ikisi de dikey olarak, varsayılan ayar olan ya da yatay olarak.</span><span class="sxs-lookup"><span data-stu-id="7266b-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="7266b-107">Aşağıdaki örnek dikey olarak beş yığınlar <xref:System.Windows.Controls.TextBlock> denetimleri, her biri farklı bir <xref:System.Windows.Controls.Border> ve <xref:System.Windows.Controls.Border.Background%2A>, kullanarak <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="7266b-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="7266b-108">Belirtilen en alt öğeleri <xref:System.Windows.FrameworkElement.Width%2A> ana pencereyi doldurmak için yayılır; ancak, alt öğeleri olan bir belirtilen <xref:System.Windows.FrameworkElement.Width%2A>, pencere içinde ortalanır.</span><span class="sxs-lookup"><span data-stu-id="7266b-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="7266b-109">Varsayılan yığın yönü bir <xref:System.Windows.Controls.StackPanel> dikeydir.</span><span class="sxs-lookup"><span data-stu-id="7266b-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="7266b-110">İçindeki içerik akışını denetlemek için bir <xref:System.Windows.Controls.StackPanel>, kullanın <xref:System.Windows.Controls.StackPanel.Orientation%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7266b-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="7266b-111">Yatay hizalama kullanarak denetleyebilirsiniz <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7266b-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7266b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7266b-112">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="7266b-113">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7266b-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="7266b-114">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7266b-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
