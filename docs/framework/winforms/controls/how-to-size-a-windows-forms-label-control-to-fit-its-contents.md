---
title: 'Nasıl yapılır: Bir Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 74947e529a472c9e9a681fcb436ce8aff990c0af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640413"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="30a5c-102">Nasıl yapılır: Bir Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="30a5c-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="30a5c-103">Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satır veya çok satırlı olabilir ve boyutunu ya da düzeltilmesi veya otomatik olarak kendini kendi açıklamalı alt yazı uyum sağlayacak şekilde boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30a5c-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="30a5c-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Özellik başlığı çalışma zamanında değişir, özellikle yararlı olan daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="30a5c-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="30a5c-105">Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapma</span><span class="sxs-lookup"><span data-stu-id="30a5c-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="30a5c-106">Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="30a5c-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="30a5c-107">Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükleri <xref:System.Windows.Forms.Label.Text%2A> özelliği, mümkünse sonraki satıra kaydırma, ancak denetim yok büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="30a5c-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a5c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30a5c-108">See also</span></span>
- [<span data-ttu-id="30a5c-109">Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="30a5c-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="30a5c-110">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30a5c-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)
- [<span data-ttu-id="30a5c-111">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="30a5c-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
