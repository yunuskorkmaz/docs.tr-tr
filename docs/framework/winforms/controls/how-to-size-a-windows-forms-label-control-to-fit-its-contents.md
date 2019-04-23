---
title: 'Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312195"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="41040-102">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="41040-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="41040-103">Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satır veya çok satırlı olabilir ve boyutunu ya da düzeltilmesi veya otomatik olarak kendini kendi açıklamalı alt yazı uyum sağlayacak şekilde boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41040-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="41040-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Özellik başlığı çalışma zamanında değişir, özellikle yararlı olan daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="41040-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="41040-105">Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapma</span><span class="sxs-lookup"><span data-stu-id="41040-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="41040-106">Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="41040-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="41040-107">Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükleri <xref:System.Windows.Forms.Label.Text%2A> özelliği, mümkünse sonraki satıra kaydırma, ancak denetim yok büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="41040-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41040-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41040-108">See also</span></span>

- [<span data-ttu-id="41040-109">Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="41040-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="41040-110">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41040-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="41040-111">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="41040-111">Label Control</span></span>](label-control-windows-forms.md)
