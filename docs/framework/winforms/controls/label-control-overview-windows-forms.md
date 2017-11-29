---
title: "Etiket Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f55cfb6afa8ad533aac84b391a7cd6fef83d72d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="e8c88-102">Etiket Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e8c88-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="e8c88-103">Windows Forms <xref:System.Windows.Forms.Label> denetimleri, metin veya kullanıcı tarafından düzenlenemez görüntüler görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8c88-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="e8c88-104">Bir form üzerinde nesneleri tanımlamak için kullanılan — hangi belirli bir denetimin açıklamasını yeterlidir tıkladıysanız, örneğin sağlayın ya da bir çalışma zamanı olay veya işlem uygulamanızda yanıt bilgileri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="e8c88-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="e8c88-105">Örneğin, etiketleri metin kutuları, liste kutuları, birleşik giriş kutuları ve benzeri tanımlayıcı resim yazıları eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8c88-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="e8c88-106">Ayrıca olaylarına yanıt olarak bir etiket tarafından çalışma zamanında görüntülenen metni değiştirir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8c88-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="e8c88-107">Örneğin, uygulamanızın bir değişiklik işlemek için birkaç dakika sürer, bir etiket işleme durum iletisi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8c88-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="e8c88-108">Etiket denetimi ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e8c88-108">Working with the Label Control</span></span>  
 <span data-ttu-id="e8c88-109">Çünkü <xref:System.Windows.Forms.Label> denetimi odağı alamıyor, diğer denetimler için erişim anahtarları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8c88-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="e8c88-110">Erişim tuşu kullanıcının erişim anahtarı ile ALT tuşuna basarak diğer denetim seçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8c88-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="e8c88-111">Daha fazla bilgi için bkz: [oluşturma erişim anahtarları için Windows Forms denetimleri](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) ve [nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e8c88-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="e8c88-112">Etiketinde gösterilen resim yazısı yer <xref:System.Windows.Forms.Label.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8c88-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="e8c88-113"><xref:System.Windows.Forms.Label.TextAlign%2A> Özelliği etiketi içinde metin hizalamasını ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8c88-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="e8c88-114">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimi tarafından görüntülenen metni ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="e8c88-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c88-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8c88-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="e8c88-116">Nasıl yapılır: Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="e8c88-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="e8c88-117">Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8c88-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
