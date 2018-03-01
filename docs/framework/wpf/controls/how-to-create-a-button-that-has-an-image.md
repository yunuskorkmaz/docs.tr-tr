---
title: "Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e95f027a8e3568365fa7957c36241b6ec2c30d28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="0a460-102">Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a460-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="0a460-103">Bu örnek, bir resim eklemek gösterilmiştir bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="0a460-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a460-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a460-104">Example</span></span>  
 <span data-ttu-id="0a460-105">Aşağıdaki örnekte iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0a460-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="0a460-106">Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir.</span><span class="sxs-lookup"><span data-stu-id="0a460-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="0a460-107">Örneğin proje klasörün bir alt veri adlı bir klasöre görüntüdür.</span><span class="sxs-lookup"><span data-stu-id="0a460-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="0a460-108">Bir kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0a460-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="0a460-109">Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="0a460-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0a460-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a460-110">See Also</span></span>  
 [<span data-ttu-id="0a460-111">Denetimler</span><span class="sxs-lookup"><span data-stu-id="0a460-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="0a460-112">Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="0a460-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
