---
title: 'Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 5be928ac75ad727feabcde07ac0c6dc76ed130e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910955"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="d3b2e-102">Nasıl yapılır: Görüntüsü Bulunan bir Düğme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3b2e-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="d3b2e-103">Bu örnek nasıl görüntü ekleneceğini gösterir. bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3b2e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3b2e-104">Example</span></span>  
 <span data-ttu-id="d3b2e-105">Aşağıdaki örnek iki oluşturur <xref:System.Windows.Controls.Button> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="d3b2e-106">Bir <xref:System.Windows.Controls.Button> metni içeren ve diğeri bir görüntü içerir.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="d3b2e-107">Örneğin proje klasörünün alt klasörüdür verileri, adlı bir klasöre görüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="d3b2e-108">Kullanıcı tıkladığında <xref:System.Windows.Controls.Button> görüntü, arka plan ve diğer metin olan <xref:System.Windows.Controls.Button> değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="d3b2e-109">Bu örnekte <xref:System.Windows.Controls.Button> denetleyen biçimlendirme kullanarak ancak kod yazmak için kullandığı <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d3b2e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b2e-110">See also</span></span>

- [<span data-ttu-id="d3b2e-111">Denetimler</span><span class="sxs-lookup"><span data-stu-id="d3b2e-111">Controls</span></span>](index.md)
- [<span data-ttu-id="d3b2e-112">Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="d3b2e-112">Control Library</span></span>](control-library.md)
