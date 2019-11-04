---
title: 'Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424813"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="cc52e-102">Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cc52e-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="cc52e-103"><xref:System.Drawing.Image> sınıfından devralan <xref:System.Drawing.Imaging.Metafile> sınıfı, vektör görüntülerini kaydetme, görüntüleme ve İnceleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc52e-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc52e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc52e-104">Example</span></span>  
 <span data-ttu-id="cc52e-105">Ekranda bir vektör görüntüsünü (meta dosyası) göstermek için bir <xref:System.Drawing.Imaging.Metafile> nesnesi ve bir <xref:System.Drawing.Graphics> nesnesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc52e-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc52e-106">Bir dosyanın (veya akışın) adını <xref:System.Drawing.Imaging.Metafile> oluşturucusuna geçirin.</span><span class="sxs-lookup"><span data-stu-id="cc52e-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="cc52e-107">Bir <xref:System.Drawing.Imaging.Metafile> nesnesi oluşturduktan sonra, bu <xref:System.Drawing.Imaging.Metafile> nesnesini <xref:System.Drawing.Graphics> nesnesinin <xref:System.Drawing.Graphics.DrawImage%2A> metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="cc52e-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="cc52e-108">Örnek, bir EMF (Gelişmiş Meta dosyası) dosyasından bir <xref:System.Drawing.Imaging.Metafile> nesnesi oluşturur ve sonra görüntüyü sol üst köşesine (60, 10) çizer.</span><span class="sxs-lookup"><span data-stu-id="cc52e-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="cc52e-109">Aşağıdaki çizimde belirtilen konumda çizilen meta dosya gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc52e-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="cc52e-110">![Görüntü konumunu gösteren ekran görüntüsü.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="cc52e-110">![Screenshot showing image position.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc52e-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cc52e-111">Compiling the Code</span></span>  
 <span data-ttu-id="cc52e-112">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan <xref:System.Windows.Forms.PaintEventArgs> `e`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cc52e-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc52e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc52e-113">See also</span></span>

- [<span data-ttu-id="cc52e-114">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="cc52e-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
