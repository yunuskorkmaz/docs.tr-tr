---
title: 'Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma'
description: Windows Forms için çift arabelleğe alma ile grafik titreşimini azaltmayı öğrenin ve boyama işlemleriyle ilişkili titreşim sorunlarını gidermek için denetimleri kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618135"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="c0714-103">Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma</span><span class="sxs-lookup"><span data-stu-id="c0714-103">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="c0714-104">Çift arabelleğe alma, birden çok boyama işlemiyle ilişkili titreşim sorunlarını gidermek için bir bellek arabelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0714-104">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="c0714-105">Çift arabelleğe alma etkinleştirildiğinde, tüm boyama işlemleri, ekranda çizim yüzeyi yerine öncelikle bir bellek arabelleğine işlenir.</span><span class="sxs-lookup"><span data-stu-id="c0714-105">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="c0714-106">Tüm boyama işlemleri tamamlandıktan sonra, bellek arabelleği doğrudan onunla ilişkili çizim yüzeyine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c0714-106">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="c0714-107">Ekranda yalnızca bir grafik işlemi gerçekleştirildiğinden, karmaşık boyama işlemleriyle ilişkili görüntü titreşmesini ortadan kaldırmıştır. Çoğu uygulama için, .NET Framework tarafından belirtilen varsayılan çift arabelleğe alma en iyi sonuçları sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c0714-107">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the .NET Framework will provide the best results.</span></span> <span data-ttu-id="c0714-108">Standart Windows Forms denetimleri varsayılan olarak iki kez arabelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="c0714-108">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="c0714-109">Formlarınızın ve yazılan denetimlerde varsayılan çift arabelleğe almayı iki şekilde etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0714-109">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="c0714-110"><xref:System.Windows.Forms.Control.DoubleBuffered%2A>Özelliğini olarak ayarlayabilir `true` ya da <xref:System.Windows.Forms.Control.SetStyle%2A> bayrağını olarak ayarlamak için yöntemini çağırabilirsiniz <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> `true` .</span><span class="sxs-lookup"><span data-stu-id="c0714-110">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="c0714-111">Her iki yöntem de, formunuz veya denetiminiz için varsayılan çift arabelleğe almayı etkinleştirir ve titreşimsiz grafik işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0714-111">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="c0714-112">Yöntemi çağırmak <xref:System.Windows.Forms.Control.SetStyle%2A> yalnızca tüm işleme kodunu yazdığınız özel denetimler için önerilir.</span><span class="sxs-lookup"><span data-stu-id="c0714-112">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="c0714-113">Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryolarında kendi çift arabelleğe alma mantığınızı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0714-113">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="c0714-114">Daha fazla bilgi için bkz. [nasıl yapılır: arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="c0714-114">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="c0714-115">Titreşimi azaltmak için</span><span class="sxs-lookup"><span data-stu-id="c0714-115">To reduce flicker</span></span>  
  
- <span data-ttu-id="c0714-116"><xref:System.Windows.Forms.Control.DoubleBuffered%2A>Özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="c0714-116">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="c0714-117">\-veya</span><span class="sxs-lookup"><span data-stu-id="c0714-117">\- or -</span></span>  
  
- <span data-ttu-id="c0714-118"><xref:System.Windows.Forms.Control.SetStyle%2A>Bayrağını ayarlamak için yöntemini çağırın <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> `true` .</span><span class="sxs-lookup"><span data-stu-id="c0714-118">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="c0714-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0714-119">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="c0714-120">İki Kez Arabelleğe Alınan Grafikler</span><span class="sxs-lookup"><span data-stu-id="c0714-120">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="c0714-121">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="c0714-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
