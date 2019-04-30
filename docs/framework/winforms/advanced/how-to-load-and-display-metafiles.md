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
ms.openlocfilehash: 39b7251b2789c7410e1d59b4aa7990a2f73055fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723228"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="0796f-102">Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0796f-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="0796f-103"><xref:System.Drawing.Imaging.Metafile> Öğesinden devralan sınıf <xref:System.Drawing.Image> sınıfı, kaydı, görüntüleme ve vektör görüntüleri sınamak için yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0796f-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0796f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0796f-104">Example</span></span>  
 <span data-ttu-id="0796f-105">Ekranda bir vektör görüntüsü (meta dosyası) için ihtiyacınız bir <xref:System.Drawing.Imaging.Metafile> nesnesi ve bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="0796f-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0796f-106">Bir dosya (veya bir akışa) adını geçirin bir <xref:System.Drawing.Imaging.Metafile> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="0796f-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="0796f-107">Oluşturduktan sonra bir <xref:System.Drawing.Imaging.Metafile> nesne, bu geçirmek <xref:System.Drawing.Imaging.Metafile> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="0796f-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="0796f-108">Örnek bir <xref:System.Drawing.Imaging.Metafile> EMF (Gelişmiş Meta dosyası) dosyasından nesnesi ve ardından, sol üst köşede görüntüsüyle çizer (60, 10).</span><span class="sxs-lookup"><span data-stu-id="0796f-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="0796f-109">Belirtilen konumda çizilmiş meta dosyası aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0796f-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="0796f-110">![Görüntü konumu](./media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="0796f-110">![Image Position](./media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0796f-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0796f-111">Compiling the Code</span></span>  
 <span data-ttu-id="0796f-112">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="0796f-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0796f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0796f-113">See also</span></span>

- [<span data-ttu-id="0796f-114">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="0796f-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
