---
title: "Nasıl yapılır: Çizgileri Birleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d12cc7b4b4c878ec812190fd56a1face64118ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-join-lines"></a><span data-ttu-id="12d03-102">Nasıl yapılır: Çizgileri Birleştirme</span><span class="sxs-lookup"><span data-stu-id="12d03-102">How to: Join Lines</span></span>
<span data-ttu-id="12d03-103">Satır birleştirme, uçları karşıladığında veya üst üste iki çizgiyle biçimlendirilmiş ortak alandır.</span><span class="sxs-lookup"><span data-stu-id="12d03-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="12d03-104">üç çizgi birleştirme stili sağlar: gönye, eğim ve yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="12d03-104"> provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="12d03-105">Çizgisi birleştirme stili bir özelliğidir <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12d03-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="12d03-106">Çizgisi birleştirme stili için belirttiğinizde bir <xref:System.Drawing.Pen> nesnesi, birleştirme stili herhangi bir bağlı olan tüm satırları uygulanacak <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bu kalem kullanarak çizilir.</span><span class="sxs-lookup"><span data-stu-id="12d03-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="12d03-107">Aşağıdaki çizimde eğik çizgi birleştirme örneğin sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12d03-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="12d03-108">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="12d03-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="12d03-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="12d03-109">Example</span></span>  
 <span data-ttu-id="12d03-110">Kullanarak çizgisi birleştirme stili belirtebilirsiniz <xref:System.Drawing.Pen.LineJoin%2A> özelliği <xref:System.Drawing.Pen> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12d03-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="12d03-111">Örnek bir eğik çizgi birleştirme yatay çizgi dikey çizgi arasındaki gösterir.</span><span class="sxs-lookup"><span data-stu-id="12d03-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="12d03-112">Aşağıdaki kodda, değer <xref:System.Drawing.Drawing2D.LineJoin.Bevel> atanan <xref:System.Drawing.Pen.LineJoin%2A> özelliği üyesi olduğu <xref:System.Drawing.Drawing2D.LineJoin> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="12d03-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="12d03-113">Diğer üyeleriyle <xref:System.Drawing.Drawing2D.LineJoin> numaralandırması olan <xref:System.Drawing.Drawing2D.LineJoin.Miter> ve <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span><span class="sxs-lookup"><span data-stu-id="12d03-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12d03-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="12d03-114">Compiling the Code</span></span>  
 <span data-ttu-id="12d03-115">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="12d03-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d03-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12d03-116">See Also</span></span>  
 [<span data-ttu-id="12d03-117">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="12d03-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
