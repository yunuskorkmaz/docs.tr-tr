---
title: 'Nasıl yapılır: Algılama Enter tuşuna basıldığında'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: 1796127d33087a3fd4504d03f175f8afe5323630
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351872"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="e5b40-102">Nasıl yapılır: Algılama Enter tuşuna basıldığında</span><span class="sxs-lookup"><span data-stu-id="e5b40-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="e5b40-103">Bu örnek nasıl algılanacağını gösterir <xref:System.Windows.Input.Key.Enter> klavyede tuşuna basıldığında.</span><span class="sxs-lookup"><span data-stu-id="e5b40-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="e5b40-104">Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="e5b40-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b40-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5b40-105">Example</span></span>  
 <span data-ttu-id="e5b40-106">Kullanıcının bastığında <xref:System.Windows.Input.Key.Enter> anahtarını <xref:System.Windows.Controls.TextBox>, başka bir bölümünde giriş metin kutusunda görüntülenen [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5b40-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="e5b40-107">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşur kullanıcı arabirimi oluşturan bir <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock>ve <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="e5b40-107">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="e5b40-108">Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.KeyDown> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e5b40-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="e5b40-109">Basıldığında anahtar bulunuyorsa <xref:System.Windows.Input.Key.Enter> anahtar, bir ileti görüntülenir <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="e5b40-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="e5b40-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b40-110">See also</span></span>
- [<span data-ttu-id="e5b40-111">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5b40-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="e5b40-112">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5b40-112">Routed Events Overview</span></span>](routed-events-overview.md)
