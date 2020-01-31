---
title: Etiket denetimini Içeriğini sığacak şekilde boyutlandır
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743778"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="cc2f9-102">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="cc2f9-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="cc2f9-103">Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satırlık veya çok satırlı olabilir ve boyut olarak sabitlenebilir ya da otomatik olarak kendi başlık yazısına sığacak şekilde yeniden boyutlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc2f9-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="cc2f9-104"><xref:System.Windows.Forms.Label.AutoSize%2A> özelliği, daha büyük veya daha küçük açıklamalı alt yazıların sığması için denetimleri boyutlandırmanıza yardımcı olur. Bu, özellikle başlık çalışma zamanında değişliyorsa kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc2f9-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="cc2f9-105">Bir etiket denetimini, içeriğini sığdırmak için dinamik olarak yeniden boyutlandırmak için</span><span class="sxs-lookup"><span data-stu-id="cc2f9-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="cc2f9-106"><xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc2f9-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="cc2f9-107"><xref:System.Windows.Forms.Label.AutoSize%2A> `false`olarak ayarlanırsa, <xref:System.Windows.Forms.Label.Text%2A> özelliğinde belirtilen sözcükler mümkünse sonraki satıra kaydırılır, ancak denetim büyütülecektir.</span><span class="sxs-lookup"><span data-stu-id="cc2f9-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2f9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc2f9-108">See also</span></span>

- [<span data-ttu-id="cc2f9-109">Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc2f9-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="cc2f9-110">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc2f9-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="cc2f9-111">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="cc2f9-111">Label Control</span></span>](label-control-windows-forms.md)
