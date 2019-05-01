---
title: 'Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: ef05b72b33d3f28d1811389dfae65554a1567d43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967134"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="15ee0-102">Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma</span><span class="sxs-lookup"><span data-stu-id="15ee0-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="15ee0-103">İki kez arabelleğe almayı bellek arabelleği birden çok Boya işlemleriyle ilişkili titreşimini sorunları ele almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="15ee0-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="15ee0-104">İki kez arabelleğe alma etkinleştirildiğinde, tüm Boya işlemleri ilk ekranda çizim yüzeyi yerine bir arabelleğe işlenir.</span><span class="sxs-lookup"><span data-stu-id="15ee0-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="15ee0-105">Tüm Boya işlemleri tamamlandıktan sonra doğrudan ilişkili çizim yüzeyi ara belleğe kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="15ee0-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="15ee0-106">Yalnızca bir grafik işlem ekranda gerçekleştirildiğinden, karmaşık boyama işlemleriyle ilişkili görüntü titremeyi ortadan kalkar. Çoğu uygulama için varsayılan iki kez arabelleğe alma sağladığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] en iyi sonuçlar şunları sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="15ee0-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="15ee0-107">Standart Windows Forms denetimleri, varsayılan olarak arabelleğe çift.</span><span class="sxs-lookup"><span data-stu-id="15ee0-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="15ee0-108">Varsayılan arabelleğe almayı formlarınızı sıfırladığınızdan çift etkinleştirebilirsiniz ve iki yolla denetimleri yazıldı.</span><span class="sxs-lookup"><span data-stu-id="15ee0-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="15ee0-109">Kümelerden yapabilirsiniz <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğini `true`, veya çağırabilirsiniz <xref:System.Windows.Forms.Control.SetStyle%2A> ayarlanacak yöntemi <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> bayrak `true`.</span><span class="sxs-lookup"><span data-stu-id="15ee0-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="15ee0-110">Her iki yöntem de, varsayılan çift form veya denetim için arabelleğe almayı etkinleştir ve titreşimsiz grafik işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="15ee0-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="15ee0-111">Çağırma <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi için yazdığınız tüm işleme kodu yalnızca fazla özel denetimler için önerilir.</span><span class="sxs-lookup"><span data-stu-id="15ee0-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="15ee0-112">Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryoları için kendi çift arabelleğe alma mantığını uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="15ee0-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="15ee0-113">Daha fazla bilgi için [nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="15ee0-113">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="15ee0-114">Titreşimi azaltmak için</span><span class="sxs-lookup"><span data-stu-id="15ee0-114">To reduce flicker</span></span>  
  
- <span data-ttu-id="15ee0-115">Ayarlama <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="15ee0-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="15ee0-116">\- veya -</span><span class="sxs-lookup"><span data-stu-id="15ee0-116">\- or -</span></span>  
  
- <span data-ttu-id="15ee0-117">Çağrı <xref:System.Windows.Forms.Control.SetStyle%2A> ayarlanacak yöntemi <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> bayrak `true`.</span><span class="sxs-lookup"><span data-stu-id="15ee0-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="15ee0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ee0-118">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="15ee0-119">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="15ee0-119">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="15ee0-120">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="15ee0-120">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
