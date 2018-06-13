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
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533734"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="08e9b-102">Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="08e9b-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="08e9b-103">Windows Forms <xref:System.Windows.Forms.Label> denetim tek satırlı veya çok satırlı olabilir ve ya da boyutu sabit ya da otomatik olarak kendisini yazısına uyum sağlayacak şekilde boyutlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08e9b-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="08e9b-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Özelliği resim yazısını çalışma zamanında değişecekse özellikle yararlı olduğu daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="08e9b-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="08e9b-105">Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapmak için</span><span class="sxs-lookup"><span data-stu-id="08e9b-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="08e9b-106">Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="08e9b-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="08e9b-107">Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükler <xref:System.Windows.Forms.Label.Text%2A> özelliği mümkünse sonraki satıra kaydır, ancak denetim yok büyüyecektir.</span><span class="sxs-lookup"><span data-stu-id="08e9b-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e9b-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08e9b-108">See Also</span></span>  
 [<span data-ttu-id="08e9b-109">Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08e9b-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="08e9b-110">Etiket Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="08e9b-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="08e9b-111">Etiket Denetimi</span><span class="sxs-lookup"><span data-stu-id="08e9b-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
