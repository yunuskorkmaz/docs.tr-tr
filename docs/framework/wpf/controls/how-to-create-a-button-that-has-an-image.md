---
title: 'Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: cfebe53047531ecddde42a3a0596dfd949629ecd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682082"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="6d814-102">Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d814-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="6d814-103">Bu örnek nasıl görüntü ekleneceğini gösterir. bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6d814-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d814-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d814-104">Example</span></span>  
 <span data-ttu-id="6d814-105">Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="6d814-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="6d814-106">Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir.</span><span class="sxs-lookup"><span data-stu-id="6d814-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="6d814-107">Örneğin proje klasörünün alt klasörüdür verileri, adlı bir klasöre görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="6d814-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="6d814-108">Kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d814-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="6d814-109">Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="6d814-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6d814-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d814-110">See also</span></span>
- [<span data-ttu-id="6d814-111">Denetimler</span><span class="sxs-lookup"><span data-stu-id="6d814-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="6d814-112">Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6d814-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
