---
title: TableLayoutPanel Denetiminde AutoSize Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 466edeee5f45ec72ef265ef4855049c7852641b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164976"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="08f06-102">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="08f06-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="08f06-103">Farklı AutoSize davranışları</span><span class="sxs-lookup"><span data-stu-id="08f06-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="08f06-104"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi, aşağıdaki yollarla otomatik boyutlandırma davranışını destekler:</span><span class="sxs-lookup"><span data-stu-id="08f06-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="08f06-105">Aracılığıyla <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği;</span><span class="sxs-lookup"><span data-stu-id="08f06-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="08f06-106">Aracılığıyla <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.</span><span class="sxs-lookup"><span data-stu-id="08f06-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="08f06-107">AutoSize özelliği ile satır ve sütun stilleri</span><span class="sxs-lookup"><span data-stu-id="08f06-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="08f06-108">Aşağıdaki tabloda arasındaki etkileşim açıklanmıştır <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.</span><span class="sxs-lookup"><span data-stu-id="08f06-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="08f06-109">AutoSize ayarı</span><span class="sxs-lookup"><span data-stu-id="08f06-109">AutoSize setting</span></span>|<span data-ttu-id="08f06-110">Stil etkileşimi</span><span class="sxs-lookup"><span data-stu-id="08f06-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="08f06-111"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi soldan sağa devam eder ve sütun veya satır ya da aşağıdaki sırayla alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="08f06-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="08f06-112">1.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.SizeType.Absolute>, tarafından belirtilen piksel sayısı <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> ayrılır.</span><span class="sxs-lookup"><span data-stu-id="08f06-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="08f06-113">2.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği <xref:System.Windows.Forms.SizeType.AutoSize>, alt denetimin tarafından döndürülen piksel sayısı <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi ayrılır.</span><span class="sxs-lookup"><span data-stu-id="08f06-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="08f06-114">3.  Alan sonra <xref:System.Windows.Forms.SizeType.Absolute> ve <xref:System.Windows.Forms.SizeType.AutoSize> satırları veya sütunları ayrılır, herhangi bir sütun veya satır ile <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> kümesine <xref:System.Windows.Forms.SizeType.Percent> orantılı olarak kalan boş alanı ayırmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="08f06-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="08f06-115">Benzer şekilde, önceki etkileşimi, özel durum, <xref:System.Windows.Forms.SizeType.Percent> satırları veya sütunları otomatik boyutlandırma boyut alma.</span><span class="sxs-lookup"><span data-stu-id="08f06-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="08f06-116"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi genişletir yeterli boş alan oluşturmak için satır ve sütun böylece hiçbir sütun veya satır ile <xref:System.Windows.Forms.SizeType.Percent> stil içeriğini kırpar.</span><span class="sxs-lookup"><span data-stu-id="08f06-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="08f06-117"><xref:System.Windows.Forms.TableLayoutPanel> Denetim ayırır yeni alanına orantılı olarak göre <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="08f06-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08f06-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08f06-118">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="08f06-119">TableLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="08f06-119">TableLayoutPanel Control Overview</span></span>](tablelayoutpanel-control-overview.md)
