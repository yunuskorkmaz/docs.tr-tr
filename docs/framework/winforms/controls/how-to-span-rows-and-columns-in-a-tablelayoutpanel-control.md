---
title: "Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0380e63925dcbd27a7ee6262ddbfb2706455c2a9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="8bdd2-102">Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Yayma</span><span class="sxs-lookup"><span data-stu-id="8bdd2-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="8bdd2-103">Denetimlerini bir <xref:System.Windows.Forms.TableLayoutPanel> denetim bitişik satırları ve sütunları yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bdd2-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8bdd2-105">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8bdd2-106">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8bdd2-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="8bdd2-107">Satırları ve sütunları kapsanacak</span><span class="sxs-lookup"><span data-stu-id="8bdd2-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="8bdd2-108">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="8bdd2-109">Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** sol üst hücresine <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="8bdd2-110">Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğine **2**.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="8bdd2-111">Unutmayın <xref:System.Windows.Forms.Button> denetimi birinci ve ikinci sütunları kapsar.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="8bdd2-112">Ayarlama <xref:System.Windows.Forms.Button> denetimin **RowSpan** özelliğine **2**.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="8bdd2-113">Unutmayın <xref:System.Windows.Forms.Button> denetim yayılan birinci ve ikinci satır.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="8bdd2-114">Ayarlama <xref:System.Windows.Forms.Button> denetimin **ColumnSpan** özelliğine **1**.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="8bdd2-115">Unutmayın <xref:System.Windows.Forms.Button> denetimi ilk sütuna taşır ve birinci ve ikinci satır yayılır.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdd2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bdd2-116">See Also</span></span>  
 [<span data-ttu-id="8bdd2-117">TableLayoutPanel denetimi</span><span class="sxs-lookup"><span data-stu-id="8bdd2-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
