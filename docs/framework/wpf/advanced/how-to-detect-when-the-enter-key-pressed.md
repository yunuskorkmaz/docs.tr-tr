---
title: 'Nasıl yapılır: Enter Tuşuna Basıldığında Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: e2337826077c836696937f91541d6d261f1270aa
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004817"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="4ded3-102">Nasıl yapılır: Enter Tuşuna Basıldığında Algılama</span><span class="sxs-lookup"><span data-stu-id="4ded3-102">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="4ded3-103">Bu örnek, <xref:System.Windows.Input.Key.Enter> tuşuna klavyede basıldığında nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4ded3-103">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="4ded3-104">Bu örnek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasından ve arka plan kod dosyasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="4ded3-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ded3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ded3-105">Example</span></span>  
 <span data-ttu-id="4ded3-106">Kullanıcı <xref:System.Windows.Controls.TextBox> ' deki <xref:System.Windows.Input.Key.Enter> anahtarına bastığında, metin kutusundaki giriş [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ' nin başka bir alanında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ded3-106">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="4ded3-107">Aşağıdaki XAML, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.TextBox> ' den oluşan Kullanıcı arabirimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ded3-107">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="4ded3-108">Aşağıdaki kod arkasında <xref:System.Windows.UIElement.KeyDown> olay işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4ded3-108">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="4ded3-109">Basılan anahtar <xref:System.Windows.Input.Key.Enter> anahtarlıysa, <xref:System.Windows.Controls.TextBlock> ' de bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ded3-109">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="4ded3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ded3-110">See also</span></span>

- [<span data-ttu-id="4ded3-111">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ded3-111">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="4ded3-112">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ded3-112">Routed Events Overview</span></span>](routed-events-overview.md)
