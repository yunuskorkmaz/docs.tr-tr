---
title: 'Nasıl yapılır: Enter Tuşuna Basıldığında Algılama'
description: Windows Presentation Foundation ' deki klavyede ENTER tuşunun ne zaman seçili olduğunu tespit edin. Bu örnek XAML ve arka plan kod dosyasından oluşur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163179"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="a0056-104">Nasıl yapılır: Enter Tuşuna Basıldığında Algılama</span><span class="sxs-lookup"><span data-stu-id="a0056-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="a0056-105">Bu örnek, tuşa klavyede basıldığında nasıl algılanacağını göstermektedir <xref:System.Windows.Input.Key.Enter> .</span><span class="sxs-lookup"><span data-stu-id="a0056-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="a0056-106">Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0056-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0056-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0056-107">Example</span></span>  
 <span data-ttu-id="a0056-108">Kullanıcı içindeki anahtara bastığında, <xref:System.Windows.Input.Key.Enter> <xref:System.Windows.Controls.TextBox> metin kutusundaki giriş ' ın başka bir alanında görüntülenir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a0056-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="a0056-109">Aşağıdaki XAML, bir, ve ' den oluşan Kullanıcı arabirimini oluşturur <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="a0056-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="a0056-110">Aşağıdaki kod arkasında <xref:System.Windows.UIElement.KeyDown> olay işleyicisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a0056-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="a0056-111">Basılan anahtar <xref:System.Windows.Input.Key.Enter> anahtar ise, içinde bir ileti görüntülenir <xref:System.Windows.Controls.TextBlock> .</span><span class="sxs-lookup"><span data-stu-id="a0056-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="a0056-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0056-112">See also</span></span>

- [<span data-ttu-id="a0056-113">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a0056-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="a0056-114">Gönderilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a0056-114">Routed Events Overview</span></span>](routed-events-overview.md)
