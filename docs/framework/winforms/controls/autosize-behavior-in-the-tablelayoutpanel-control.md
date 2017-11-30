---
title: "TableLayoutPanel Denetiminde AutoSize Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d4813b7bd37c0c5bd9b04b37cb825067b35ce3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="7fffd-102">TableLayoutPanel Denetiminde AutoSize Davranışı</span><span class="sxs-lookup"><span data-stu-id="7fffd-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="7fffd-103">Ayrı AutoSize davranışı</span><span class="sxs-lookup"><span data-stu-id="7fffd-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="7fffd-104"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi, aşağıdaki yollarla otomatik boyutlandırma davranışını destekler:</span><span class="sxs-lookup"><span data-stu-id="7fffd-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="7fffd-105">Aracılığıyla <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği;</span><span class="sxs-lookup"><span data-stu-id="7fffd-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="7fffd-106">Aracılığıyla <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özellikte <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.</span><span class="sxs-lookup"><span data-stu-id="7fffd-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="7fffd-107">Satır ve sütun stilleri AutoSize özelliği</span><span class="sxs-lookup"><span data-stu-id="7fffd-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="7fffd-108">Aşağıdaki tabloda arasındaki etkileşim açıklanmıştır <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği ve <xref:System.Windows.Forms.TableLayoutPanel> denetimin sütun ve satır stilleri.</span><span class="sxs-lookup"><span data-stu-id="7fffd-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="7fffd-109">AutoSize ayarı</span><span class="sxs-lookup"><span data-stu-id="7fffd-109">AutoSize setting</span></span>|<span data-ttu-id="7fffd-110">Stil etkileşim</span><span class="sxs-lookup"><span data-stu-id="7fffd-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="7fffd-111"><xref:System.Windows.Forms.TableLayoutPanel> Denetimi soldan sağa doğru devam eder ve sütun veya satır için veya aşağıdaki sırayla alan ayırır.</span><span class="sxs-lookup"><span data-stu-id="7fffd-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="7fffd-112">1.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği ayarlanmış <xref:System.Windows.Forms.SizeType.Absolute>, tarafından belirtilen piksel sayısı <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7fffd-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="7fffd-113">2.  Varsa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> özelliği ayarlanmış <xref:System.Windows.Forms.SizeType.AutoSize>, alt denetimin tarafından döndürülen piksel sayısı <xref:System.Windows.Forms.Control.GetPreferredSize%2A> yöntemi ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7fffd-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="7fffd-114">3.  Tüm alanı sonra <xref:System.Windows.Forms.SizeType.Absolute> ve <xref:System.Windows.Forms.SizeType.AutoSize> sütunlara veya satırlara ayrılır, herhangi bir sütun veya satır ile <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> kümesine <xref:System.Windows.Forms.SizeType.Percent> orantılı olarak kalan boş alanı ayırmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="7fffd-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="7fffd-115">Özel önceki etkileşimini benzer, <xref:System.Windows.Forms.SizeType.Percent> sütunlara veya satırlara otomatik boyutlandırma en boy edinin.</span><span class="sxs-lookup"><span data-stu-id="7fffd-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="7fffd-116"><xref:System.Windows.Forms.TableLayoutPanel> Denetimini genişleten sütun veya yeterli boş alan oluşturmak için satır böylece hiçbir sütun veya satır ile <xref:System.Windows.Forms.SizeType.Percent> stil içeriğini kırpar.</span><span class="sxs-lookup"><span data-stu-id="7fffd-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="7fffd-117"><xref:System.Windows.Forms.TableLayoutPanel> Denetim ayırır yeni alana orantılı olarak göre <xref:System.Windows.Forms.ColumnStyle.Width%2A> veya <xref:System.Windows.Forms.RowStyle.Height%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7fffd-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fffd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7fffd-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="7fffd-119">TableLayoutPanel denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7fffd-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
